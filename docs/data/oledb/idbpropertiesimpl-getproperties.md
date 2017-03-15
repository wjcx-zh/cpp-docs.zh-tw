---
title: "IDBPropertiesImpl::GetProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBPropertiesImpl::GetProperties"
  - "IDBPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties 方法"
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回資料來源，資料來源資訊及在目前設定於列舉值的資料來源物件或在初始化屬性群組中的屬性的值設定的目前資料來源、資訊初始化和屬性群組中的屬性值。  
  
## 語法  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties    
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) 。  
  
 有些參數對應至在 **IDBProperties::GetProperties**中說明的不同名稱的 *OLE DB* 參數:  
  
|OLE DB 樣版參數|*OLE DB 程式設計人員參考* 參數|  
|-----------------|--------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## 備註  
 如果提供者已初始化，這個方法會傳回目前在資料來源物件設定的 **DBPROPSET\_DATASOURCE**，**DBPROPSET\_DATASOURCEINFO**，**DBPROPSET\_DBINIT** 屬性群組的屬性值。  如果提估者未初始化，則只會傳回 **DBPROPSET\_DBINIT** 群組屬性。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IDBPropertiesImpl 類別](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)