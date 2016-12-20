---
title: "IAccessorImpl::CreateAccessor | Microsoft Docs"
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
  - "IAccessorImpl::CreateAccessor"
  - "CreateAccessor"
  - "ATL::IAccessorImpl::CreateAccessor"
  - "IAccessorImpl.CreateAccessor"
  - "ATL.IAccessorImpl.CreateAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateAccessor 方法"
ms.assetid: f6b92075-c0b8-46ca-8361-026d562d24f5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl::CreateAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

透過一組繫結建立存取子。  
  
## 語法  
  
```  
  
      STDMETHOD(CreateAccessor)(  
   DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IAccessor::CreateAccessor](https://msdn.microsoft.com/en-us/library/ms720969.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IAccessorImpl 類別](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)