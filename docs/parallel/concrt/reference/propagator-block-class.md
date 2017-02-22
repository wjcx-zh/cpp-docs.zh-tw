---
title: "propagator_block 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::propagator_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propagator_block 類別"
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# propagator_block 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`propagator_block` 類別是同時為來源和目標之訊息區塊的抽象基底類別。  它結合 `source_block` 和 `target_block` 類別的功能。  
  
## 語法  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class propagator_block : public source_block<_TargetLinkRegistry, _MessageProcessorType>, public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### 參數  
 `_TargetLinkRegistry`  
 要用來保留目標連結的連結登錄。  
  
 `_SourceLinkRegistry`  
 要用來保留來源連結的連結登錄。  
  
 `_MessageProcessorType`  
 訊息處理的處理器型別。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`source_iterator`|這個 `propagator_block` 之 `source_link_manager` 的 Iterator 的型別。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[propagator\_block::propagator\_block 建構函式](../Topic/propagator_block::propagator_block%20Constructor.md)|建構 `propagator_block` 物件。|  
|[propagator\_block::~propagator\_block 解構函式](../Topic/propagator_block::~propagator_block%20Destructor.md)|終結 `propagator_block` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[propagator\_block::propagate 方法](../Topic/propagator_block::propagate%20Method.md)|以非同步方式將訊息從來源區塊傳遞到這個目標區塊。|  
|[propagator\_block::send 方法](../Topic/propagator_block::send%20Method.md)|以同步方式啟始這個區塊的訊息。  由 `ISource` 區塊呼叫。  當此函式完成時，已將訊息傳播至區塊中。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[propagator\_block::decline\_incoming\_messages 方法](../Topic/propagator_block::decline_incoming_messages%20Method.md)|表示應拒絕新訊息的區塊。|  
|[propagator\_block::initialize\_source\_and\_target 方法](../Topic/propagator_block::initialize_source_and_target%20Method.md)|初始化基底物件。  尤其必須初始化 `message_processor` 物件。|  
|[propagator\_block::link\_source 方法](../Topic/propagator_block::link_source%20Method.md)|連結指定的來源區塊與這個 `propagator_block` 物件。|  
|[propagator\_block::process\_input\_messages 方法](../Topic/propagator_block::process_input_messages%20Method.md)|處理輸入訊息。  這會將傳回者區塊才有用，從 source\_block \(覆寫衍生自 [source\_block::process\_input\_messages](../Topic/source_block::process_input_messages%20Method.md)\)。|  
|[propagator\_block::propagate\_message 方法](../Topic/propagator_block::propagate_message%20Method.md)|在衍生類別中被覆寫時，這個方法會以非同步方式從 `ISource` 區塊傳遞訊息到這個 `propagator_block` 物件。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[propagator\_block::register\_filter 方法](../Topic/propagator_block::register_filter%20Method.md)|註冊會在收到每個訊息時叫用的篩選方法。|  
|[propagator\_block::remove\_network\_links 方法](../Topic/propagator_block::remove_network_links%20Method.md)|移除這個 `propagator_block` 物件中的所有來源與目標網路連結。|  
|[propagator\_block::send\_message 方法](../Topic/propagator_block::send_message%20Method.md)|在衍生類別中被覆寫時，這個方法會以同步方式從 `ISource` 區塊傳遞訊息到這個 `propagator_block` 物件。  會於來源區塊呼叫時由 `send` 方法叫用。|  
|[propagator\_block::unlink\_source 方法](../Topic/propagator_block::unlink_source%20Method.md)|將指定的來源區塊與這個 `propagator_block` 物件中斷連結。|  
|[propagator\_block::unlink\_sources 方法](../Topic/propagator_block::unlink_sources%20Method.md)|將所有來源區塊與這個 `propagator_block` 物件中斷連結。\(會覆寫 [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md)\)。|  
  
## 備註  
 為避免多重繼承，`propagator_block` 類別會自 `source_block` 類別和 `ITarget` 抽象類別繼承。  `target_block` 類別的大多數功能是在這裡複寫的。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `propagator_block`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [source\_block 類別](../../../parallel/concrt/reference/source-block-class.md)   
 [ITarget 類別](../../../parallel/concrt/reference/itarget-class.md)