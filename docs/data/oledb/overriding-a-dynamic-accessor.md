---
title: "覆寫動態存取子 | Microsoft Docs"
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
  - "存取子 [C++], 動態"
  - "動態存取子"
  - "覆寫, 動態存取子"
ms.assetid: cbefd156-6da5-490d-b795-c2d7d874f7ce
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 覆寫動態存取子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您使用 `CDynamicAccessor` 這類的動態存取子時，**Open** 命令的方法會自動地為您根據已開啟資料列集的資料行資訊，建立一個存取子。  您可以覆寫動態存取子以便確實地控制資料行的繫結方式。  
  
 若要覆寫這個動態存取子，請將 **false** 當成最後一個參數傳遞給 `CCommand::Open` 方法。  這樣便可以避免 **Open** 自動建立存取子。  然後您可以為每個要繫結的資料行呼叫 `GetColumnInfo` 和呼叫 `AddBindEntry`。  請參見下列範例程式碼：  
  
```  
USES_CONVERSION;  
double   dblProductID;  
  
CCommand<CDynamicAccessor> product;  
// Open the table, passing false to prevent automatic binding   
product.Open(session, _T("Select * FROM Products"), NULL, NULL, DBGUID_DEFAULT, false);  
  
ULONG         nColumns;  
DBCOLUMNINFO*   pColumnInfo;  
// Get the column information from the opened rowset.  
product.GetColumnInfo(&nColumns, &pColumnInfo);  
  
// Bind the product ID as a double.  
pColumnInfo[0].wType          = DBTYPE_R8;  
pColumnInfo[0].ulColumnSize = 8;  
product.AddBindEntry(pColumnInfo[0]);  
  
// Bind the product name as it is.  
product.AddBindEntry(pColumnInfo[1]);  
  
// Bind the reorder level as a string.  
pColumnInfo[8].wType          = DBTYPE_STR;  
pColumnInfo[8].ulColumnSize = 10;  
product.AddBindEntry(pColumnInfo[8]);  
  
// You have finished specifying the bindings. Go ahead and bind.  
product.Bind();  
// Free the memory for the column information that was retrieved in   
// previous call to GetColumnInfo.  
CoTaskMemFree(pColumnInfo);  
  
char*   pszProductName;  
char*   pszReorderLevel;  
bool   bRC;  
  
// Loop through the records tracing out the information.  
while (product.MoveNext() == S_OK)  
{  
   bRC = product.GetValue(1, &dblProductID);  
   pszProductName   = (char*)product.GetValue(2);  
   pszReorderLevel  = (char*)product.GetValue(9);  
  
   ATLTRACE(_T("Override = %lf \"%s\" \"%s\"\n"), dblProductID,  
      A2T(pszProductName), A2T(pszReorderLevel));  
}  
```  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)