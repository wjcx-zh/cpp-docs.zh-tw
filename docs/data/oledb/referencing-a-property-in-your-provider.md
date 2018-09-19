---
title: 您的提供者內參考屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6730746cbb3da08e52b5a4d9936aa48a8484886
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052554"
---
# <a name="referencing-a-property-in-your-provider"></a>在提供者內參考屬性

尋找您想要的屬性的屬性群組和屬性識別碼。 如需詳細資訊，請參閱 < [OLE DB 屬性](/previous-versions/windows/desktop/ms722734\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
下列範例假設您嘗試從資料列集取得的屬性。 使用工作階段或命令的程式碼很類似，但使用不同的介面。  
  
建立[CDBPropSet](../../data/oledb/cdbpropset-class.md)物件做為建構函式的參數使用的屬性群組。 例如:   
  
```cpp  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
呼叫[AddProperty](../../data/oledb/cdbpropset-addproperty.md)，將它傳遞的屬性識別碼和要指派給屬性的值。 值的類型取決於您使用的屬性。  
  
```cpp  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
使用`IRowset`介面呼叫`GetProperties`。 傳遞做為參數設定的屬性。 以下是最後的程式碼：  
  
```cpp  
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
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