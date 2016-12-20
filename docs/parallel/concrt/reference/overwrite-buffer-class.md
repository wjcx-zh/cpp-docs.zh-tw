---
title: "overwrite_buffer 類別 | Microsoft Docs"
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
  - "agents/concurrency::overwrite_buffer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "overwrite_buffer 類別"
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# overwrite_buffer 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`overwrite_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，一次能夠存放一個訊息。  新訊息覆寫先前保留的訊息。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 參數  
 `_Type`  
 緩衝區預存及傳播的訊息的承載類型。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[overwrite\_buffer::overwrite\_buffer 建構函式](../Topic/overwrite_buffer::overwrite_buffer%20Constructor.md)|多載。  建構 `overwrite_buffer` 傳訊區塊。|  
|[overwrite\_buffer::~overwrite\_buffer 解構函式](../Topic/overwrite_buffer::~overwrite_buffer%20Destructor.md)|終結 `overwrite_buffer` 傳訊區塊。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[overwrite\_buffer::has\_value 方法](../Topic/overwrite_buffer::has_value%20Method.md)|會檢查這個 `overwrite_buffer` 傳訊區塊是否具有值。|  
|[overwrite\_buffer::value 方法](../Topic/overwrite_buffer::value%20Method.md)|取得訊息目前承載的參考，該訊息目前存放在 `overwrite_buffer` 傳訊區塊中。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[overwrite\_buffer::accept\_message 方法](../Topic/overwrite_buffer::accept_message%20Method.md)|接受這個 `overwrite_buffer` 傳訊區塊所提供的訊息，將訊息複本傳回給呼叫端。|  
|[overwrite\_buffer::consume\_message 方法](../Topic/overwrite_buffer::consume_message%20Method.md)|會將訊息複本傳回至呼叫端，使用 `overwrite_buffer` 傳訊區塊先前提供並由目標保留的訊息。|  
|[overwrite\_buffer::link\_target\_notification 方法](../Topic/overwrite_buffer::link_target_notification%20Method.md)|通知已有新目標與這個 `overwrite_buffer` 傳訊區塊相連結的回呼。|  
|[overwrite\_buffer::propagate\_message 方法](../Topic/overwrite_buffer::propagate_message%20Method.md)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `overwrite_buffer` 傳訊區塊。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[overwrite\_buffer::propagate\_to\_any\_targets 方法](../Topic/overwrite_buffer::propagate_to_any_targets%20Method.md)|將 `message``_PMessage` 置於此 `overwrite_buffer` 傳訊區塊中，並將它提供給所有連結目標。|  
|[overwrite\_buffer::release\_message 方法](../Topic/overwrite_buffer::release_message%20Method.md)|會釋放前一個訊息保留項目。\(會覆寫 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)\)。|  
|[overwrite\_buffer::reserve\_message 方法](../Topic/overwrite_buffer::reserve_message%20Method.md)|會保留先前由這個 `overwrite_buffer` 傳訊區塊所提供的訊息。\(會覆寫 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)\)。|  
|[overwrite\_buffer::resume\_propagation 方法](../Topic/overwrite_buffer::resume_propagation%20Method.md)|釋放保留項目之後繼續傳播。\(會覆寫 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)\)。|  
|[overwrite\_buffer::send\_message 方法](../Topic/overwrite_buffer::send_message%20Method.md)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `overwrite_buffer` 傳訊區塊。  會於來源區塊呼叫時由 `send` 方法叫用。|  
|[overwrite\_buffer::supports\_anonymous\_source 方法](../Topic/overwrite_buffer::supports_anonymous_source%20Method.md)|覆寫 `supports_anonymous_source` 方法指示這個區塊可以接受為它所提供的訊息由未連結的來源。\(覆寫 [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)\)。|  
  
## 備註  
 `overwrite_buffer` 傳訊區塊會傳播出其存放訊息的複本至其每一個目標。  
  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [unbounded\_buffer 類別](../Topic/unbounded_buffer%20Class.md)   
 [single\_assignment 類別](../../../parallel/concrt/reference/single-assignment-class.md)