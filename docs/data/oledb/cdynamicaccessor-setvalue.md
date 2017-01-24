---
title: "CDynamicAccessor::SetValue | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.SetValue"
  - "ATL::CDynamicAccessor::SetValue"
  - "ATL::CDynamicAccessor::SetValue<ctype>"
  - "CDynamicAccessor.SetValue"
  - "ATL.CDynamicAccessor.SetValue<ctype>"
  - "CDynamicAccessor::SetValue"
  - "CDynamicAccessor::SetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetValue 方法"
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將資料儲存至指定的資料行。  
  
## 語法  
  
```  
  
      template < class ctype >    
bool SetValue(   
   DBORDINAL nColumn,   
   const ctype& data    
) throw( );  
template < class ctype >    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data    
) throw( );  
template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data   
) throw( );  
```  
  
#### 參數  
 `ctype`  
 \[A 樣板化處理不同資料型別的參數 \(**CHAR\***， **WCHAR\***\) 的任何資料型別，則需要特殊處理。  `GetValue` 使用根據適當的資料型別您在這裡指定。  
  
 `pColumnName`  
 \[out 包含資料行名稱的字串的指標。  
  
 `data`  
 \[out 包含資料的記憶體指標。  
  
 `nColumn`  
 \[的資料列數目。  資料行的以 1。  值為 0 表示書籤資料行，，如果有的話。  
  
## 傳回值  
 如果您要將字串資料，請使用 `GetValue`nontemplated 版本。  這個方法 nontemplated 版本傳回 **void\***，指向緩衝區中包含指定之資料行的資料。  如果找不到，則會傳回 **NULL** 。  
  
 對其他資料型別，是較簡單的使用 `GetValue`樣板化版本。  樣板化版本會在成功的在失敗的 **true** 或 **false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)