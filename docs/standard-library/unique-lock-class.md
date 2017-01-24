---
title: "unique_lock 類別 | Microsoft Docs"
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
  - "mutex/std::unique_lock"
dev_langs: 
  - "C++"
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unique_lock 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示可以執行個體化建立物件處理鎖定和解除鎖定 `mutex`的範本。  
  
## 語法  
  
```  
template<class Mutex>  
class unique_lock;  
```  
  
## 備註  
 樣板引數 `Mutex` 必須命名 *為型別*。  
  
 在內部， `unique_lock` 存放指標相關聯的 `mutex` 物件和 `bool` 表示目前執行緒是否擁有 `mutex`。  
  
## 成員  
  
### 公用 Typedefs  
  
|Name|說明|  
|----------|--------|  
|`unique_lock::mutex_type`|樣板引數的 `Mutex`同義資料表。|  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[unique\_lock::unique\_lock 建構函式](../Topic/unique_lock::unique_lock%20Constructor.md)|建構 `unique_lock` 物件。|  
|[unique\_lock::~unique\_lock 解構函式](../Topic/unique_lock::~unique_lock%20Destructor.md)|釋放與 `unique_lock` 物件相關聯的所有資源。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[unique\_lock::lock 方法](../Topic/unique_lock::lock%20Method.md)|封鎖呼叫的執行緒，直到執行緒取得相關聯 `mutex`的擁有權。|  
|[unique\_lock::mutex 方法](../Topic/unique_lock::mutex%20Method.md)|擷取儲存於的指標相關聯的 `mutex`。|  
|[unique\_lock::owns\_lock 方法](../Topic/unique_lock::owns_lock%20Method.md)|指定呼叫執行緒是否擁有相關聯的 `mutex`。|  
|[unique\_lock::release 方法](../Topic/unique_lock::release%20Method.md)|解除關聯 `mutex` 物件的 `unique_lock` 物件。|  
|[unique\_lock::swap 方法](../Topic/unique_lock::swap%20Method.md)|交換相關聯的 `mutex` 和擁有權狀態與指定的物件。|  
|[unique\_lock::try\_lock 方法](../Topic/unique_lock::try_lock%20Method.md)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|  
|[unique\_lock::try\_lock\_for 方法](../Topic/unique_lock::try_lock_for%20Method.md)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|  
|[unique\_lock::try\_lock\_until 方法](../Topic/unique_lock::try_lock_until%20Method.md)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|  
|[unique\_lock::unlock 方法](../Topic/unique_lock::unlock%20Method.md)|釋放相關聯之 `mutex`的擁有權。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[unique\_lock::operator bool 運算子](../Topic/unique_lock::operator%20bool%20Operator.md)|指定呼叫執行緒是否有相關聯之 `mutex`的擁有權。|  
|[unique\_lock::operator\= 運算子](../Topic/unique_lock::operator=%20Operator.md)|複製儲存 `mutex` 指標和關聯的擁有權狀態從指定的物件。|  
  
## 繼承階層  
 `unique_lock`  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)