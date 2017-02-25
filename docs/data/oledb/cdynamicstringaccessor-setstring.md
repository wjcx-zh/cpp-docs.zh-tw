---
title: "CDynamicStringAccessor::SetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor::SetString"
  - "CDynamicStringAccessor.SetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetString 方法"
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDynamicStringAccessor::SetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定指定資料行的資料做為字串。  
  
## 語法  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\]資料行編號。  資料行編號從 1 開始。  特殊值 0 代表書籤資料行，，如果有的話。  
  
 `pColumnName`  
 \[in\] 包含資料行名稱的字串的指標。  
  
 `data`  
 \[in\]寫入指定的資料行要寫入的字串資料之的指標。  
  
## 傳回值  
 設定指定之資料行的字串值的指標。  值屬於型別 `BaseType`，則會是 `CHAR` 或 `WCHAR` 是 `_UNICODE` 中定義。  
  
## 備註  
 當做 ANSI 字串和第三個覆寫表單接受資料行名稱指定為 Unicode 字串，第二個覆寫表單接受資料行名稱。  
  
 如果 `_SECURE_ATL` 定義為具有非零的值，執行階段判斷提示失敗時產生，如果輸入字串的 `data` 參考的資料行可允許的最大長度。  否則，如果它超過允許的最大長度，其輸入字串將被截斷。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)