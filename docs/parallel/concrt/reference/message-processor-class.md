---
title: "message_processor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_processor 類別"
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# message_processor 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`message_processor` 類別是處理 `message` 物件的抽象基底類別。  不保證訊息順序。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class message_processor;  
```  
  
#### 參數  
 `_Type`  
 此`message_processor` 物件所處理的訊息內之承載的資料型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`type`|`_Type` 的型別別名。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[message\_processor::async\_send 方法](../Topic/message_processor::async_send%20Method.md)|在衍生類別中被覆寫時，以非同步方式將訊息放置到區塊中。|  
|[message\_processor::sync\_send 方法](../Topic/message_processor::sync_send%20Method.md)|在衍生類別中被覆寫時，以同步方式將訊息放置到區塊中。|  
|[message\_processor::wait 方法](../Topic/message_processor::wait%20Method.md)|在衍生類別中被覆寫時，等候所有非同步作業完成。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[message\_processor::process\_incoming\_message 方法](../Topic/message_processor::process_incoming_message%20Method.md)|在衍生類別中被覆寫時，執行順向處理訊息到區塊。  每當加入新訊息且佇列是空的時呼叫一次。|  
  
## 繼承階層架構  
 `message_processor`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ordered\_message\_processor 類別](../../../parallel/concrt/reference/ordered-message-processor-class.md)