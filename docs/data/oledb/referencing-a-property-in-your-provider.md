---
title: 在提供者內參考屬性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: ecb11c54d4c5926fbead0196c441ec23e8b0891f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509516"
---
# <a name="referencing-a-property-in-your-provider"></a>在提供者內參考屬性

尋找您想要的屬性的屬性群組和屬性識別碼。 如需詳細資訊，請參閱 OLE DB 程式設計**人員參考**中的[OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))。

下列範例假設您正在嘗試從資料列集取得屬性。 使用會話或命令的程式碼很類似，但使用不同的介面。

使用屬性群組作為函式的參數來建立 [CDBPropSet](../../data/oledb/cdbpropset-class.md) 物件。 例如：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

呼叫 [AddProperty](./cdbpropset-class.md#addproperty)，將屬性識別碼和要指派給屬性的值傳遞給它。 值的類型取決於您所使用的屬性。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

使用 `IRowset` 要呼叫的介面 `GetProperties` 。 將屬性集傳遞為參數。 以下是最後的程式碼：

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
