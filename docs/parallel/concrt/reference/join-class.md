---
title: "join 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::join"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "join 類別"
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# join 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`join` 傳訊區塊是單一目標、多來源的排序  `propagator_block`，會與來自其每個來源的 `_Type` 類型訊息合併。  
  
## 語法  
  
```  
template<  
   class _Type,  
   join_type _Jtype = non_greedy  
>  
class join : public propagator_block<single_link_registry<ITarget<std::vector<_Type>>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 參數  
 `_Type`  
 區塊所聯結和傳播的訊息的承載類型。  
  
 `_Jtype`  
 這個 `join` 區塊的種類是 `greedy` 或 `non_greedy`  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[join::join 建構函式](../Topic/join::join%20Constructor.md)|多載。  建構 `join` 傳訊區塊。|  
|[join::~join 解構函式](../Topic/join::~join%20Destructor.md)|終結 `join` 區塊。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[join::accept\_message 方法](../Topic/join::accept_message%20Method.md)|接受這個 `join` 傳訊區塊所提供的訊息，將擁有權轉移至呼叫端。|  
|[join::consume\_message 方法](../Topic/join::consume_message%20Method.md)|會將擁有權轉移至呼叫端，使用 `join` 傳訊區塊先前提供並由目標保留的訊息。|  
|[join::link\_target\_notification 方法](../Topic/join::link_target_notification%20Method.md)|通知已有新目標與這個 `join` 傳訊區塊相連結的回呼。|  
|[join::propagate\_message 方法](../Topic/join::propagate_message%20Method.md)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `join` 傳訊區塊。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[join::propagate\_to\_any\_targets 方法](../Topic/join::propagate_to_any_targets%20Method.md)|建構輸出訊息，其中包含每個來源全部傳播訊息時送出的傳入訊息。  將這個輸出訊息傳送至其每一個目標。|  
|[join::release\_message 方法](../Topic/join::release_message%20Method.md)|會釋放前一個訊息保留項目。\(會覆寫 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)\)。|  
|[join::reserve\_message 方法](../Topic/join::reserve_message%20Method.md)|會保留先前由這個 `join` 傳訊區塊所提供的訊息。\(會覆寫 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)\)。|  
|[join::resume\_propagation 方法](../Topic/join::resume_propagation%20Method.md)|釋放保留項目之後繼續傳播。\(會覆寫 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)\)。|  
  
## 備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `join`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [choice 類別](../../../parallel/concrt/reference/choice-class.md)   
 [multitype\_join 類別](../../../parallel/concrt/reference/multitype-join-class.md)   
 [join\_type 列舉](../Topic/join_type%20Enumeration.md)