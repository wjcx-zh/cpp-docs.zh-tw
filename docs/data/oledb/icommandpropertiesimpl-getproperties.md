---
title: "ICommandPropertiesImpl::GetProperties | Microsoft Docs"
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
  - "ICommandPropertiesImpl::GetProperties"
  - "ICommandPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties 方法"
ms.assetid: 1bee5f1b-bd08-435a-956a-e4cebcdf5d5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用命令的屬性對應，傳回所有要求的屬性集合。  
  
## 語法  
  
```  
  
      STDMETHOD(GetProperties)(   
   const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets    
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的 [ICommandProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms723119.aspx)。  
  
## 備註  
 請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ICommandPropertiesImpl 類別](../../data/oledb/icommandpropertiesimpl-class.md)   
 [ICommandPropertiesImpl::SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)