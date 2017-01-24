---
title: "ISessionPropertiesImpl 類別 | Microsoft Docs"
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
  - "ISessionPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISessionPropertiesImpl 類別"
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISessionPropertiesImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `ISessionPropertiesImpl`。  
  
 `PropClass`  
 該使用者可定義的屬性類別會預設值為 `T`。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|在工作階段屬性群組中傳回這個工作階段目前設定的屬性清單。|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|在工作階段屬性群組中設定屬性。|  
  
## 備註  
 在工作階段中需要的介面。  這個類別會藉由呼叫靜態函式實作工作階段屬性所定義的 [屬性集對應](../../data/oledb/begin-propset-map.md)。  在您的工作階段類別應該指定屬性集對應。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)