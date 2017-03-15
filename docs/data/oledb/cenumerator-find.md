---
title: "CEnumerator::Find | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CEnumerator::Find"
  - "ATL::CEnumerator::Find"
  - "ATL.CEnumerator.Find"
  - "CEnumerator.Find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Find 方法"
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::Find
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在可用提供者中尋找指定名稱。  
  
## 語法  
  
```  
  
      bool Find(   
   TCHAR* szSearchName    
) throw( );  
```  
  
#### 參數  
 *szSearchName*  
 \[in\] 要搜尋的名稱。  
  
## 傳回值  
 如果找到相符的名稱，則為 **true**。  否則為 **false**。  
  
## 備註  
 這個名稱對應至 **SOURCES\_NAME** [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) 介面的成員。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CEnumerator 類別](../../data/oledb/cenumerator-class.md)