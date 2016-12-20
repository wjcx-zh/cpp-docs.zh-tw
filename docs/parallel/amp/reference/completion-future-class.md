---
title: "completion_future 類別 | Microsoft Docs"
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
  - "amprt/Concurrency::completion_future"
dev_langs: 
  - "C++"
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# completion_future 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示對應 C\+\+ AMP 非同步處理操作的 future 。  
  
## 語法  
  
```  
class completion_future;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[completion\_future::completion\_future 建構函式](../Topic/completion_future::completion_future%20Constructor.md)|初始化 `completion_future` 類別的新執行個體。|  
|[completion\_future::~completion\_future 解構函式](../Topic/completion_future::~completion_future%20Destructor.md)|終結 `completion_future` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[completion\_future::get 方法](../Topic/completion_future::get%20Method.md)|等候直到關聯的非同步作業完成為止。|  
|[completion\_future::then 方法](../Topic/completion_future::then%20Method.md)|將回呼函式物件鏈結至，要在相關聯非同步處理作業完成執行時執行的 `completion_future` 物件。|  
|[completion\_future::to\_task 方法](../Topic/completion_future::to_task%20Method.md)|傳回與相關聯的非同步作業對應的 `task` 物件。|  
|[completion\_future::valid 方法](../Topic/completion_future::valid%20Method.md)|取得布林值，表示物件是否與非同步作業有關聯。|  
|[completion\_future::wait 方法](../Topic/completion_future::wait%20Method.md)|封鎖直到相關聯的非同步處理作業完成為止。|  
|[completion\_future::wait\_for 方法](../Topic/completion_future::wait_for%20Method.md)|封鎖直到相關聯的非同步處理作業已經完成，或者已經過由 `_Rel_time` 所指定的時間為止。|  
|[completion\_future::wait\_until 方法](../Topic/completion_future::wait_until%20Method.md)|封鎖直到相關聯的非同步作業完成，或目前時間超過 `_Abs_time` 指定的值為止。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[completion\_future::operator std::shared\_future\<void\> 運算子](../Topic/completion_future::operator%20std::shared_future%3Cvoid%3E%20Operator.md)|隱含轉換 `std::shared_future` 物件成 `completion_future` 物件。|  
|[completion\_future::operator\= 運算式](../Topic/completion_future::operator=%20Operator.md)|將指定之 `completion_future` 物件的內容複製到這個物件。|  
  
## 繼承階層架構  
 `completion_future`  
  
## 需求  
 **標頭：**amprt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)