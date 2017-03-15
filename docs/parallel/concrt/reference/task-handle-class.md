---
title: "task_handle 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::task_handle
dev_langs:
- C++
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b113cf519f4326650dc1ed4d20dd2ed00921eda9
ms.lasthandoff: 02/24/2017

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
 將要叫用以執行該工作所表示的函式物件型別`task_handle`物件。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[task_handle 建構函式](#ctor)|建構新`task_handle`物件。 藉由叫用指定做為參數的建構函式的函式執行工作的工作。|  
|[~ task_handle 解構函式](#dtor)|終結`task_handle`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator （) 運算子](#task_handle__operator_call)|執行階段會叫用來執行的工作控制代碼的工作函式呼叫運算子。|  
  
## <a name="remarks"></a>備註  
 `task_handle`物件可以用於搭配`structured_task_group`或多個一般`task_group`物件，用來將工作分解成平行工作。 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 請注意，建立者`task_handle`物件負責維護所建立的存留期`task_handle`物件，直到它已不再需要由並行執行階段。 通常，這表示`task_handle`物件必須不解構直到`wait`或`run_and_wait`方法`task_group`或`structured_task_group`呼叫的佇列。  
  
 `task_handle`物件通常用於搭配 c + + lambda。 因為您不知道真正的 lambda 類型[make_task](concurrency-namespace-functions.md#make_task)函式通常用來建立`task_handle`物件。  
  
 執行階段會建立一份工作函式傳遞至`task_handle`物件。 因此，任何狀態變更發生在函數中的物件將傳遞至`task_handle`物件將不會顯示該函式物件的複本中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_handle`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-nametaskhandleoperatorcalla-operator"></a><a name="task_handle__operator_call"></a>operator （) 

 執行階段會叫用來執行的工作控制代碼的工作函式呼叫運算子。  
  
```  
void operator()() const;

 
```  
  
##  <a name="a-nametaskhandlectora-taskhandle"></a><a name="task_handle__ctor"></a>task_handle 

 建構新`task_handle`物件。 藉由叫用指定做為參數的建構函式的函式執行工作的工作。  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>參數  
 `_Func`  
 將要叫用以執行該工作所表示的函式`task_handle`物件。 這可能是 lambda 仿函式，函式指標，或任何物件支援的版本與簽章的函式呼叫運算子`void operator()()`。  
  
### <a name="remarks"></a>備註  
 執行階段會建立一份工作函式傳遞至建構函式。 因此，任何狀態變更發生在函數中的物件將傳遞至`task_handle`物件將不會顯示該函式物件的複本中。  
  
##  <a name="a-namedtora-taskhandle"></a><a name="dtor"></a>~ task_handle 

 終結`task_handle`物件。  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_group 類別](task-group-class.md)   
 [structured_task_group 類別](structured-task-group-class.md)

