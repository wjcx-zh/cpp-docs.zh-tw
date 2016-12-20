---
title: "IDBPropertiesImpl::SetProperties | Microsoft Docs"
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
  - "IDBPropertiesImpl.SetProperties"
  - "SetProperties"
  - "IDBPropertiesImpl::SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties 方法"
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為了資料來源物件在資料來源和初始化屬性群組中設定屬性，或是為了列舉程式初始化屬性群組。  
  
## 語法  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx) 。  
  
## 備註  
 如果提供者已初始化，這個方法會設定目前在資料來源物件的 **DBPROPSET\_DATASOURCE**，**DBPROPSET\_DATASOURCEINFO**，**DBPROPSET\_DBINIT** 屬性群組的屬性值。  如果提估者未初始化，則只會設定 **DBPROPSET\_DBINIT** 群組屬性。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IDBPropertiesImpl 類別](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)