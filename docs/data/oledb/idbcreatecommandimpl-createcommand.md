---
title: "IDBCreateCommandImpl::CreateCommand | Microsoft Docs"
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
  - "IDBCreateCommandImpl.CreateCommand"
  - "CreateCommand"
  - "IDBCreateCommandImpl::CreateCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateCommand 方法"
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateCommandImpl::CreateCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立新的命令並傳回要求的介面。  
  
## 語法  
  
```  
  
      STDMETHOD(CreateCommand)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand    
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* [IDBCreateCommand::CreateCommand](https://msdn.microsoft.com/en-us/library/ms709772.aspx) 。  
  
 有些參數對應至 *OLE DB 程式設計人員參考* 參數中的不同名稱，並由 **IDBCreateCommand::CreateCommand** 說明。  
  
|OLE DB 樣版參數|*OLE DB 程式設計人員參考* 參數|  
|-----------------|--------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IDBCreateCommandImpl 類別](../../data/oledb/idbcreatecommandimpl-class.md)