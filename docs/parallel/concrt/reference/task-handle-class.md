---
title: task_handle 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs:
- C++
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fa72ed19a691015214fe263033e07f8d6a74c34
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="taskhandle-class"></a>task_handle 類別
`task_handle` 類別代表個別的平行工作項目。 它會封裝執行工作所需的指示和資料。  
  
## <a name="syntax"></a>語法  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用以執行該工作所表示的函式物件類型`task_handle`物件。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[task_handle](#ctor)|建構新`task_handle`物件。 工作的工作會執行叫用指定做為參數的建構函式的函式。|  
|[~ task_handle 解構函式](#dtor)|終結`task_handle`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator()](#task_handle__operator_call)|執行階段會叫用來執行的工作控制代碼的工作函式呼叫運算子。|  
  
## <a name="remarks"></a>備註  
 `task_handle` 物件可以用於搭配`structured_task_group`或多個一般`task_group`物件，將工作分解成平行工作。 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 請注意，建立者`task_handle`物件都負責維護的存留期建立`task_handle`物件，直到它已不再需要之並行執行階段。 通常，這表示`task_handle`物件必須不解構直到`wait`或`run_and_wait`方法`task_group`或`structured_task_group`的佇列已呼叫。  
  
 `task_handle` 物件通常用於搭配 c + + lambda。 因為您不知道的 lambda，則為 true 的型別[make_task](concurrency-namespace-functions.md#make_task)函式通常用來建立`task_handle`物件。  
  
 執行階段建立一份工作函式傳遞給`task_handle`物件。 因此，任何狀態變更發生在函數中的物件將傳遞至`task_handle`物件不會出現在您的函式物件的複本。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_handle`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="task_handle__operator_call"></a> operator （) 

 執行階段會叫用來執行的工作控制代碼的工作函式呼叫運算子。  
  
```  
void operator()() const;

 
```  
  
##  <a name="task_handle__ctor"></a> task_handle 

 建構新`task_handle`物件。 工作的工作會執行叫用指定做為參數的建構函式的函式。  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>參數  
 `_Func`  
 將要叫用以執行該工作所表示的函式`task_handle`物件。 這可能是 lambda 函式，函式指標，或任何物件的支援版本的函式呼叫運算子與簽章`void operator()()`。  
  
### <a name="remarks"></a>備註  
 執行階段建立一份您傳遞給建構函式的工作函式。 因此，任何狀態變更發生在函數中的物件將傳遞至`task_handle`物件不會出現在您的函式物件的複本。  
  
##  <a name="dtor"></a> ~ task_handle 

 終結`task_handle`物件。  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_group 類別](task-group-class.md)   
 [structured_task_group 類別](structured-task-group-class.md)
