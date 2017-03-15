---
title: "ICommandPropertiesImpl::SetProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandPropertiesImpl.SetProperties"
  - "ICommandPropertiesImpl::SetProperties"
  - "SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties 方法"
ms.assetid: c42132bb-16a9-4e00-aba6-dee785a98488
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ICommandPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定命令物件的屬性。  
  
## 語法  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[ICommandProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms711497.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [ICommandPropertiesImpl 類別](../../data/oledb/icommandpropertiesimpl-class.md)   
 [ICommandPropertiesImpl::GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)