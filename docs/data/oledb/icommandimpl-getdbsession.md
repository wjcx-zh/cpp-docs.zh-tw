---
title: "ICommandImpl::GetDBSession | Microsoft Docs"
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
  - "ICommandImpl::GetDBSession"
  - "GetDBSession"
  - "ICommandImpl.GetDBSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDBSession 方法"
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::GetDBSession
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回介面指標建立命令的工作階段。  
  
## 語法  
  
```  
  
      STDMETHOD (GetDBSession) (  
   REFIID riid,  
   IUnknown** ppSession   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx) 。  
  
## 備註  
 對於擷取屬性從工作階段。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)