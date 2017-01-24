---
title: "task_canceled 類別 | Microsoft Docs"
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
  - "concrt/concurrency::task_canceled"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_canceled 類別"
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
caps.latest.revision: 11
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_canceled 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的 PPL 工作層級，以強制取消目前的工作。  它也會藉由擲回`get()`上的方法[工作](../Topic/Task%20Class%20-%20Internal%20Members.md)，已取消的工作。  
  
## 語法  
  
```  
class task_canceled : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[task\_canceled::task\_canceled 建構函式](../Topic/task_canceled::task_canceled%20Constructor.md)|多載。  建構 `task_canceled` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `task_canceled`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task::get 方法](../Topic/task::get%20Method.md)   
 [cancel\_current\_task 函式](../Topic/cancel_current_task%20Function.md)