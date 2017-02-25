---
title: "timer 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::timer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "timer 類別"
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# timer 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`timer` 傳訊區塊是單一目標 `source_block`，能夠在經過指定的時間長度或在特定時間間隔，將訊息傳送至它的目標。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<_Type>>>;  
```  
  
#### 參數  
 `_Type`  
 此區塊之輸出訊息的承載類型。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[timer::timer 建構函式](../Topic/timer::timer%20Constructor.md)|多載。  建構會在指定的間隔之後引發指定訊息的 `timer` 傳訊區塊。|  
|[timer::~timer 解構函式](../Topic/timer::~timer%20Destructor.md)|終結 `timer` 傳訊區塊。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[timer::pause 方法](../Topic/timer::pause%20Method.md)|會停止 `timer` 傳訊區塊。  如果是重複的 `timer` 傳訊區塊，即可由後續 `start()` 呼叫重新啟動。  在非重複計時器中，這和 `stop` 呼叫的效果相同。|  
|[timer::start 方法](../Topic/timer::start%20Method.md)|啟動 `timer` 傳訊區塊。  呼叫這個之後的指定毫妙數，指定的值會向下傳播為 `message`。|  
|[timer::stop 方法](../Topic/timer::stop%20Method.md)|會停止 `timer` 傳訊區塊。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[timer::accept\_message 方法](../Topic/timer::accept_message%20Method.md)|接受這個 `timer` 傳訊區塊所提供的訊息，將擁有權轉移至呼叫端。|  
|[timer::consume\_message 方法](../Topic/timer::consume_message%20Method.md)|會將擁有權轉移至呼叫端，使用 `timer` 先前提供並由目標保留的訊息。|  
|[timer::link\_target\_notification 方法](../Topic/timer::link_target_notification%20Method.md)|通知已有新目標與這個 `timer` 傳訊區塊相連結的回呼。|  
|[timer::propagate\_to\_any\_targets 方法](../Topic/timer::propagate_to_any_targets%20Method.md)|嘗試提供 `timer` 區塊產生的訊息至所有連結的目標。|  
|[timer::release\_message 方法](../Topic/timer::release_message%20Method.md)|會釋放前一個訊息保留項目。\(會覆寫 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)\)。|  
|[timer::reserve\_message 方法](../Topic/timer::reserve_message%20Method.md)|會保留先前由這個 `timer` 傳訊區塊所提供的訊息。\(會覆寫 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)\)。|  
|[timer::resume\_propagation 方法](../Topic/timer::resume_propagation%20Method.md)|釋放保留項目之後繼續傳播。\(會覆寫 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)\)。|  
  
## 備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `timer`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)