---
title: "CDynamicAccessor::GetValue | Microsoft Docs"
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
  - "GetValue"
  - "CDynamicAccessor::GetValue<ctype>"
  - "ATL.CDynamicAccessor.GetValue<ctype>"
  - "CDynamicAccessor.GetValue"
  - "CDynamicAccessor::GetValue"
  - "ATL.CDynamicAccessor.GetValue"
  - "ATL::CDynamicAccessor::GetValue"
  - "ATL::CDynamicAccessor::GetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetValue 方法"
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取資料為指定的資料行。  
  
## 語法  
  
```  
  
      void* GetValue(   
   DBORDINAL nColumn    
) const throw( );  
void* GetValue(  
   const CHAR* pColumnName   
) const throw( );  
void* GetValue(  
   const WCHAR* pColumnName   
) const throw( );  
template < class ctype >  
bool GetValue(  
   DBORDINAL nColumn,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const CHAR* pColumnName,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const WCHAR* pColumnName,  
   ctype* pData   
) const throw( );  
```  
  
#### 參數  
 `ctype`  
 \[A 樣板化處理不同資料型別的參數 \(**CHAR\***， **WCHAR\***\) 的任何資料型別，則需要特殊處理。  `GetValue` 使用根據適當的資料型別您在這裡指定。  
  
 `nColumn`  
 \[in\]資料行編號。  資料行編號從 1 開始。  一個為 0 的值表示書籤資料行 \(如果有的話\)。  
  
 `pColumnName`  
 \[in\] 資料行名稱。  
  
 `pData`  
 \[至指定的資料列內容的指標。  
  
## 傳回值  
 如果您要將字串資料，請使用 `GetValue`nontemplated 版本。  這個方法 nontemplated 版本傳回 **void\***，指向緩衝區中包含指定之資料行的資料。  如果找不到欄，則會傳回 **NULL**。  
  
 對其他資料型別，是較簡單的使用 `GetValue`樣板化版本。  對於包含版本，成功時傳回 **true** ，失敗時則傳回 **false** 。  
  
## 備註  
 使用 nontemplated 版本傳回包含字串和樣板化的控制項中其他資料型別的資料行。  
  
 在偵錯模式中，您會取得判斷提示 `pData` 的大小是否不等於它所指向的資料行的大小。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)