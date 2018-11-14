---
title: task_handle 類別
ms.date: 11/04/2016
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: 060be8614fc3a0a93d446c747b65de82b863ab3c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518875"
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

*_Function*<br/>
將會叫用來執行工作所代表的函式物件的型別`task_handle`物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_handle](#ctor)|建構新`task_handle`物件。 工作的工作是由叫用做為建構函式的參數所指定的函式執行。|
|[~ task_handle 解構函式](#dtor)|終結`task_handle`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|若要執行的工作控制代碼的工作的執行階段叫用函式呼叫運算子。|

## <a name="remarks"></a>備註

`task_handle` 物件可以用於搭配`structured_task_group`或更多一般`task_group`物件，要將工作分解成平行工作。 如需詳細資訊，請參閱 <<c0> [ 工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

請注意，建立者`task_handle`物件會負責維護所建立的存留期`task_handle`物件，直到它不再需要之並行執行階段。 通常，這表示`task_handle`物件必須未解構直到`wait`或`run_and_wait`方法`task_group`或`structured_task_group`呼叫的佇列。

`task_handle` 物件通常用於搭配使用 c + + lambda。 因為您不知道的 lambda，則為 true 的型別[make_task](concurrency-namespace-functions.md#make_task)函式通常用來建立`task_handle`物件。

執行階段會建立一份工作函式傳遞至`task_handle`物件。 因此，函式中發生的任何狀態變更的物件，您將傳遞給`task_handle`物件不會出現在您的函式物件的複本。

## <a name="inheritance-hierarchy"></a>繼承階層

`task_handle`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="task_handle__operator_call"></a> operator （)

若要執行的工作控制代碼的工作的執行階段叫用函式呼叫運算子。

```
void operator()() const;
```

##  <a name="task_handle__ctor"></a> task_handle

建構新`task_handle`物件。 工作的工作是由叫用做為建構函式的參數所指定的函式執行。

```
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>參數

*_Func*<br/>
將會叫用來執行工作所代表的函式`task_handle`物件。 這可能是 lambda 函式，函式的指標，或是任何物件，可支援版本與簽章的函式呼叫運算子`void operator()()`。

### <a name="remarks"></a>備註

執行階段會建立一份您傳遞給建構函式的工作函式。 因此，函式中發生的任何狀態變更的物件，您將傳遞給`task_handle`物件不會出現在您的函式物件的複本。

##  <a name="dtor"></a> ~ task_handle

終結`task_handle`物件。

```
~task_handle();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)
