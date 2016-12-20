---
title: "single_assignment 類別 | Microsoft Docs"
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
  - "agents/concurrency::single_assignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single_assignment 類別"
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# single_assignment 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`single_assignment` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠儲存寫入一次的單一 `message`。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class single_assignment : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 參數  
 `_Type`  
 緩衝區預存及傳播的訊息的承載類型。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[single\_assignment::single\_assignment 建構函式](../Topic/single_assignment::single_assignment%20Constructor.md)|多載。  建構 `single_assignment` 傳訊區塊。|  
|[single\_assignment::~single\_assignment 解構函式](../Topic/single_assignment::~single_assignment%20Destructor.md)|終結 `single_assignment` 傳訊區塊。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[single\_assignment::has\_value 方法](../Topic/single_assignment::has_value%20Method.md)|會檢查這個 `single_assignment` 傳訊區塊是否已初始化並具有值。|  
|[single\_assignment::value 方法](../Topic/single_assignment::value%20Method.md)|取得訊息目前承載的參考，該訊息目前存放在 `single_assignment` 傳訊區塊中。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[single\_assignment::accept\_message 方法](../Topic/single_assignment::accept_message%20Method.md)|接受這個 `single_assignment` 傳訊區塊所提供的訊息，將訊息複本傳回給呼叫端。|  
|[single\_assignment::consume\_message 方法](../Topic/single_assignment::consume_message%20Method.md)|會將訊息複本傳回至呼叫端，使用 `single_assignment` 先前提供並由目標保留的訊息。|  
|[single\_assignment::link\_target\_notification 方法](../Topic/single_assignment::link_target_notification%20Method.md)|通知已有新目標與這個 `single_assignment` 傳訊區塊相連結的回呼。|  
|[single\_assignment::propagate\_message 方法](../Topic/single_assignment::propagate_message%20Method.md)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 傳訊區塊。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[single\_assignment::propagate\_to\_any\_targets 方法](../Topic/single_assignment::propagate_to_any_targets%20Method.md)|將 `message``_PMessage` 置於此 `single_assignment` 傳訊區塊中，並將它提供給所有連結目標。|  
|[single\_assignment::release\_message 方法](../Topic/single_assignment::release_message%20Method.md)|會釋放前一個訊息保留項目。\(會覆寫 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)\)。|  
|[single\_assignment::reserve\_message 方法](../Topic/single_assignment::reserve_message%20Method.md)|會保留先前由這個 `single_assignment` 傳訊區塊所提供的訊息。\(會覆寫 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)\)。|  
|[single\_assignment::resume\_propagation 方法](../Topic/single_assignment::resume_propagation%20Method.md)|釋放保留項目之後繼續傳播。\(會覆寫 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)\)。|  
|[single\_assignment::send\_message 方法](../Topic/single_assignment::send_message%20Method.md)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 傳訊區塊。  會於來源區塊呼叫時由 `send` 方法叫用。|  
  
## 備註  
 `single_assignment` 傳訊區塊會傳播出每個目標其訊息的複本。  
  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `single_assignment`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [overwrite\_buffer 類別](../../../parallel/concrt/reference/overwrite-buffer-class.md)   
 [unbounded\_buffer 類別](../Topic/unbounded_buffer%20Class.md)