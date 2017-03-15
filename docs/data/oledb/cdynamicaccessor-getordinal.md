---
title: "CDynamicAccessor::GetOrdinal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor.GetOrdinal"
  - "ATL::CDynamicAccessor::GetOrdinal"
  - "CDynamicAccessor::GetOrdinal"
  - "ATL.CDynamicAccessor.GetOrdinal"
  - "GetOrdinal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOrdinal 方法"
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetOrdinal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定資料行名稱的資料行數目。  
  
## 語法  
  
```  
  
      bool GetOrdinal(  
   const CHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
bool GetOrdinal(  
   const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
```  
  
#### 參數  
 `pColumnName`  
 \[in\] 指向包含資料行名稱的字串之指標。  
  
 *pOrdinal*  
 \[out\] 指向資料列數目的指標。  
  
## 傳回值  
 如果找到具有指定名稱的資料行的話，傳回 **true** 。  否則，函式會傳回**false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)