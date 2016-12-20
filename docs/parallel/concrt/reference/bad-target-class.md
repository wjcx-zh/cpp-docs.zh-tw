---
title: "bad_target 類別 | Microsoft Docs"
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
  - "concrt/concurrency::bad_target"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_target 類別"
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_target 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述訊息的區塊指定指標所執行的操作不正確的目標時，會擲回例外狀況。  
  
## 語法  
  
```  
class bad_target : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[bad\_target::bad\_target 建構函式](../Topic/bad_target::bad_target%20Constructor.md)|多載。  建構 `bad_target` 物件。|  
  
## 備註  
 擲回這個例外狀況的原因通常是目標嘗試使用保留供另一個目標使用的訊息，或是釋放它並未持有的保留。  
  
## 繼承階層架構  
 `exception`  
  
 `bad_target`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)