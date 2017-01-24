---
title: "ISessionPropertiesImpl::GetProperties | Microsoft Docs"
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
  - "ISessionPropertiesImpl::GetProperties"
  - "ISessionPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties 方法"
ms.assetid: 48726c2a-9599-4fc5-9940-a932faef91ab
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISessionPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在屬性 **DBPROPSET\_SESSION** 群組中傳回這個工作階段目前設定的屬性清單。  
  
## 語法  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets    
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱*OLE DB 程式設計人員參考* 中的 [ISessionProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms723643.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ISessionPropertiesImpl 類別](../../data/oledb/isessionpropertiesimpl-class.md)   
 [ISessionPropertiesImpl::SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)