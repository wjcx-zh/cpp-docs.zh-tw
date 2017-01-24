---
title: "future 類別 | Microsoft Docs"
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
  - "future/std::future"
dev_langs: 
  - "C++"
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# future 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述非同步 *傳回物件*。  
  
## 語法  
  
```  
template<class Ty>  
class future;  
```  
  
## 備註  
 每個標準 *非同步提供者* 傳回型別為範本具現化的物件。  `future` 物件提供對非同步提供者的唯一存取關聯。  如果您需要與同一個非同步提供者的多個非同步傳回物件，複製至 [shared\_future](../standard-library/shared-future-class.md) 物件的 `future` 物件。  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[future::future 建構函式](../Topic/future::future%20Constructor.md)|建構 `future` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[future::get 方法](../Topic/future::get%20Method.md)|擷取與這個相關聯的非同步狀態儲存在本機的結果。|  
|[future::share 方法](../Topic/future::share%20Method.md)|轉換的 `shared_future`物件。|  
|[future::valid 方法](../Topic/future::valid%20Method.md)|指定物件是否不是空的。|  
|[future::wait 方法](../Topic/future::wait%20Method.md)|封鎖目前的執行緒，直到此關聯的非同步狀態為就緒。|  
|[future::wait\_for 方法](../Topic/future::wait_for%20Method.md)|在這個關聯的非同步狀態的區塊準備好或在指定的時間長度已經過去。|  
|[future::wait\_until 方法](../Topic/future::wait_until%20Method.md)|在這個關聯的非同步狀態的區塊準備好或在指定的時間點。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[future::operator\= 運算子](../Topic/future::operator=%20Operator.md)|從指定的物件傳送這個關聯的非同步狀態。|  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)