---
title: "lock_guard 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::lock_guard"
dev_langs: 
  - "C++"
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# lock_guard 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示可以執行個體化建立物件解構函式開啟 `mutex`的範本。  
  
## 語法  
  
```  
template<class Mutex>  
class lock_guard;  
```  
  
## 備註  
 樣板引數 `Mutex` 必須命名 *為型別*。  
  
## 成員  
  
### 公用 Typedefs  
  
|Name|說明|  
|----------|--------|  
|`lock_guard::mutex_type`|樣板引數的 `Mutex`同義資料表。|  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[lock\_guard::lock\_guard 建構函式](../Topic/lock_guard::lock_guard%20Constructor.md)|建構 `lock_guard` 物件。|  
|[lock\_guard::~lock\_guard 解構函式](../Topic/lock_guard::~lock_guard%20Destructor.md)|開啟傳遞至建構函式的 `mutex` 。|  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)