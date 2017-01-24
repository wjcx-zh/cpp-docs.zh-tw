---
title: "IDBCreateSessionImpl::CreateSession | Microsoft Docs"
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
  - "IDBCreateSessionImpl::CreateSession"
  - "IDBCreateSessionImpl.CreateSession"
  - "CreateSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateSession 方法"
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateSessionImpl::CreateSession
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料來源物件中建立新工作階段，並傳回這個新建立的工作階段所要求的介面。  
  
## 語法  
  
```  
  
      STDMETHOD(CreateSession)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession    
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IDBCreateSessionImpl 類別](../../data/oledb/idbcreatesessionimpl-class.md)