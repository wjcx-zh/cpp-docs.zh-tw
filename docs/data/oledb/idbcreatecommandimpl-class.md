---
title: "IDBCreateCommandImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBCreateCommandImpl"
  - "IDBCreateCommandImpl"
  - "ATL.IDBCreateCommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBCreateCommandImpl 類別"
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBCreateCommandImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
#### 參數  
 `T`  
 從 `IDBCreateCommandImpl`取得的工作階段物件。  
  
 `CommandClass`  
 您的命令類別。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[CreateCommand](../../data/oledb/idbcreatecommandimpl-createcommand.md)|建立新命令。|  
  
## 備註  
 在取得新命令的工作階段物件的選擇性介面。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)