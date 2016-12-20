---
title: "IDBPropertiesImpl 類別 | Microsoft Docs"
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
  - "IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBPropertiesImpl 類別"
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IDBProperties` 介面的實作。  
  
## 語法  
  
```  
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IDBPropertiesImpl` 。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|傳回資料來源，資料來源資訊及在目前設定於列舉值的資料來源物件或在初始化屬性群組中的屬性的值設定的目前資料來源、資訊初始化和屬性群組中的屬性值。|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|傳回有關提供者支援之所有屬性的資訊。|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|為了資料來源物件在資料來源和初始化屬性群組中設定屬性，或是為了列舉程式初始化屬性群組。|  
  
## 備註  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) 是資料來源物件中需要的介面和列舉值的選擇性介面。  不過，如果列舉值公開 [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx)，它必須公開 `IDBProperties`。  使用 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)定義的靜態函式的`IDBPropertiesImpl` 實作 `IDBProperties` 。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)