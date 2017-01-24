---
title: "operation_timed_out 類別 | Microsoft Docs"
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
  - "concrt/concurrency::operation_timed_out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operation_timed_out 類別"
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operation_timed_out 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述一項作業已逾時，擲回例外狀況。  
  
## 語法  
  
```  
class operation_timed_out : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[operation\_timed\_out::operation\_timed\_out 建構函式](../Topic/operation_timed_out::operation_timed_out%20Constructor.md)|多載。  建構 `operation_timed_out` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `operation_timed_out`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)