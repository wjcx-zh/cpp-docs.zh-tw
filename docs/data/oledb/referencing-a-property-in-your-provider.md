---
title: 在提供者內參考屬性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: d70a1901c457d9fbdbe8712d84999e256a54d0c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209758"
---
# <a name="referencing-a-property-in-your-provider"></a>在提供者內參考屬性

尋找您想要之屬性的屬性群組和屬性 ID。 如需詳細資訊，請參閱 OLE DB 程式設計**人員參考**中的[OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))。

下列範例假設您正嘗試從資料列集取得屬性。 使用會話或命令的程式碼很類似，但使用不同的介面。

使用屬性群組做為函式的參數，以建立[CDBPropSet](../../data/oledb/cdbpropset-class.md)物件。 例如：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

呼叫[AddProperty](../../data/oledb/cdbpropset-addproperty.md)，將屬性識別碼和要指派給屬性的值傳遞給它。 值的類型取決於您所使用的屬性。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

使用 `IRowset` 介面來呼叫 `GetProperties`。 傳遞屬性集做為參數。 以下是最後的程式碼：

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
