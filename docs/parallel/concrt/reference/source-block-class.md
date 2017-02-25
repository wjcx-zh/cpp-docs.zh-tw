---
title: "source_block 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::source_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_block 類別"
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# source_block 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`source_block` 類別是僅限來源區塊的抽象基底類別。  類別會提供基本連結管理功能與常見的錯誤檢查功能。  
  
## 語法  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;  
```  
  
#### 參數  
 `_TargetLinkRegistry`  
 要用來進行持有目標連結的連結登錄。  
  
 `_MessageProcessorType`  
 訊息處理的處理器型別。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`target_iterator`|查核連接目標的 Iterator。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[source\_block::source\_block 建構函式](../Topic/source_block::source_block%20Constructor.md)|建構 `source_block` 物件。|  
|[source\_block::~source\_block 解構函式](../Topic/source_block::~source_block%20Destructor.md)|終結 `source_block` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[source\_block::accept 方法](../Topic/source_block::accept%20Method.md)|接受這個 `source_block` 物件所提供的訊息，將擁有權轉移至呼叫端。|  
|[source\_block::acquire\_ref 方法](../Topic/source_block::acquire_ref%20Method.md)|取得這個 `source_block` 物件的參考計數，以防止刪除。|  
|[source\_block::consume 方法](../Topic/source_block::consume%20Method.md)|會將擁有權轉移至呼叫端，使用此 `source_block` 物件先前提供並由目標成功保留的訊息。|  
|[source\_block::link\_target 方法](../Topic/source_block::link_target%20Method.md)|連結目標會封鎖這個 `source_block` 物件。|  
|[source\_block::release 方法](../Topic/source_block::release%20Method.md)|會釋放前一個成功的訊息保留項目。|  
|[source\_block::release\_ref 方法](../Topic/source_block::release_ref%20Method.md)|釋放此 `source_block` 物件的參考計數。|  
|[source\_block::reserve 方法](../Topic/source_block::reserve%20Method.md)|會保留先前由這個 `source_block` 物件所提供的訊息。|  
|[source\_block::unlink\_target 方法](../Topic/source_block::unlink_target%20Method.md)|將目標區塊與這個 `source_block` 物件中斷連結。|  
|[source\_block::unlink\_targets 方法](../Topic/source_block::unlink_targets%20Method.md)|將所有區塊與這個 `source_block` 物件中斷連結。\(會覆寫 [ISource::unlink\_targets](../Topic/ISource::unlink_targets%20Method.md)\)。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[source\_block::accept\_message 方法](../Topic/source_block::accept_message%20Method.md)|在衍生類別中被覆寫時，接受由來源提供的訊息。  訊息區塊應該覆寫這個方法，以驗證 `_MsgId` 並傳回訊息。|  
|[source\_block::async\_send 方法](../Topic/source_block::async_send%20Method.md)|以非同步方式向上佇列訊息，並且啟動傳播工作 \(如果尚未這麼做\)|  
|[source\_block::consume\_message 方法](../Topic/source_block::consume_message%20Method.md)|在衍生類別中被覆寫時，會消耗先前已保留的訊息。|  
|[source\_block::enable\_batched\_processing 方法](../Topic/source_block::enable_batched_processing%20Method.md)|啟用批次處理了這個區塊。|  
|[source\_block::initialize\_source 方法](../Topic/source_block::initialize_source%20Method.md)|初始化此 `source_block` 中的 `message_propagator`。|  
|[source\_block::link\_target\_notification 方法](../Topic/source_block::link_target_notification%20Method.md)|通知已有新目標與這個 `source_block` 物件相連結的回呼。|  
|[source\_block::process\_input\_messages 方法](../Topic/source_block::process_input_messages%20Method.md)|處理輸入訊息。  這會將傳回者區塊才有用，從 source\_block 衍生|  
|[source\_block::propagate\_output\_messages 方法](../Topic/source_block::propagate_output_messages%20Method.md)|對目標的傳播訊息。|  
|[source\_block::propagate\_to\_any\_targets 方法](../Topic/source_block::propagate_to_any_targets%20Method.md)|在衍生類別中被覆寫時，將指定的訊息傳播至任何或所有連結的目標。  這是訊息區塊主要的傳播慣例。|  
|[source\_block::release\_message 方法](../Topic/source_block::release_message%20Method.md)|在衍生類別中被覆寫時，釋放前一個訊息保留項目。|  
|[source\_block::remove\_targets 方法](../Topic/source_block::remove_targets%20Method.md)|移除這個來源區塊的所有目標連結。  這應從解構函式呼叫。|  
|[source\_block::reserve\_message 方法](../Topic/source_block::reserve_message%20Method.md)|在衍生類別中被覆寫時，保留先前由這個 `source_block` 物件所提供的訊息。|  
|[source\_block::resume\_propagation 方法](../Topic/source_block::resume_propagation%20Method.md)|在衍生類別中被覆寫時，在釋放保留後恢復傳播。|  
|[source\_block::sync\_send 方法](../Topic/source_block::sync_send%20Method.md)|以同步方式向上佇列訊息，並且啟動傳播工作 \(如果尚未這麼做\)。|  
|[source\_block::unlink\_target\_notification 方法](../Topic/source_block::unlink_target_notification%20Method.md)|通知已有目標與這個 `source_block` 物件解除連結的回呼。|  
|[source\_block::wait\_for\_outstanding\_async\_sends 方法](../Topic/source_block::wait_for_outstanding_async_sends%20Method.md)|等候所有非同步傳播完成。  這個傳播程式特定微調等候用於訊息區塊的解構函式，以確定所有的非同步傳播有時間完成，才能摧毀該區塊。|  
  
## 備註  
 訊息區塊應該衍生自這個區塊，以善用此類別提供的連結管理和同步處理。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `source_block`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource 類別](../../../parallel/concrt/reference/isource-class.md)