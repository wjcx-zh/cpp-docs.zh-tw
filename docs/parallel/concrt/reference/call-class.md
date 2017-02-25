---
title: "call 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::call"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call 類別"
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# call 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`call` 傳訊區塊是一個多來源的排序 `target_block`， 接收訊息時會叫用指定的函式。  
  
## 語法  
  
```  
template<  
   class _Type,  
   class _FunctorType = std::tr1::function<void(_Type const&)>  
>  
class call : public target_block<multi_link_registry<ISource<_Type>>>;  
```  
  
#### 參數  
 `_Type`  
 傳播至此區塊之訊息的承載類型。  
  
 `_FunctorType`  
 這個區塊可以接受的函式簽章。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[call::call 建構函式](../Topic/call::call%20Constructor.md)|多載。  建構 `call` 傳訊區塊。|  
|[call::~call 解構函式](../Topic/call::~call%20Destructor.md)|終結 `call` 傳訊區塊。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[call::process\_input\_messages 方法](../Topic/call::process_input_messages%20Method.md)|執行輸入訊息的呼叫函式。|  
|[call::process\_message 方法](../Topic/call::process_message%20Method.md)|處理這個 `call` 傳訊區塊所接受的訊息。|  
|[call::propagate\_message 方法](../Topic/call::propagate_message%20Method.md)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 傳訊區塊。  會於來源區塊呼叫時由 `propagate` 方法叫用。|  
|[call::send\_message 方法](../Topic/call::send_message%20Method.md)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 傳訊區塊。  會於來源區塊呼叫時由 `send` 方法叫用。|  
|[call::supports\_anonymous\_source 方法](../Topic/call::supports_anonymous_source%20Method.md)|覆寫 `supports_anonymous_source` 方法指示這個區塊可以接受為它所提供的訊息由未連結的來源。\(覆寫 [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)\)。|  
  
## 備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [target\_block](../../../parallel/concrt/reference/target-block-class.md)  
  
 `call`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [transformer 類別](../../../parallel/concrt/reference/transformer-class.md)