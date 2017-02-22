---
title: "message 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message 類別"
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# message 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

基本訊息信封，包含在傳訊區塊之間傳遞的資料承載。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class message : public ::Concurrency::details::_Runtime_object;  
```  
  
#### 參數  
 `_Type`  
 訊息內的承載的資料型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`type`|`_Type` 的型別別名。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[message::message 建構函式](../Topic/message::message%20Constructor.md)|多載。  建構 `message` 物件。|  
|[message::~message 解構函式](../Topic/message::~message%20Destructor.md)|終結 `message` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[message::add\_ref 方法](../Topic/message::add_ref%20Method.md)|加入至 `message` 物件的參考計數。  用於需要參考計數來決定訊息存留時間的訊息區塊。|  
|[message::msg\_id 方法](../Topic/message::msg_id%20Method.md)|傳回 `message` 物件的 ID。|  
|[message::remove\_ref 方法](../Topic/message::remove_ref%20Method.md)|從 `message` 物件的參考計數減去。  用於需要參考計數來決定訊息存留時間的訊息區塊。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[message::payload 資料成員](../Topic/message::payload%20Data%20Member.md)|`message` 物件的承載。|  
  
## 備註  
 如需詳細資訊，請參閱 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層架構  
 `message`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)