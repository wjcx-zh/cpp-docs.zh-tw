---
title: "mutex 類別 (STL) | Microsoft Docs"
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
  - "mutex/std::mutex"
dev_langs: 
  - "C++"
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: 11
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mutex 類別 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 *mutex 型別*。  這個型別的物件可以用來強制程式內的互斥。  
  
## 語法  
  
```  
class mutex;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[mutex::mutex 建構函式 \(STL\)](../Topic/mutex::mutex%20Constructor%20\(STL\).md)|建構 `mutex` 物件。|  
|[mutex::~mutex 解構函式 \(STL\)](../Topic/mutex::~mutex%20Destructor%20\(STL\).md)|釋放 `mutex` 物件使用的所有資源。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[mutex::lock 方法 \(STL\)](../Topic/mutex::lock%20Method%20\(STL\).md)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|  
|[mutex::native\_handle 方法 \(STL\)](../Topic/mutex::native_handle%20Method%20\(STL\).md)|傳回表示 mutex 控制代碼的實作特定的型別。|  
|[mutex::try\_lock 方法 \(STL\)](../Topic/mutex::try_lock%20Method%20\(STL\).md)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|  
|[mutex::unlock 方法 \(STL\)](../Topic/mutex::unlock%20Method%20\(STL\).md)|釋放 `mutex` 的擁有權。|  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)