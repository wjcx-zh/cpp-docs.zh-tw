---
title: "scheduler_ptr 結構 (並行執行階段) | Microsoft Docs"
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
  - "pplinterface/concurrency::scheduler_ptr"
dev_langs: 
  - "C++"
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 8
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_ptr 結構 (並行執行階段)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示排程器的指標。  這個類別是為了使用 shared\_ptr 或使用原始指標的簡單參考，允許共用存留期的規格。  
  
## 語法  
  
```  
struct scheduler_ptr;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[scheduler\_ptr::scheduler\_ptr 建構函式 \(並行執行階段\)](../Topic/scheduler_ptr::scheduler_ptr%20Constructor%20\(Concurrency%20Runtime\).md)|多載。  從排程器 shared\_ptr 建立排程器指標|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[scheduler\_ptr::get 方法 \(並行執行階段\)](../Topic/scheduler_ptr::get%20Method%20\(Concurrency%20Runtime\).md)|傳回排程器的原始指標|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[scheduler\_ptr::operator bool 運算子 \(並行執行階段\)](../Topic/scheduler_ptr::operator%20bool%20Operator%20\(Concurrency%20Runtime\).md)|測試排程器指標是否為非 null|  
|[scheduler\_ptr::operator\-\> 運算子 \(並行執行階段\)](../Topic/scheduler_ptr::operator-%3E%20Operator%20\(Concurrency%20Runtime\).md)|作用如同指標|  
  
## 繼承階層架構  
 `scheduler_ptr`  
  
## 需求  
 **標頭：**pplinterface.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)