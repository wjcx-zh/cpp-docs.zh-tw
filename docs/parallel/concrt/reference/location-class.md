---
title: "location 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::location"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "location 類別"
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# location 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

一個硬體的抽象實體位置。  
  
## 語法  
  
```  
class location;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[location::location 建構函式](../Topic/location::location%20Constructor.md)|多載。  建構 `location` 物件。|  
|[location::~location 解構函式](../Topic/location::~location%20Destructor.md)|終結 `location` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[location::current 方法](../Topic/location::current%20Method.md)|傳回表示呼叫執行緒執行的最特定的位置的 `location` 物件。|  
|[location::from\_numa\_node 方法](../Topic/location::from_numa_node%20Method.md)|傳回`location` 物件也就是表示指定 NUMA 的節點。|  
  
### 公用運算子  
  
|名稱|說明|  
|--------|--------|  
|[location::operator\!\= 運算子](../Topic/location::operator!=%20Operator.md)|判斷兩個 `location` 物件是否表示不同的位置。|  
|[location::operator\= 運算子](../Topic/location::operator=%20Operator.md)|將不同的 `location` 物件的內容指派給這一個。|  
|[location::operator\=\= 運算子](../Topic/location::operator==%20Operator.md)|判斷兩個 `location` 物件是否代表相同的位置。|  
  
## 繼承階層  
 `location`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)