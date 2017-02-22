---
title: "promise 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::promise"
dev_langs: 
  - "C++"
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# promise 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個*非同步提供者*。  
  
## 語法  
  
```  
template<class Ty>  
class promise;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[promise::promise 建構函式](../Topic/promise::promise%20Constructor.md)|建構 `promise` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[promise::get\_future 方法](../Topic/promise::get_future%20Method.md)|傳回 [future](../standard-library/future-class.md) 與這項承諾。|  
|[promise::set\_exception 方法](../Topic/promise::set_exception%20Method.md)|不設定這項承諾的結果會指出例外狀況。|  
|[promise::set\_exception\_at\_thread\_exit 方法](../Topic/promise::set_exception_at_thread_exit%20Method.md)|不設定這個承諾的結果會指出例外狀況，並只有在目前執行緒中所有執行緒區域物件已終結後 \(通常是在執行緒結束\) 提供告知。|  
|[promise::set\_value 方法](../Topic/promise::set_value%20Method.md)|不設定這項承諾的結果值。|  
|[promise::set\_value\_at\_thread\_exit 方法](../Topic/promise::set_value_at_thread_exit%20Method.md)|不設定這個承諾的結果會指出值，並只有在目前執行緒中所有執行緒區域物件已終結後 \(通常是在執行緒結束\) 提供告知。|  
|[promise::swap 方法](../Topic/promise::swap%20Method.md)|交換承諾的 *關聯的非同步狀態* 與指定的承諾物件。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[promise::operator\= 運算子](../Topic/promise::operator=%20Operator.md)|這個承諾物件共用狀態的工作。|  
  
## 繼承階層  
 `promise`  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)