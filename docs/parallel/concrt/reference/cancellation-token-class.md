---
title: "cancellation_token 類別 | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token 類別"
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token` 類別表示可判斷某個作業是否已要求取消的能力。  特定語彙基元可以與 `task_group`、`structured_task_group` 或 `task` 產生關聯，來提供隱含取消。  如果與相關聯的 `cancellation_token_source` 已取消，也可以向它輪詢取消，或為它註冊回呼。  
  
## 語法  
  
```  
class cancellation_token;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token::cancellation\_token 建構函式](../Topic/cancellation_token::cancellation_token%20Constructor.md)||  
|[cancellation\_token::~cancellation\_token 解構函式](../Topic/cancellation_token::~cancellation_token%20Destructor.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token::deregister\_callback 方法](../Topic/cancellation_token::deregister_callback%20Method.md)|根據註冊時傳回的 `cancellation_token_registration` 物件，移除先前透過 `register` 方法註冊的回呼。|  
|[cancellation\_token::is\_cancelable 方法](../Topic/cancellation_token::is_cancelable%20Method.md)|傳回這個語彙基元是否可以取消的指示。|  
|[cancellation\_token::is\_canceled 方法](../Topic/cancellation_token::is_canceled%20Method.md)|如果語彙基元已取消，則傳回 `true`。|  
|[cancellation\_token::none 方法](../Topic/cancellation_token::none%20Method.md)|傳回永不需取消的取消語彙基元。|  
|[cancellation\_token::register\_callback 方法](../Topic/cancellation_token::register_callback%20Method.md)|使用語彙基元註冊回呼函式。  如果這個語彙基元已取消，將會進行回呼。  請注意，如果語彙基元已經在呼叫此方法的時點取消，將會立即並同步進行回呼。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token::operator\!\= 運算子](../Topic/cancellation_token::operator!=%20Operator.md)||  
|[cancellation\_token::operator\= 運算子](../Topic/cancellation_token::operator=%20Operator.md)||  
|[cancellation\_token::operator\=\= 運算子](../Topic/cancellation_token::operator==%20Operator.md)||  
  
## 繼承階層架構  
 `cancellation_token`  
  
## 需求  
 **標頭：** pplcancellation\_token.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)