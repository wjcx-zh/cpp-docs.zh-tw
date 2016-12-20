---
title: "target_block 類別 | Microsoft Docs"
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
  - "agents/concurrency::target_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "target_block 類別"
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# target_block 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`target_block` 類別是提供基本的連結管理功能和錯誤檢查僅限目標區塊的抽象基底類別。  
  
## 語法  
  
```  
template<  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>  
>  
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### 參數  
 `_SourceLinkRegistry`  
 要用來保留來源連結的連結登錄。  
  
 `_MessageProcessorType`  
 訊息處理的處理器型別。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`source_iterator`|此 `target_block` 物件之 `source_link_manager` 的 Iterator 類型。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[target\_block::target\_block 建構函式](../Topic/target_block::target_block%20Constructor.md)|建構 `target_block` 物件。|  
|[target\_block::~target\_block 解構函式](../Topic/target_block::~target_block%20Destructor.md)|終結 `target_block` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[target\_block::propagate 方法](../Topic/target_block::propagate%20Method.md)|以非同步方式將訊息從來源區塊傳遞到這個目標區塊。|  
|[target\_block::send 方法](../Topic/target_block::send%20Method.md)|以同步方式將訊息從來源區塊傳遞到這個目標區塊。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[target\_block::async\_send 方法](../Topic/target_block::async_send%20Method.md)|以非同步方式傳送訊息，以進行處理。|  
|[target\_block::decline\_incoming\_messages 方法](../Topic/target_block::decline_incoming_messages%20Method.md)|表示應拒絕新訊息的區塊。|  
|[target\_block::enable\_batched\_processing 方法](../Topic/target_block::enable_batched_processing%20Method.md)|啟用批次處理了這個區塊。|  
|[target\_block::initialize\_target 方法](../Topic/target_block::initialize_target%20Method.md)|初始化基底物件。  尤其必須初始化 `message_processor` 物件。|  
|[target\_block::link\_source 方法](../Topic/target_block::link_source%20Method.md)|連結指定的來源區塊與這個 `target_block` 物件。|  
|[target\_block::process\_input\_messages 方法](../Topic/target_block::process_input_messages%20Method.md)|處理收到的輸入的訊息。|  
|[target\_block::process\_message 方法](../Topic/target_block::process_message%20Method.md)|在衍生類別中被覆寫時，處理這個 `target_block` 物件接受的訊息。|  
|[target\_block::propagate\_message 方法](../Topic/target_block::propagate_message%20Method.md)|在衍生類別中被覆寫時，這個方法會以非同步方式從 `ISource` 區塊傳遞訊息到這個 `target_block` 物件。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[target\_block::register\_filter 方法](../Topic/target_block::register_filter%20Method.md)|註冊會在收到每個訊息時叫用的篩選方法。|  
|[target\_block::remove\_sources 方法](../Topic/target_block::remove_sources%20Method.md)|等候未完成的非同步傳送作業完成後，中斷連結所有來源。|  
|[target\_block::send\_message 方法](../Topic/target_block::send_message%20Method.md)|在衍生類別中被覆寫時，這個方法會以同步方式從 `ISource` 區塊傳遞訊息到這個 `target_block` 物件。  會於來源區塊呼叫時由 `send` 方法叫用。|  
|[target\_block::sync\_send 方法](../Topic/target_block::sync_send%20Method.md)|以同步方式傳送訊息以進行處理。|  
|[target\_block::unlink\_source 方法](../Topic/target_block::unlink_source%20Method.md)|將指定的來源區塊與這個 `target_block` 物件中斷連結。|  
|[target\_block::unlink\_sources 方法](../Topic/target_block::unlink_sources%20Method.md)|將所有來源區塊與這個 `target_block` 物件中斷連結。\(會覆寫 [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md)\)。|  
|[target\_block::wait\_for\_async\_sends 方法](../Topic/target_block::wait_for_async_sends%20Method.md)|等候所有非同步傳播完成。|  
  
## 繼承階層  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 `target_block`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget 類別](../../../parallel/concrt/reference/itarget-class.md)