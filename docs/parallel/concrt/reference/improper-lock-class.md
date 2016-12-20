---
title: "improper_lock 類別 | Microsoft Docs"
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
  - "concrt/concurrency::improper_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_lock 類別"
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_lock 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述不當取得鎖定時，擲回例外狀況。  
  
## 語法  
  
```  
class improper_lock : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[improper\_lock::improper\_lock 建構函式](../Topic/improper_lock::improper_lock%20Constructor.md)|多載。  建構 `improper_lock exception`。|  
  
## 備註  
 通常，當嘗試在相同的內容遞迴取得不可重新進入的鎖定時，會擲回這個例外狀況。  
  
## 繼承階層架構  
 `exception`  
  
 `improper_lock`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section 類別](../../../parallel/concrt/reference/critical-section-class.md)   
 [reader\_writer\_lock 類別](../../../parallel/concrt/reference/reader-writer-lock-class.md)