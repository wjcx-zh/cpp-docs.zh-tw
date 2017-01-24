---
title: "structured_task_group 類別 | Microsoft Docs"
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
  - "ppl/concurrency::structured_task_group"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "structured_task_group 類別"
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# structured_task_group 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`structured_task_group` 類別代表平行工作的高度結構化集合。  您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。  
  
## 語法  
  
```  
class structured_task_group;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[structured\_task\_group::structured\_task\_group 建構函式](../Topic/structured_task_group::structured_task_group%20Constructor.md)|多載。  建構新的 `structured_task_group` 物件。|  
|[structured\_task\_group::~structured\_task\_group 解構函式](../Topic/structured_task_group::~structured_task_group%20Destructor.md)|終結 `structured_task_group` 物件。  您應在解構函式執行前在物件上呼叫 `wait` 或  `run_and_wait` 方法，除非執行解構函式是因例外狀況而回溯堆疊的結果。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[structured\_task\_group::cancel 方法](../Topic/structured_task_group::cancel%20Method.md)|儘可能取消以此工作群組為根的工作之樹狀子目錄。  如果可能，會以可轉移方式取消工作群組中所有排定的工作。|  
|[structured\_task\_group::is\_canceling 方法](../Topic/structured_task_group::is_canceling%20Method.md)|會通知呼叫端目前是否正在取消工作群組。  這不一定表示在 `structured_task_group` 物件上呼叫 `cancel` 方法 \(雖然這樣一定可以讓此方法傳回 `true`\)。  可能是 `structured_task_group` 物件正以內嵌方式執行，而且已取消工作樹狀結構中的工作群組。  在這類的情況下，當執行階段可以預先判斷取消會流經這個 `structured_task_group` 物件時，也會傳回 `true`。|  
|[structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)|多載。  在 `structured_task_group` 物件上排程工作。  呼叫端會管理在 `_Task_handle`參數中傳遞之 `task_handle` 物件的存留期。  採用 `_Placement` 參數的版本會造成工作被偏移往執行該參數所指定的位置。|  
|[structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)|多載。  排程工作以內嵌方式執行於呼叫內容，並以 `structured_task_group` 物件協助支援完整的取消作業。  如果將 `task_handle` 物件做為參數傳遞到 `run_and_wait`，呼叫端會負責管理 `task_handle` 物件的存留期。  函式接著會等候直到 `structured_task_group` 物件上的所有工時已完成或取消。|  
|[structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)|等候直到 `structured_task_group` 的所有工作皆已完成或取消。|  
  
## 備註  
 為了達到效能，`structured_task_group` 物件的使用方式有許多嚴格的限制：  
  
-   單一 `structured_task_group` 物件不能由多個執行緒使用。  `structured_task_group` 物件上的所有作業必須由建立該物件的執行緒執行。  此規則的兩個例外狀況是成員函式 `cancel` 和 `is_canceling`。  物件不可在 Lambda 運算式的擷取清單中，也不可用於工作中，除非該工作使用其中一種取消作業。  
  
-   排定至 `structured_task_group` 物件的所有工作均是透過使用 `task_handle` 物件排定的，在此物件中，您必須明確地管理其存留期。  
  
-   多個群組只能用於絕對巢狀順序。  如果宣告兩個 `structured_task_group` 物件，必須在所有方法之前解構第二個宣告 \(內部的\) 物件，但必須在宣告第一個 \(外部的\) 物件時呼叫 `cancel` 或 `is_canceling` 方法。  無論只是在相同的或功能巢狀的範圍中宣告多個 `structured_task_group` 物件，或是轉換透過 `run` 或 `run_and_wait` 方法排入  `structured_task_group` 佇列的工作，這個條件都為 True。  
  
-   不同於一般 `task_group` 類別，`structured_task_group` 類別中的所有狀態都是最終的。  將工作排程至群組並等候工作完成之後，您就不能再使用同樣的群組。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 繼承階層  
 `structured_task_group`  
  
## 需求  
 **標頭：** ppl.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)   
 [task\_handle 類別](../../../parallel/concrt/reference/task-handle-class.md)