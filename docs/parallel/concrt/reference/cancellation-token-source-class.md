---
title: "cancellation_token_source 類別 | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_source 類別"
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token_source 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token_source` 類別表示取消某個可取消作業的能力。  
  
## 語法  
  
```  
class cancellation_token_source;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token\_source::cancellation\_token\_source 建構函式](../Topic/cancellation_token_source::cancellation_token_source%20Constructor.md)|多載。  建構新的 `cancellation_token_source`。  來源可用於將某個可取消作業的取消加上標幟。|  
|[cancellation\_token\_source::~cancellation\_token\_source 解構函式](../Topic/cancellation_token_source::~cancellation_token_source%20Destructor.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token\_source::cancel 方法](../Topic/cancellation_token_source::cancel%20Method.md)|取消語彙基元。  任何使用語彙基元的 `task_group`、`structured_task_group` 或 `task` 都會在進行這個呼叫時取消，並在下一個中斷點擲回例外狀況。|  
|[cancellation\_token\_source::create\_linked\_source 方法](../Topic/cancellation_token_source::create_linked_source%20Method.md)|多載。  建立 `cancellation_token_source`，其會在提供的語彙基元已取消時取消。|  
|[cancellation\_token\_source::get\_token 方法](../Topic/cancellation_token_source::get_token%20Method.md)|傳回與此來源相關聯的取消語彙基元。  傳回的語彙基元可用於輪詢取消或在發生取消時提供回呼。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[cancellation\_token\_source::operator\!\= 運算子](../Topic/cancellation_token_source::operator!=%20Operator.md)||  
|[cancellation\_token\_source::operator\= 運算子](../Topic/cancellation_token_source::operator=%20Operator.md)||  
|[cancellation\_token\_source::operator\=\= 運算子](../Topic/cancellation_token_source::operator==%20Operator.md)||  
  
## 繼承階層架構  
 `cancellation_token_source`  
  
## 需求  
 **標頭：** pplcancellation\_token.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)