---
title: "IDBInitializeImpl 類別 | Microsoft Docs"
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
  - "ATL.IDBInitializeImpl<T>"
  - "ATL::IDBInitializeImpl<T>"
  - "IDBInitializeImpl"
  - "ATL::IDBInitializeImpl"
  - "ATL.IDBInitializeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBInitializeImpl 類別"
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBInitializeImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IDBInitializeImpl`。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|建構函式。|  
  
### 介面方法  
  
|||  
|-|-|  
|[初始化](../../data/oledb/idbinitializeimpl-initialize.md)|啟動提供者。|  
|[Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)|停止提供者。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|資料來源旗標。|  
|[m\_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|對 DB 屬性資訊的實作之指標。|  
  
## 備註  
 資料來源物件中的強制介面並列舉值的選擇性介面。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)