---
title: "message_not_found 類別 | Microsoft Docs"
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
  - "concrt/concurrency::message_not_found"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_not_found 類別"
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# message_not_found 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述訊息的區塊就是找不到要求的訊息時，擲回例外狀況。  
  
## 語法  
  
```  
class message_not_found : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[message\_not\_found::message\_not\_found 建構函式](../Topic/message_not_found::message_not_found%20Constructor.md)|多載。  建構 `message_not_found` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `message_not_found`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)