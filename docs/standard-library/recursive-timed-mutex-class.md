---
title: "recursive_timed_mutex 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::recursive_timed_mutex"
dev_langs: 
  - "C++"
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# recursive_timed_mutex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表一個 *時間的型別*。  您可以在程式中，的時間限制的封鎖型別物件用來強制執行互斥。  不同於型別 [timed\_mutex](../standard-library/timed-mutex-class.md)物件，呼叫 `recursive_timed_mutex` 物件的鎖定方法的作用是妥善定義的。  
  
## 語法  
  
```  
class recursive_timed_mutex;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[recursive\_timed\_mutex::recursive\_timed\_mutex 建構函式](../Topic/recursive_timed_mutex::recursive_timed_mutex%20Constructor.md)|建構未鎖定的 `recursive_timed_mutex` 物件。|  
|[recursive\_timed\_mutex::~recursive\_timed\_mutex 解構函式](../Topic/recursive_timed_mutex::~recursive_timed_mutex%20Destructor.md)|釋放 `recursive_timed_mutex` 物件所使用的所有資源。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[recursive\_timed\_mutex::lock 方法](../Topic/recursive_timed_mutex::lock%20Method.md)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|  
|[recursive\_timed\_mutex::try\_lock 方法](../Topic/recursive_timed_mutex::try_lock%20Method.md)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|  
|[recursive\_timed\_mutex::try\_lock\_for 方法](../Topic/recursive_timed_mutex::try_lock_for%20Method.md)|嘗試取得 `mutex` 的擁有權指定的間隔時間。|  
|[recursive\_timed\_mutex::try\_lock\_until 方法](../Topic/recursive_timed_mutex::try_lock_until%20Method.md)|嘗試取得 `mutex` 的擁有權直到指定的時間。|  
|[recursive\_timed\_mutex::unlock 方法](../Topic/recursive_timed_mutex::unlock%20Method.md)|釋放 `mutex` 的擁有權。|  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)