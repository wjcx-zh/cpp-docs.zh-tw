---
title: "task_options 類別 (並行執行階段) | Microsoft Docs"
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
  - "ppltasks/concurrency::task_options"
dev_langs: 
  - "C++"
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: 7
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_options 類別 (並行執行階段)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示用於建立工作的允許選項  
  
## 語法  
  
```  
class task_options;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[task\_options::task\_options 建構函式 \(並行執行階段\)](../Topic/task_options::task_options%20Constructor%20\(Concurrency%20Runtime\).md)|多載。  工作建立選項預設清單|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[task\_options::get\_cancellation\_token 方法 \(並行執行階段\)](../Topic/task_options::get_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|傳回取消語彙基元|  
|[task\_options::get\_continuation\_context 方法 \(並行執行階段\)](../Topic/task_options::get_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|傳回接續內容|  
|[task\_options::get\_scheduler 方法 \(並行執行階段\)](../Topic/task_options::get_scheduler%20Method%20\(Concurrency%20Runtime\).md)|傳回排程器|  
|[task\_options::has\_cancellation\_token 方法 \(並行執行階段\)](../Topic/task_options::has_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|表示使用者是否指定取消語彙基元|  
|[task\_options::has\_scheduler 方法 \(並行執行階段\)](../Topic/task_options::has_scheduler%20Method%20\(Concurrency%20Runtime\).md)|表示使用者是否指定排程器 n|  
|[task\_options::set\_cancellation\_token 方法 \(並行執行階段\)](../Topic/task_options::set_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|設定選項的特定語彙基元|  
|[task\_options::set\_continuation\_context 方法 \(並行執行階段\)](../Topic/task_options::set_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|設定選項的特定接續內容|  
  
## 繼承階層架構  
 `task_options`  
  
## 需求  
 **標頭：**ppltasks.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)