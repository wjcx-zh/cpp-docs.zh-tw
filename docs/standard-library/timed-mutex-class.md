---
title: "timed_mutex 類別 | Microsoft Docs"
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
  - "mutex/std::timed_mutex"
dev_langs: 
  - "C++"
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# timed_mutex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表一個 *時間的型別*。  這個型別物件用來逐一查看程式中定期有限的封鎖強制執行互斥。  
  
## 語法  
  
```  
class timed_mutex;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[timed\_mutex::timed\_mutex 建構函式](../Topic/timed_mutex::timed_mutex%20Constructor.md)|建構未鎖定的 `timed_mutex` 物件。|  
|[timed\_mutex::~timed\_mutex 解構函式](../Topic/timed_mutex::~timed_mutex%20Destructor.md)|釋放 `timed_mutex` 物件所使用的所有資源。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[timed\_mutex::lock 方法](../Topic/timed_mutex::lock%20Method.md)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|  
|[timed\_mutex::try\_lock 方法](../Topic/timed_mutex::try_lock%20Method.md)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|  
|[timed\_mutex::try\_lock\_for 方法](../Topic/timed_mutex::try_lock_for%20Method.md)|嘗試取得 `mutex` 的擁有權指定的間隔時間。|  
|[timed\_mutex::try\_lock\_until 方法](../Topic/timed_mutex::try_lock_until%20Method.md)|嘗試取得 `mutex` 的擁有權直到指定的時間。|  
|[timed\_mutex::unlock 方法](../Topic/timed_mutex::unlock%20Method.md)|釋放 `mutex` 的擁有權。|  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)