---
title: "transformer 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::transformer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transformer 類別"
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# transformer 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`transformer` 傳訊區塊是多來源的單一目標排序 `propagator_block`，可以存放無限個不同類型訊息。  
  
## 語法  
  
```  
template<  
   class _Input,  
   class _Output  
>  
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>, multi_link_registry<ISource<_Input>>>;  
```  
  
#### 參數  
 `_Input`  
 緩衝區所接受的訊息的承載類型。  
  
 `_Output`  
 緩衝區預存及對外傳播的訊息的承載類型。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[transformer::transformer 建構函式](../Topic/transformer::transformer%20Constructor.md)|多載。  建構 `transformer` 傳訊區塊。|  
|[transformer::~transformer 解構程式](../Topic/transformer::~transformer%20Destructor.md)|終結 `transformer` 傳訊區塊。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[transformer::accept\_message 方法](../Topic/transformer::accept_message%20Method.md)|接受這個 `transformer` 傳訊區塊所提供的訊息，將擁有權轉移至呼叫端。|  
|[transformer::consume\_message 方法](../Topic/transformer::consume_message%20Method.md)|會將擁有權轉移至呼叫端，使用 `transformer` 先前提供並由目標保留的訊息。|  
|[transformer::link\_target\_notification 方法](../Topic/transformer::link_target_notification%20Method.md)|通知已有新目標與這個 `transformer` 傳訊區塊相連結的回呼。|  
|[transformer::propagate\_message 方法](../Topic/transformer::propagate_message%20Method.md)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 傳訊區塊。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[transformer::propagate\_to\_any\_targets 方法](../Topic/transformer::propagate_to_any_targets%20Method.md)|執行輸入訊息的變化函式。|  
|[transformer::release\_message 方法](../Topic/transformer::release_message%20Method.md)|會釋放前一個訊息保留項目。\(會覆寫 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)\)。|  
|[transformer::reserve\_message 方法](../Topic/transformer::reserve_message%20Method.md)|會保留先前由這個 `transformer` 傳訊區塊所提供的訊息。\(會覆寫 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)\)。|  
|[transformer::resume\_propagation 方法](../Topic/transformer::resume_propagation%20Method.md)|釋放保留項目之後繼續傳播。\(會覆寫 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)\)。|  
|[transformer::send\_message 方法](../Topic/transformer::send_message%20Method.md)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 傳訊區塊。  會於來源區塊呼叫時由 `send` 方法叫用。|  
|[transformer::supports\_anonymous\_source 方法](../Topic/transformer::supports_anonymous_source%20Method.md)|覆寫 `supports_anonymous_source` 方法指示這個區塊可以接受為它所提供的訊息由未連結的來源。\(覆寫 [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)\)。|  
  
## 備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `transformer`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [call 類別](../../../parallel/concrt/reference/call-class.md)