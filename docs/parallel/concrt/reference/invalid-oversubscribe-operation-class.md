---
title: "invalid_oversubscribe_operation 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_oversubscribe_operation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_oversubscribe_operation 類別"
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: 19
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_oversubscribe_operation 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`Context::Oversubscribe`方法以呼叫`_BeginOversubscription`參數設為`false`沒有先前的呼叫`Context::Oversubscribe`具有方法`_BeginOversubscription`參數設為`true`。  
  
## 語法  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_oversubscribe\_operation::invalid\_oversubscribe\_operation 建構函式](../Topic/invalid_oversubscribe_operation::invalid_oversubscribe_operation%20Constructor.md)|多載。  建構 `invalid_oversubscribe_operation` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)