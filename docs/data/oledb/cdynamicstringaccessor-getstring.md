---
title: "CDynamicStringAccessor::GetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor.GetString"
  - "CDynamicStringAccessor::GetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetString 方法"
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDynamicStringAccessor::GetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定資料行的資料做為字串。  
  
## 語法  
  
```  
  
      BaseType* GetString(  
   DBORDINAL nColumn  
) const throw( );  
BaseType* GetString(  
   const CHAR* pColumnName  
) const throw( );  
BaseType* GetString(  
   const WCHAR* pColumnName  
) const throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\] 資料行編號。  資料行編號從 1 開始。  值為 0 表示書籤資料行，如果有的話。  
  
 `pColumnName`  
 \[in\] 包含資料行名稱的字串的指標。  
  
## 傳回值  
 要從指定的資料列擷取的字串值的指標。  值屬於型別，將 ***BaseType***是 **CHAR** 或 \_UNICODE **WCHAR** 是否已定義。  如果指定的資料行找不到，則會傳回 null。  
  
## 備註  
 第二個覆寫表單接受資料行名稱為 ANSI 字串。  第三個覆寫表單接受資料行名稱指定為 Unicode 字串。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)