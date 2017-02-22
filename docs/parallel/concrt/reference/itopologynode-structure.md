---
title: "ITopologyNode 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::ITopologyNode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyNode 結構"
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ITopologyNode 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

一個資源管理員所定義的拓撲節點的介面。  節點包含一個或多個執行資源。  
  
## 語法  
  
```  
struct ITopologyNode;  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ITopologyNode::GetExecutionResourceCount 方法](../Topic/ITopologyNode::GetExecutionResourceCount%20Method.md)|傳回在此節點下執行資源數目群組。|  
|[ITopologyNode::GetFirstExecutionResource 方法](../Topic/ITopologyNode::GetFirstExecutionResource%20Method.md)|傳回第一次執行資源群組在此節點下的列舉型別順序。|  
|[ITopologyNode::GetId 方法](../Topic/ITopologyNode::GetId%20Method.md)|傳回這個節點的資源管理員的唯一識別項。|  
|[ITopologyNode::GetNext 方法](../Topic/ITopologyNode::GetNext%20Method.md)|傳回介面對下拓撲節點的列舉型別順序。|  
|[ITopologyNode::GetNumaNode 方法](../Topic/ITopologyNode::GetNumaNode%20Method.md)|傳回這個資源 Manger 節點所屬的 Windows 指定 NUMA 節點編號。|  
  
## 備註  
 這個介面通常會套用查核系統的拓撲學做為由資源管理員的檢視。  
  
## 繼承階層  
 `ITopologyNode`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)