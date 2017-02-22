---
title: "task_handle 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::task_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_handle 類別"
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# task_handle 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_handle` 類別代表個別的平行工作項目。  它會封裝執行工作所需的指示和資料。  
  
## 語法  
  
```  
template<  
   typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### 參數  
 `_Function`  
 欲叫用以執行`task_handle`物件代表之工作的函式物件的類型。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[task\_handle::task\_handle 建構函式](../Topic/task_handle::task_handle%20Constructor.md)|建構新的 `task_handle` 物件。  工作的工作是透過教用建構函式當作參數的函式來執行的。|  
|[task\_handle::~task\_handle 解構函式](../Topic/task_handle::~task_handle%20Destructor.md)|終結 `task_handle` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[task\_handle::operator\(\) 運算子](../Topic/task_handle::operator\(\)%20Operator.md)|函式會呼叫運算子，執行階段會叫用此運算子來執行工作控制代碼的工作。|  
  
## 備註  
 `task_handle` 物件可用來配合 `structured_task_group` 或更一般的 `task_group` 物件，將工作分解成平行的工作。  如需詳細資訊，請參閱 [工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 請注意，`task_handle` 物件的建立者負責維護所建立之 `task_handle` 物件的存留期，直到不再並行執行階段不再需要此物件。  通常，這表示 `task_handle` 物件不能解構，直到呼叫該物件佇列之 `task_group` 或 `structured_task_group` 的 `wait`或`run_and_wait`方法為止。  
  
 `task_handle` 物件通常會與 C \+ \+ Lambdas 一起使用。  因為不知道 Lambda 的真正型別，因此 [make\_task](../Topic/make_task%20Function.md) 函式通常用來建立 `task_handle` 物件。  
  
 執行階段會建立傳遞給 `task_handle` 物件的工作函式複本。  因此，在您傳遞給 `task_handle` 物件之函式物件中發生的任何狀態變更都不會在該函式物件的複本中出現。  
  
## 繼承階層架構  
 `task_handle`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)   
 [structured\_task\_group 類別](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [make\_task 函式](../Topic/make_task%20Function.md)   
 [task\_group::run 方法](../Topic/task_group::run%20Method.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)