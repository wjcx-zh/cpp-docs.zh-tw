---
title: "IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs"
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
  - "IRowsetUpdateImpl.m_mapCachedData"
  - "IRowsetUpdateImpl::m_mapCachedData"
  - "m_mapCachedData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_mapCachedData"
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::m_mapCachedData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含延後作業的對應原始資料。  
  
## 語法  
  
```  
  
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### 參數  
 `hRow`  
 為資料處理的資料列。  
  
 `pData`  
 將快取的資料指標。  資料型別為 *儲存體* \(使用者資料錄類別\)。  請參閱在 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)的*Storage*樣板引數。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)