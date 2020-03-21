---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 8e90db287bc7ac8994914766045eb210446dfd48
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079785"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Wizard 會產生資料列集物件的專案。 在此情況下，它會被稱為 `CCustomRowset`。 `CCustomRowset` 類別繼承自稱為 `CRowsetImpl`的 OLE DB 提供者類別，它會針對資料列集物件執行所有必要的介面。 下列程式碼顯示 `CRowsetImpl`的繼承鏈：

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` 也會使用 `IAccessor` 和 `IColumnsInfo` 介面。 它會針對資料表中的輸出欄位使用這些介面。 類別也會提供 `IRowsetIdentity`的執行，讓取用者能夠判斷兩個數據列是否相同。 `IRowsetInfo` 介面會實作為資料列集物件的屬性。 `IConvertType` 介面可以讓提供者解決取用者要求的資料類型與提供者所使用的不同之間的差異。

`IRowset` 介面會實際處理資料的抓取。 取用者會先呼叫名為 `GetNextRows` 的方法，以傳回資料列的控制碼，稱為 `HROW`。 然後，取用者會使用該 `HROW` 來呼叫 `IRowset::GetData`，以取得要求的資料。

`CRowsetImpl` 也會採用數個範本參數。 這些參數可讓您判斷 `CRowsetImpl` 類別處理資料的方式。 `ArrayType` 引數可讓您決定用來儲存資料列資料的儲存機制。 *RowClass*參數會指定哪個類別包含 `HROW`。

*RowsetInterface*參數可讓您同時使用 `IRowsetLocate` 或 `IRowsetScroll` 介面。 `IRowsetLocate` 和 `IRowsetScroll` 介面都繼承自 `IRowset`。 因此，OLE DB 提供者範本必須提供這些介面的特殊處理。 如果您想要使用其中一個介面，則需要使用此參數。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>
