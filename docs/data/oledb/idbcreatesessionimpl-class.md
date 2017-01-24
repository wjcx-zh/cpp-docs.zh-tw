---
title: "IDBCreateSessionImpl 類別 | Microsoft Docs"
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
  - "IDBCreateSessionImpl"
  - "ATL.IDBCreateSessionImpl"
  - "ATL::IDBCreateSessionImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBCreateSessionImpl 類別"
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateSessionImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### 參數  
 `T`  
 YOUR CLASS, DERIVED FROM  
  
 `SessionClass`  
 工作階段物件。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[CreateSession](../../data/oledb/idbcreatesessionimpl-createsession.md)|從資料來源物件中建立新工作階段，並傳回這個新建立的工作階段所要求的介面。|  
  
## 備註  
 資料來源物件中需要的介面。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)