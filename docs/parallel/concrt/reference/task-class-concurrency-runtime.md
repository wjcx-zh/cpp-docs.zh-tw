---
title: "task 類別 (並行執行階段) | Microsoft Docs"
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
  - "ppltasks/concurrency::task"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task 類別"
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task 類別 (並行執行階段)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

平行模式程式庫 \(PPL\) `task` 類別。  `task` 物件代表可以非同步執行的工作，這項工作還可以和其他工作以及並行執行階段之平行演算法所產生的平行工作同時執行。  它會在成功完成時產生屬於類型 `_ResultType` 的結果。  `task<void>` 類型的工作並不會產生結果。  您可以等候或取消工作，而不需考慮其他工作。  它也可以使用接續 \(`then`\)、聯結 \(`when_all`\) 和選項 \(`when_any`\) 模式搭配其他工作來組成。  
  
## 語法  
  
```  
template <  
   typename _Type  
>  
class task;  
  
template <>  
class task<void>;  
  
template<  
   typename _ReturnType  
>  
class task;  
```  
  
#### 參數  
 `_Type`  
 `T`  
 `_ReturnType`  
 此工作的結果類型。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`result_type`|這個類別的物件所產生結果的類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[task::task 建構函式](../Topic/task::task%20Constructor.md)|多載。  建構 `task` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[task::get 方法](../Topic/task::get%20Method.md)|多載。  傳回這個工作產生的結果。  如果工作不在終止狀態，則呼叫 `get` 將會等候工作完成。  在 `result_type` 為 `void` 的工作上被呼叫時，這個方法不會傳回值。|  
|[task::is\_apartment\_aware 方法](../Topic/task::is_apartment_aware%20Method.md)|判斷工作是將 Windows 執行階段 `IAsyncInfo` 介面解除包裝，還是從這類工作繼承而來。|  
|[task::is\_done 方法 \(並行執行階段\)](../Topic/task::is_done%20Method%20\(Concurrency%20Runtime\).md)|判斷工作是否已完成。|  
|[task::scheduler 方法 \(並行執行階段\)](../Topic/task::scheduler%20Method%20\(Concurrency%20Runtime\).md)|傳回這個工作的排程器。|  
|[task::then 方法](../Topic/task::then%20Method.md)|多載。  將接續工作加入至工作。|  
|[task::wait 方法](../Topic/task::wait%20Method.md)|等候這個工作到達終止狀態。  如果符合所有的工作相依性，而且未經選取供背景工作執行，則 `wait` 可以執行內嵌工作。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[task::operator\!\= 運算子](../Topic/task::operator!=%20Operator.md)|多載。  判斷兩個 `task` 物件是否表示不同的內部工作。|  
|[task::operator\= 運算子](../Topic/task::operator=%20Operator.md)|多載。  將某個 `task` 物件的內容取代為另一個物件的內容。|  
|[task::operator\=\= 運算子](../Topic/task::operator==%20Operator.md)|多載。  判斷兩個 `task` 物件是否表示相同的內部工作。|  
  
## 備註  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 繼承階層架構  
 `task`  
  
## 需求  
 **標頭：**ppltasks.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)