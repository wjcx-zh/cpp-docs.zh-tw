---
title: "cancellation_token_registration 類別 | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token_registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_registration 類別"
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token_registration 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token_registration` 類別表示來自 `cancellation_token` 的回呼通知。  當 `cancellation_token` 的 `register` 方法用來接收發生取消的通知時，則會傳回 `cancellation_token_registration` 物件做為回呼的控制代碼，讓呼叫端可以要求不再透過使用 `deregister` 方法發出的特定回呼。  
  
## 語法  
  
```  
class cancellation_token_registration;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token\_registration::cancellation\_token\_registration 建構函式](../Topic/cancellation_token_registration::cancellation_token_registration%20Constructor.md)||  
|[cancellation\_token\_registration::~cancellation\_token\_registration 解構函式](../Topic/cancellation_token_registration::~cancellation_token_registration%20Destructor.md)||  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token\_registration::operator\!\= 運算子](../Topic/cancellation_token_registration::operator!=%20Operator.md)||  
|[cancellation\_token\_registration::operator\= 運算子](../Topic/cancellation_token_registration::operator=%20Operator.md)||  
|[cancellation\_token\_registration::operator\=\= 運算子](../Topic/cancellation_token_registration::operator==%20Operator.md)||  
  
## 繼承階層架構  
 `cancellation_token_registration`  
  
## 需求  
 **標頭：** pplcancellation\_token.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)