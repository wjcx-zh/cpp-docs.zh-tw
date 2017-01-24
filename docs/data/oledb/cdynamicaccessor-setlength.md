---
title: "CDynamicAccessor::SetLength | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicAccessor::SetLength"
  - "CDynamicAccessor.SetLength"
  - "CDynamicAccessor::SetLength"
  - "ATL.CDynamicAccessor.SetLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetLength 方法"
ms.assetid: 8109ae73-04ec-4a47-be97-ba1e60080384
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將指定資料行的長度。  
  
## 語法  
  
```  
  
      bool SetLength(   
   DBORDINAL nColumn,   
   DBLENGTH nLength    
) throw( );  
bool SetLength(   
   const CHAR* pColumnName,   
   DBLENGTH nLength    
) throw( );  
bool SetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH nLength    
) throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\] 資料行編號。  資料行編號從 1 開始。  值為 0 表示書籤資料行，如果有的話。  
  
 `nLength`  
 \[in\] 資料行的長度，以位元組為單位。  
  
 `pColumnName`  
 \[in\] 包含資料行名稱的字串的指標。  
  
## 傳回值  
 如果指定的資料行長度成功，將傳回 **true** 。  否則，函式會傳回**false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetLength](../../data/oledb/cdynamicaccessor-getlength.md)