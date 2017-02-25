---
title: "在提供者內參考屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 屬性"
  - "參考, 至提供者中的屬性"
  - "參考提供者中的屬性"
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在提供者內參考屬性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為您要的屬性尋找屬性群組和屬性 ID。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》中的 [OLE DB 屬性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)。  
  
 以下範例假設您想要從資料列集取得屬性。  使用工作階段或命令的程式碼很類似，不同的是它們使用不同的介面。  
  
 將屬性群組以建構函式 \(Constructor\) 參數方式使用，來建立 [CDBPropSet](../../data/oledb/cdbpropset-class.md) 物件。  例如：  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 呼叫 [AddProperty](../../data/oledb/cdbpropset-addproperty.md)，將屬性 ID 和要指定給屬性的數值傳遞給它。  實值型別將視您所使用的屬性而定。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IRowsetChange, true);  
propset.AddProperty(DBPROP_UPDATABILITY,  
DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 使用 `IRowset` 介面來呼叫 **GetProperties**。  將屬性集 \(Property Set\) 以參數方式傳遞。  最後的程式碼如下所列：  
  
```  
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
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)