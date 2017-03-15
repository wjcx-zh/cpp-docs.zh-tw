---
title: "CDynamicAccessor::GetLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor.GetLength"
  - "ATL.CDynamicAccessor.GetLength"
  - "CDynamicAccessor::GetLength"
  - "ATL::CDynamicAccessor::GetLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetLength 方法"
ms.assetid: 3ae8983b-b267-4cf9-bfc0-3e191f79e646
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定資料行的長度。  
  
## 語法  
  
```  
  
      bool GetLength(   
   DBORDINAL nColumn,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const CHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\] 資料行編號。  資料行編號從 1 開始。  一個為 0 的值表示書籤資料行 \(如果有的話\)。  
  
 `pColumnName`  
 \[in\] 指向包含資料行名稱的字串之指標。  
  
 `pLength`  
 \[out\] 指向包含資料行長度 \(以位元組為單位\) 的整數之指標。  
  
## 傳回值  
 如果找到指定的資料行的話，傳回 **true**。  否則，函式會傳回**false**。  
  
## 備註  
 第一個覆寫採用資料行數，而第二和第三個覆寫分別採用 ANSI 或 Unicode 格式的資料行名稱。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetLength](../../data/oledb/cdynamicaccessor-setlength.md)