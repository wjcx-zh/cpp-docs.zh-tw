---
title: 修改的 RCustomRowset |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a6f4827ecf0571878bc0eeaef5dce74326488c61
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990279"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>修改的 RCustomRowset

若要新增`IRowsetLocate`介面的簡單唯讀提供者範例，請修改繼承的`RCustomRowset`。 一開始，`RCustomRowset`繼承自`CRowsetImpl`。 您需要修改它繼承自`CRowsetBaseImpl`。  
  
若要這樣做，請建立新的類別， `CMyRowsetImpl`，請在*自訂*RS.h:  
  
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
  
這會建立 COM 介面對應，告訴`CMyRowsetImpl`來呼叫`QueryInterface`同時`IRowset`和`IRowsetLocate`介面。 若要取得所有其他的資料列集的實作類別，對應連結`CMyRowsetImpl`類別將會回到`CRowsetBaseImpl`OLE DB 範本所定義的類別，地圖會使用 COM_INTERFACE_ENTRY_CHAIN 巨集，它會告訴掃描中的 COM 對應的 OLE DB 樣板`CRowsetBaseImpl`回應`QueryInterface`呼叫。  
  
最後，連結`RAgentRowset`要`CMyRowsetBaseImpl`藉由修改`RAgentRowset`繼承自`CMyRowsetImpl`、，如下所示：  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>  
```  
  
`RAgentRowset` 現在可以使用`IRowsetLocate`同時利用其餘的資料列集類別的實作的介面。  
  
當這麼做時，您可以[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>另請參閱  

[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)