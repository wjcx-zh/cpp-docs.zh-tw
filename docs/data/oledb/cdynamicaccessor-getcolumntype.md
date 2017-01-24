---
title: "CDynamicAccessor::GetColumnType | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.GetColumnType"
  - "CDynamicAccessor::GetColumnType"
  - "GetColumnType"
  - "CDynamicAccessor.GetColumnType"
  - "ATL::CDynamicAccessor::GetColumnType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnType 方法"
ms.assetid: ac96a2e9-6049-4eb5-9718-9f5f5446b74e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetColumnType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要取得特定資料行的資料型別  
  
## 語法  
  
```  
  
      bool GetColumnType(   
   DBORDINAL nColumn,   
   DBTYPE* pType    
) const throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\] 資料行編號。  資料行編號從 1 開始。  值為 0 表示書籤資料行，如果有的話。  
  
 `pType`  
 \[out\] 特定資料欄中型別的指標。  
  
## 傳回值  
 如果成功則傳回 **true**，失敗則傳回 **false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)