---
title: 修改的 RCustomRowset
ms.date: 10/26/2018
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
ms.openlocfilehash: d22c6902667ec84abe7bd85ffbffd1f5c5c57f2a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024864"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>修改的 RCustomRowset

若要新增`IRowsetLocate`介面的簡單唯讀提供者範例，請修改繼承的`CCustomRowset`。 一開始，`CCustomRowset`繼承自`CRowsetImpl`。 您需要修改它繼承自`CRowsetBaseImpl`。

若要這樣做，請建立新的類別， `CCustomRowsetImpl`，請在*自訂*RS.h:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

現在，編輯中的 COM 介面對應*自訂*RS.h 要如下所示：

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

此程式碼建立 COM 介面對應，告訴`CMyRowsetImpl`來呼叫`QueryInterface`同時`IRowset`和`IRowsetLocate`介面。 若要取得所有其他的資料列集的實作類別，對應連結`CMyRowsetImpl`類別將會回到`CRowsetBaseImpl`OLE DB 範本所定義的類別，地圖會使用 COM_INTERFACE_ENTRY_CHAIN 巨集，它會告訴掃描中的 COM 對應的 OLE DB 樣板`CRowsetBaseImpl`回應`QueryInterface`呼叫。

最後，連結`CCustomRowset`要`CMyRowsetBaseImpl`藉由修改`CCustomRowset`繼承自`CMyRowsetImpl`、，如下所示：

```cpp
class CCustomRowset : public CMyRowsetImpl<CCustomRowset, CCustomWindowsFile, CCustomCommand>
```

`CCustomRowset` 現在可以使用`IRowsetLocate`同時利用其餘的資料列集類別的實作的介面。

當這麼做時，您可以[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>另請參閱

[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
