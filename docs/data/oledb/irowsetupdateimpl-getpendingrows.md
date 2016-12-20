---
title: "IRowsetUpdateImpl::GetPendingRows | Microsoft Docs"
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
  - "IRowsetUpdateImpl::GetPendingRows"
  - "GetPendingRows"
  - "IRowsetUpdateImpl.GetPendingRows"
  - "ATL::IRowsetUpdateImpl::GetPendingRows"
  - "ATL.IRowsetUpdateImpl.GetPendingRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPendingRows 方法"
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::GetPendingRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回具有暫止變更的資料行清單。  
  
## 語法  
  
```  
  
      STDMETHOD ( GetPendingRows )(  
   HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus   
);  
```  
  
#### 參數  
 `hReserved`  
 \[in\] 對應至 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)的 `hChapter` 參數。  
  
 如需其他參數，請參閱 *OLE DB 程式設計人員參考*的 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) 。  
  
## 備註  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) 。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)