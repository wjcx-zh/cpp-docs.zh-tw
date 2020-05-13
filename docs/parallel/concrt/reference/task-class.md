---
title: task 類別 (並行執行階段)
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358727"
---
# <a name="task-class-concurrency-runtime"></a>task 類別 (並行執行階段)

平行模式程式庫 (PPL) `task` 類別。 物件`task`表示可以非同步執行的工作,並與其他併發運行時中的並行演演演算法生成的並行工作同時執行。 成功完成時，會產生 `_ResultType` 類型的結果。 `task<void>` 類型的工作不會產生任何結果。 工作可以獨立於其他工作，個別等候及取消。 它還可以使用延續()和聯接()`then``when_all`和選擇()`when_any`模式與其他任務組成。 當工作物件分配給新變數時,行為是 。 `std::shared_ptr`換句話說,兩個物件表示相同的基礎任務。

## <a name="syntax"></a>語法

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>參數

*_ResultType*<br/>
任務生成的結果的類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`result_type`|此類別物件所產生的結果類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[工作](#ctor)|已多載。 建構 `task` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|已多載。 傳回這個工作產生的結果。 如果工作不在終止狀態，則呼叫 `get` 將會等候工作完成。 在 `result_type` 為 `void` 的工作上被呼叫時，這個方法不會傳回值。|
|[is_apartment_aware](#is_apartment_aware)|判斷工作是否解除包裝 Windows 執行階段 `IAsyncInfo` 介面或是從這類工作繼承而來。|
|[is_done](#is_done)|判定工作是否完成。|
|[調度](#scheduler)|傳回此工作的排程器|
|[然後在受影響的網域控制站上執行](#then)|已多載。 將接續工作加入至此工作。|
|[等](#wait)|等候這個工作到達終止狀態。 如果符合所有的工作相依性，而且未經選取供背景工作執行，則 `wait` 可以執行內嵌工作。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[操作員!](#operator_neq)|已多載。 判斷兩個 `task` 物件是否表示不同的內部工作。|
|[運算子*](#operator_eq)|已多載。 將某個 `task` 物件的內容取代為另一個物件的內容。|
|[運算子*](#operator_eq_eq)|已多載。 判斷兩個 `task` 物件是否表示相同的內部工作。|

## <a name="remarks"></a>備註

有關詳細資訊,請參閱[工作並行性](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`task`

## <a name="requirements"></a>需求

**標題:** ppltasks.h

**命名空間:** 併發

## <a name="get"></a><a name="get"></a>抓取

傳回這個工作產生的結果。 如果工作不在終止狀態，則呼叫 `get` 將會等候工作完成。 在 `result_type` 為 `void` 的工作上被呼叫時，這個方法不會傳回值。

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>傳回值

工作的結果。

### <a name="remarks"></a>備註

如果任務被取消,則調用`get`將引發[task_canceled](task-canceled-class.md)異常。 如果工作發生不同的例外狀況，或例外狀況從前項工作傳播至它，則呼叫 `get` 將會擲回該例外狀況。

> [!IMPORTANT]
> 在通用 Windows 平臺 (UWP) 應用中,不要在使用者介面線程上運行的代碼中調用[併發:任務::等待](#wait)或`get`(`wait`呼叫)。 `get` 否則,運行時將引發[併發::invalid_operation](invalid-operation-class.md)因為這些方法會阻止當前線程,並可能導致應用變得無回應。 但是,`get`您可以調用 方法以在基於任務的延續中接收前任務的結果,因為結果立即可用。

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

判斷工作是否解除包裝 Windows 執行階段 `IAsyncInfo` 介面或是從這類工作繼承而來。

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>傳回值

**如果**任務解`IAsyncInfo`包 介面或是此類任務的後裔,則為**true,否則為 false。**

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>任務::is_done方法(併發運行時)

判定工作是否完成。

```cpp
bool is_done() const;
```

### <a name="return-value"></a>傳回值

如果任務已完成,則為 True,否則為 false。

### <a name="remarks"></a>備註

如果任務已完成或取消(無論是否有用戶異常),則函數將返回 true。

## <a name="operator"></a><a name="operator_neq"></a>操作員!

判斷兩個 `task` 物件是否表示不同的內部工作。

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的任務。

### <a name="return-value"></a>傳回值

如果物件引用不同的基礎任務,**則為 true,** 否則**為 false。**

## <a name="operator"></a><a name="operator_eq"></a>運算子*

將某個 `task` 物件的內容取代為另一個物件的內容。

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
來源 `task` 物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

由於 `task` 的表現就像智慧型指標，因此在複製指派之後，這個 `task` 物件和 `_Other` 一樣，都表示相同的實際工作。

## <a name="operator"></a><a name="operator_eq_eq"></a>運算子*

判斷兩個 `task` 物件是否表示相同的內部工作。

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的任務。

### <a name="return-value"></a>傳回值

如果物件引用同一基礎任務,**則為 true,** 否則**為 false。**

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>工作::調度程式方法(併發運行時)

傳回此工作的排程器

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>傳回值

指向計畫程式的指標

## <a name="task"></a><a name="ctor"></a> 工作

建構 `task` 物件。

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>參數

*T*<br/>
從中要建構工作的參數的類型。

*_Param*<br/>
從中要建構工作的參數。 這可能是 lambda、函數物件`task_completion_event<result_type>`、 物件或 Windows:基礎:::IAsyncInfo,如果您正在 Windows 運行時應用中使用任務。 lambda 或函數物件應與 等效`std::function<X(void)>`的類型 ,其中 X`result_type`可以是`task<result_type>`類型的 變數 , 或 Windows::基礎::IAsyncInfo 在 Windows 運行時應用中。

*_TaskOptions*<br/>
工作選項包括取消語彙基元、排程器等等

*_Other*<br/>
來源 `task` 物件。

### <a name="remarks"></a>備註

出現 `task` 的預設建構函式，只是為了讓工作在容器內使用。 只有在指派有效的工作給預設建構的工作之後，您才能使用它。 方法,如`get``wait``then`, 或將在調用預設構造的任務時引發[invalid_argument](../../../standard-library/invalid-argument-class.md)異常。

從 `task_completion_event` 建立的工作，會在設定工作完成事件後完成 (並排定其接續作業)。

接受取消語彙基元的建構函式版本，會建立可以透過使用 `cancellation_token_source` (語彙基元取得來源) 取消的工作。 在沒有取消語彙基元的情況下建立的工作，無法取消。

從 `Windows::Foundation::IAsyncInfo` 介面或從傳回 `IAsyncInfo` 介面的 Lambda 建立的工作，當內含的 Windows 執行階段非同步作業或動作完成時，該工作會到達其終止狀態。 同樣,從 lambda 創建的任務`task<result_type>`,當 內部任務到達其終端狀態時返回到達其終端狀態,而不是當 lambda 返回時返回其終端狀態。

`task` 的行為就像智慧型指標，可透過傳值方式安全傳遞。 它可以由多個執行緒存取，而不需要鎖定。

採用 Windows::基礎::iAsyncInfo 介面或返回此類介面的 lambda 的構造函數重載僅適用於 Windows 運行時應用。

有關詳細資訊,請參閱[工作並行性](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="then"></a><a name="then"></a>然後

將接續工作加入至此工作。

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>參數

*_Function*<br/>
此工作會叫用的函式物件的類型。

*_Func*<br/>
當這個工作完成時執行的接續函式。 這個接續函式必須接受 `result_type` 或 `task<result_type>` 的變數做為輸入，其中 `result_type` 是這個工作所產生結果的類型。

*_TaskOptions*<br/>
工作選項包括取消語彙基元、排程器和接續內容。 前 3 個選項預設會從前項工作繼承

*_CancellationToken*<br/>
要與接續工作產生關聯的取消語彙基元。 所建立不含取消語彙基元的接續工作將會繼承其前項工作的語彙基元。

*_ContinuationContext*<br/>
指定執行接續作業位置的變數。 此變數僅在UWP應用中使用時有用。 有關詳細資訊,請參閱[task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>傳回值

新建立的接續工作。 所傳回工作的結果類型取決於 `_Func` 傳回哪些項目。

### <a name="remarks"></a>備註

重載`then`的 lambda 或 functor 返回 Windows::基礎::iAsyncInfo 介面,僅適用於 Windows 運行時應用。

有關如何使用任務延續來撰寫非同步工作的詳細資訊,請參閱[工作並行性](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="wait"></a><a name="wait"></a>等

等候這個工作到達終止狀態。 如果符合所有的工作相依性，而且未經選取供背景工作執行，則 `wait` 可以執行內嵌工作。

```cpp
task_status wait() const;
```

### <a name="return-value"></a>傳回值

可能是 `task_status` 或 `completed` 的 `canceled` 值。 如果工作在執行時發生例外狀況，或例外狀況從前項工作傳播至它，則 `wait` 將會擲回該例外狀況。

### <a name="remarks"></a>備註

> [!IMPORTANT]
> 在通用 Windows 平臺 (UWP)`wait`應用中, 不要呼叫在使用者介面線程上運行的代碼。 否則，因為這個方法會封鎖目前的執行緒，而且可能會導致應用程式沒有回應，所以執行階段會擲回 [concurrency::invalid_operation](invalid-operation-class.md) 。 不過，您可以呼叫 [concurrency::task::get](#get) 方法來以工作為基礎連續的形式接收前項工作的結果。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
