---
title: "packaged_task 類別 | Microsoft Docs"
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
  - "future/std::packaged_task"
dev_langs: 
  - "C++"
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# packaged_task 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述是呼叫包裝函式呼叫簽章是 `Ty(ArgTypes...)`的非同步 *提供者* 。  除了動畫想結果之外，其相關聯 *的非同步狀態* 保存它可呼叫的物件複本。  
  
## 語法  
  
```  
template<class>  
class packaged_task;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[packaged\_task::packaged\_task 建構函式](../Topic/packaged_task::packaged_task%20Constructor.md)|建構 `packaged_task` 物件。|  
|[packaged\_task::~packaged\_task 解構函式](../Topic/packaged_task::~packaged_task%20Destructor.md)|終結 `packaged_task` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[packaged\_task::get\_future 方法](../Topic/packaged_task::get_future%20Method.md)|傳回具有相同相關聯的非同步狀態的 [未來](../standard-library/future-class.md) 物件。|  
|[packaged\_task::make\_ready\_at\_thread\_exit 方法](../Topic/packaged_task::make_ready_at_thread_exit%20Method.md)|呼叫這個關聯的非同步狀態儲存於可呼叫的物件並且完整儲存傳回的值。|  
|[packaged\_task::reset 方法](../Topic/packaged_task::reset%20Method.md)|取代這個關聯的非同步狀態。|  
|[packaged\_task::swap 方法](../Topic/packaged_task::swap%20Method.md)|交換這個關聯的非同步狀態與指定的物件。|  
|[packaged\_task::valid 方法](../Topic/packaged_task::valid%20Method.md)|指定物件是否有相關聯的非同步狀態。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[packaged\_task::operator\= 運算子](../Topic/packaged_task::operator=%20Operator.md)|從指定的物件將有相關聯的非同步狀態。|  
|[packaged\_task::operator\(\) 運算子](../Topic/packaged_task::operator\(\)%20Operator.md)|呼叫這個關聯的非同步狀態儲存於可呼叫的物件，不儲存傳回的值，並將這個狀態 *準備*。|  
|[packaged\_task::operator bool 運算子](../Topic/packaged_task::operator%20bool%20Operator.md)|指定物件是否有相關聯的非同步狀態。|  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)