---
title: "CSimpleRow 類別 | Microsoft Docs"
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
  - "CSimpleRow"
  - "ATL::CSimpleRow"
  - "ATL.CSimpleRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleRow 類別"
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

資料列控制代碼提供的預設實作中，使用 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) 類別。  
  
## 語法  
  
```  
class CSimpleRow  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|將參考次數 \(Reference Count\) 加入至現有的資料列控制代碼。|  
|[Compare](../../data/oledb/csimplerow-compare.md)|比較兩個資料列，以查看它們是否參考相同的資料列執行個體。|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|建構函式。|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|釋放資料列。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_dwRef](../../data/oledb/csimplerow-m-dwref.md)|參考次數 \(Reference Count\) 現有的資料列控制代碼。|  
|[m\_iRowset](../../data/oledb/csimplerow-m-irowset.md)|一個對行集合的索引代表游標。|  
  
## 備註  
 資料列控制代碼在邏輯上是結果資料行的唯一的標記。  `IRowsetImpl` 會在 [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)要求的每個資料列的新 `CSimpleRow` 。  因為它是預設樣板引數為 `IRowsetImpl`，則`CSimpleRow` 可以用您資料列控制代碼的實作來取代。  將取代這個類別的唯一要求是讓取代類別提供 **LONG**接受型別的單一參數的建構函式。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)