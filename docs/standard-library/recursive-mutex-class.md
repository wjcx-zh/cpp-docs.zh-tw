---
title: "recursive_mutex 類別 | Microsoft Docs"
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
  - "mutex/std::recursive_mutex"
dev_langs: 
  - "C++"
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# recursive_mutex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 *mutex 型別*。  與 [mutex](../standard-library/mutex-class-stl.md)相反，呼叫行為對方法的鎖定已鎖定的物件都已妥善定義的。  
  
## 語法  
  
```  
class recursive_mutex;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[recursive\_mutex::recursive\_mutex 建構函式](../Topic/recursive_mutex::recursive_mutex%20Constructor.md)|建構 `recursive_mutex` 物件。|  
|[recursive\_mutex::~recursive\_mutex 解構函式](../Topic/recursive_mutex::~recursive_mutex%20Destructor.md)|釋放 `recursive_mutex` 物件所使用的所有資源。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[recursive\_mutex::lock 方法](../Topic/recursive_mutex::lock%20Method.md)|封鎖呼叫的執行緒，直到執行緒取得 Mutex 的擁有權。|  
|[recursive\_mutex::try\_lock 方法](../Topic/recursive_mutex::try_lock%20Method.md)|嘗試取得 Mutex 的擁有權，而不需封鎖。|  
|[recursive\_mutex::unlock 方法](../Topic/recursive_mutex::unlock%20Method.md)|釋放 Mutex 的擁有權。|  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)