---
title: "task_completion_event 類別 | Microsoft Docs"
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
  - "ppltasks/concurrency::task_completion_event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_completion_event 類別"
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: 11
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_completion_event 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_completion_event` 類別可讓您延遲工作的執行，直到滿足條件為止，或者啟動工作以回應外部事件。  
  
## 語法  
  
```  
template<  
   typename _ResultType  
>  
class task_completion_event;  
  
template<>  
class task_completion_event<void>;  
```  
  
#### 參數  
 `_ResultType`  
 此 `task_completion_event` 類別的結果類型。  
  
 `T`  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[task\_completion\_event::task\_completion\_event 建構函式](../Topic/task_completion_event::task_completion_event%20Constructor.md)|建構 `task_completion_event` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[task\_completion\_event::set 方法](../Topic/task_completion_event::set%20Method.md)|多載。  設定工作完成事件。|  
|[task\_completion\_event::set\_exception 方法](../Topic/task_completion_event::set_exception%20Method.md)|多載。  傳播例外狀況至與這個事件相關聯的所有工作。|  
  
## 備註  
 當案例需要您建立要完成的工作時，使用從工作完成事件建立的工作，因此將其接續排程在未來的某個時間點執行。  `task_completion_event` 必須與您建立的工作具有相同類型，而且在具有該類型值的工作完成事件上呼叫 Set 方法，將導致關聯工作完成，並將該值當做結果提供給其接續。  
  
 如果永不發出工作完成事件的信號，則工作解構時會取消從它建立的所有工作。  
  
 `task_completion_event` 的行為就像智慧型指標，應該透過傳值方式傳遞。  
  
## 繼承階層架構  
 `task_completion_event`  
  
## 需求  
 **標頭：**ppltasks.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/zh-tw/5389e8a5-5038-40b6-844a-55e9b58ad35f)