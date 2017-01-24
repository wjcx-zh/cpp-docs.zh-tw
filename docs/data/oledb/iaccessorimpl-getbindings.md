---
title: "IAccessorImpl::GetBindings | Microsoft Docs"
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
  - "IAccessorImpl.GetBindings"
  - "ATL::IAccessorImpl::GetBindings"
  - "IAccessorImpl::GetBindings"
  - "GetBindings"
  - "ATL.IAccessorImpl.GetBindings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBindings 方法"
ms.assetid: eb550077-77ef-450b-89f1-a2930cee6ab8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl::GetBindings
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回從消費者的基本資料行繫結的存取子。  
  
## 語法  
  
```  
  
      STDMETHOD(GetBindings)(  
   HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IAccessor::GetBindings](https://msdn.microsoft.com/en-us/library/ms721253.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IAccessorImpl 類別](../../data/oledb/iaccessorimpl-class.md)