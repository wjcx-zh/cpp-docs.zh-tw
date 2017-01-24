---
title: "IRowsetLocateImpl::Hash | Microsoft Docs"
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
  - "IRowsetLocateImpl::Hash"
  - "IRowsetLocateImpl.Hash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Hash 方法"
ms.assetid: 7df4386d-80fb-4332-a85f-baae98cdc6e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl::Hash
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回指定的書籤有關聯的雜湊值。  
  
## 語法  
  
```  
  
      STDMETHOD ( Hash )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmarks,  
   const DBBKMARK* rgcbBookmarks[],  
   const BYTE* rgpBookmarks[],  
   DBHASHVALUE rgHashValues[],  
   DBROWSTATUS rgBookmarkStatus[]   
);  
```  
  
#### 參數  
 `hReserved`  
 \[對應於 `hChapter` 參數中 [IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx)。  
  
 如需其他參數，請參閱《 *OLE DB 程式設計人員參考*》的[IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)