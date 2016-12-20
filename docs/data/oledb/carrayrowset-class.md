---
title: "CArrayRowset 類別 | Microsoft Docs"
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
  - "ATL.CArrayRowset<TAccessor>"
  - "ATL.CArrayRowset"
  - "CArrayRowset"
  - "ATL::CArrayRowset"
  - "ATL::CArrayRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArrayRowset 類別"
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArrayRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用陣列語法，存取資料列集的項目。  
  
## 語法  
  
```  
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別的型別要使用資料列集。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|建構函式。|  
|[快照集](../../data/oledb/carrayrowset-snapshot.md)|讀取整個資料列集至記憶體。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 &#91;&#93;](../../data/oledb/carrayrowset-operator.md)|存取資料列集的項目。|  
  
### 資料成員  
  
|||  
|-|-|  
|[CArrayRowset::m\_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|已讀取的資料列數目。|  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset 類別](../../data/oledb/crowset-class.md)