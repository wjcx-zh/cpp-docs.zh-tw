---
title: "ICommandPropertiesImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandPropertiesImpl"
  - "ATL.ICommandPropertiesImpl"
  - "ATL::ICommandPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandPropertiesImpl 類別"
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandPropertiesImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### 參數  
 `T`  
 您的類別，其衍生自  
  
 `PropClass`  
 您的屬性類別。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|在資料列集屬性群組中傳回目前要求資料列集屬性的清單。|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|在資料列集屬性群組中設定屬性。|  
  
## 備註  
 這是必須在命令。  [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) 巨集定義的靜態函式的實作。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)