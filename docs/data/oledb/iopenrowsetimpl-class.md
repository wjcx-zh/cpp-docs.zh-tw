---
title: "IOpenRowsetImpl 類別 | Microsoft Docs"
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
  - "IOpenRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOpenRowsetImpl 類別"
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOpenRowsetImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IOpenRowset` 介面的實作。  
  
## 語法  
  
```  
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### 參數  
 `SessionClass`  
 您的類別，衍生自 `IOpenRowsetImpl`。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|建立資料列集物件。  不會直接呼叫由使用者。|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|開啟並傳回含有來自單一基底資料表或索引的所有資料行的資料列集。\(不在 ATLDB.H\)|  
  
## 備註  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) 介面對工作階段物件是必要的。  開啟並傳回含有來自單一基底資料表或索引的所有資料行的資料列集。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)