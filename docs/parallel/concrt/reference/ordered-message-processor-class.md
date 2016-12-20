---
title: "ordered_message_processor 類別 | Microsoft Docs"
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
  - "agents/concurrency::ordered_message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered_message_processor 類別"
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ordered_message_processor 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ordered_message_processor` 是 `message_processor`，可讓訊息區塊按照接收順序處理訊息。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class ordered_message_processor : public message_processor<_Type>;  
```  
  
#### 參數  
 `_Type`  
 由處理器處理的訊息內容承載型別。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`type`|`_Type` 的型別別名。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[ordered\_message\_processor::ordered\_message\_processor 建構函式](../Topic/ordered_message_processor::ordered_message_processor%20Constructor.md)|建構 `ordered_message_processor` 物件。|  
|[ordered\_message\_processor::~ordered\_message\_processor 解構函式](../Topic/ordered_message_processor::~ordered_message_processor%20Destructor.md)|終結 `ordered_message_processor` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ordered\_message\_processor::async\_send 方法](../Topic/ordered_message_processor::async_send%20Method.md)|以非同步方式向上佇列訊息，並且啟動處理工作 \(如果尚未這麼做\)。\(會覆寫 [message\_processor::async\_send](../Topic/message_processor::async_send%20Method.md)\)。|  
|[ordered\_message\_processor::Initialize 方法](../Topic/ordered_message_processor::initialize%20Method.md)|以適當的回呼函式、排程器和排程群組初始化 `ordered_message_processor` 物件。|  
|[ordered\_message\_processor::initialize\_batched\_processing 方法](../Topic/ordered_message_processor::initialize_batched_processing%20Method.md)|初始化批次處理訊息|  
|[ordered\_message\_processor::sync\_send 方法](../Topic/ordered_message_processor::sync_send%20Method.md)|以同步方式向上佇列訊息，並且啟動處理工作 \(如果尚未這麼做\)。\(會覆寫 [message\_processor::sync\_send](../Topic/message_processor::sync_send%20Method.md)\)。|  
|[ordered\_message\_processor::wait 方法](../Topic/ordered_message_processor::wait%20Method.md)|處理器特定微調等候，用於訊息區塊的解構函式，以確定所有非同步處理工作有時間完成，才能摧毀該區塊。\(會覆寫 [message\_processor::wait](../Topic/message_processor::wait%20Method.md)\)。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[ordered\_message\_processor::process\_incoming\_message 方法](../Topic/ordered_message_processor::process_incoming_message%20Method.md)|非同步呼叫之處理函式。  它會清除佇列中的訊息，並開始處理。\(會覆寫 [message\_processor::process\_incoming\_message](../Topic/message_processor::process_incoming_message%20Method.md)\)。|  
  
## 繼承階層  
 [message\_processor](../../../parallel/concrt/reference/message-processor-class.md)  
  
 `ordered_message_processor`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)