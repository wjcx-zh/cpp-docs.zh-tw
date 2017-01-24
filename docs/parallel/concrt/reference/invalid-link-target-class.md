---
title: "invalid_link_target 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_link_target"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_link_target 類別"
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_link_target 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`link_target`傳訊區塊的方法稱為和傳訊區塊不能連結至目標。  這可能是因為超過允許傳訊區塊的連結數目，或是嘗試連結兩次以相同的來源的特定目標。  
  
## 語法  
  
```  
class invalid_link_target : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_link\_target::invalid\_link\_target 建構函式](../Topic/invalid_link_target::invalid_link_target%20Constructor.md)|多載。  建構 `invalid_link_target` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_link_target`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)