---
title: task_handle 類別
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142547"
---
# <a name="task_handle-class"></a>task_handle 類別

`task_handle` 類別代表個別的平行工作項目。 它會封裝執行工作所需的指示和資料。

## <a name="syntax"></a>語法

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的型別，將叫用此類型，以執行 `task_handle` 物件所表示的工作。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_handle](#task_handle)|建構新的 `task_handle` 物件。 工作的執行方式是將指定為參數的函式叫用至此函式。|
|[~ task_handle 的析構函式](#dtor)|終結 `task_handle` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|執行時間所叫用的函式呼叫運算子，用來執行工作控制碼。|

## <a name="remarks"></a>備註

`task_handle` 物件可以與 `structured_task_group` 或較通用的 `task_group` 物件搭配使用，以將工作分解成平行作業。 如需詳細資訊，請參閱工作[平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

請注意，`task_handle` 物件的建立者會負責維護所建立 `task_handle` 物件的存留期，直到並行執行階段不再需要它為止。 一般來說，這表示 `task_handle` 物件必須等到其已排入佇列的 `task_group` 或 `structured_task_group` 的 `wait` 或 `run_and_wait` 方法被呼叫之後，才可以進行析構。

`task_handle` 物件通常會與C++ lambda 搭配使用。 因為您不知道 lambda 的真正類型，所以[make_task](concurrency-namespace-functions.md#make_task)函數通常用來建立 `task_handle` 物件。

執行時間會建立您傳遞至 `task_handle` 物件的工作函式複本。 因此，您傳遞至 `task_handle` 物件之函式物件中發生的任何狀態變更，都不會出現在該函式物件的複本中。

## <a name="inheritance-hierarchy"></a>繼承階層

`task_handle`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** concurrency

## <a name="task_handle__operator_call"></a>operator （）

執行時間所叫用的函式呼叫運算子，用來執行工作控制碼。

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

建構新的 `task_handle` 物件。 工作的執行方式是將指定為參數的函式叫用至此函式。

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>參數

*_Func*<br/>
將叫用以執行 `task_handle` 物件所代表之工作的函式。 這可能是 lambda 仿函數、函式的指標，或是支援具有簽章 `void operator()()`之函式呼叫運算子版本的任何物件。

### <a name="remarks"></a>備註

執行時間會建立您傳遞至此函式的工作函式複本。 因此，您傳遞至 `task_handle` 物件之函式物件中發生的任何狀態變更，都不會出現在該函式物件的複本中。

## <a name="dtor"></a>~ task_handle

終結 `task_handle` 物件。

```cpp
~task_handle();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)
