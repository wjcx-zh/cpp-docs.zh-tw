---
title: "ITopologyExecutionResource 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::ITopologyExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyExecutionResource 結構"
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ITopologyExecutionResource 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

一個資源管理員所定義的執行資源的介面。  
  
## 語法  
  
```  
struct ITopologyExecutionResource;  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ITopologyExecutionResource::GetId 方法](../Topic/ITopologyExecutionResource::GetId%20Method.md)|對於執行資源傳回資源管理員的唯一識別項。|  
|[ITopologyExecutionResource::GetNext 方法](../Topic/ITopologyExecutionResource::GetNext%20Method.md)|傳回介面對下執行資源的列舉型別順序。|  
  
## 備註  
 這個介面通常會套用查核系統的拓撲學做為由資源管理員的檢視。  
  
## 繼承階層  
 `ITopologyExecutionResource`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)