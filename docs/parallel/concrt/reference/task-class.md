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
ms.openlocfilehash: e0f876b3c0971e70763f36622fb72a3dea671461
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682524"
---
# <a name="task-class-concurrency-runtime"></a>task 類別 (並行執行階段)

平行模式程式庫 (PPL) `task` 類別。 `task`物件代表可以在並行執行階段中以非同步方式和其他工作來執行, 以及平行演算法所產生的平行工作。 成功完成時，會產生 `_ResultType` 類型的結果。 `task<void>` 類型的工作不會產生任何結果。 工作可以獨立於其他工作，個別等候及取消。 也可以使用接續 ( `then`) 和 join ( `when_all`) 和 choice ( `when_any`) 模式, 與其他工作一起撰寫。 將 task 物件指派給新的變數時, 其行為會是`std::shared_ptr`; 換句話說, 這兩個物件都代表相同的基礎工作。

## <a name="syntax"></a>語法

```
template <>
class task<void>;

template<typename _ResultType>
class task;
```

#### <a name="parameters"></a>參數

*_ResultType*<br/>
工作產生的結果類型。 

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`result_type`|此類別物件所產生的結果類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task](#ctor)|多載。 建構 `task` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|多載。 傳回這個工作產生的結果。 如果工作不在終止狀態，則呼叫 `get` 將會等候工作完成。 在 `result_type` 為 `void` 的工作上被呼叫時，這個方法不會傳回值。|
|[is_apartment_aware](#is_apartment_aware)|判斷工作是否解除包裝 Windows 執行階段 `IAsyncInfo` 介面或是從這類工作繼承而來。|
|[is_done](#is_done)|判定工作是否完成。|
|[scheduler](#scheduler)|傳回此工作的排程器|
|[then](#then)|多載。 將接續工作加入至此工作。|
|[等候](#wait)|等候這個工作到達終止狀態。 如果符合所有的工作相依性，而且未經選取供背景工作執行，則 `wait` 可以執行內嵌工作。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|多載。 判斷兩個 `task` 物件是否表示不同的內部工作。|
|[operator=](#operator_eq)|多載。 將某個 `task` 物件的內容取代為另一個物件的內容。|
|[operator==](#operator_eq_eq)|多載。 判斷兩個 `task` 物件是否表示相同的內部工作。|

## <a name="remarks"></a>備註

如需詳細資訊, 請參閱工作[平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

## <a name="inheritance-hierarchy"></a>繼承階層

`task`

## <a name="requirements"></a>需求

**標頭:** ppltasks.h。h

**命名空間：** concurrency

##  <a name="get"></a>獲取

傳回這個工作產生的結果。 如果工作不在終止狀態，則呼叫 `get` 將會等候工作完成。 在 `result_type` 為 `void` 的工作上被呼叫時，這個方法不會傳回值。

```
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>傳回值

工作的結果。

### <a name="remarks"></a>備註

如果工作已取消, 呼叫`get`將會擲回[task_canceled](task-canceled-class.md)例外狀況。 如果工作發生不同的例外狀況，或例外狀況從前項工作傳播至它，則呼叫 `get` 將會擲回該例外狀況。

> [!IMPORTANT]
>  在通用 Windows 平臺 (UWP) 應用程式中, 請勿在使用者介面執行緒上執行的程式碼中呼叫`get` [concurrency:: task:: wait](#wait)或`get` ( `wait`呼叫)。 否則, 執行時間會擲回[concurrency:: invalid_operation](invalid-operation-class.md) , 因為這些方法會封鎖目前的執行緒, 而且可能會導致應用程式沒有回應。 不過, 您可以呼叫`get`方法, 在以工作為基礎的接續中接收 antecedent 工作的結果, 因為結果會立即可用。

##  <a name="is_apartment_aware"></a> is_apartment_aware

判斷工作是否解除包裝 Windows 執行階段 `IAsyncInfo` 介面或是從這類工作繼承而來。

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>傳回值

如果工作`IAsyncInfo`解除包裝介面或從這類工作繼承, 則**為 true** , 否則為**false** 。

##  <a name="is_done"></a>task:: is_done 方法 (並行執行階段)

判定工作是否完成。

```
bool is_done() const;
```

### <a name="return-value"></a>傳回值

如果工作已完成, 則為 True, 否則為 false。

### <a name="remarks"></a>備註

如果工作已完成或已取消 (不論使用者是否有例外狀況), 此函式會傳回 true。

##  <a name="operator_neq"></a>operator! =

判斷兩個 `task` 物件是否表示不同的內部工作。

```
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的工作。

### <a name="return-value"></a>傳回值

如果物件參考不同的基礎工作,**則為 true** , 否則為**false** 。

##  <a name="operator_eq"></a>operator =

將某個 `task` 物件的內容取代為另一個物件的內容。

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
來源 `task` 物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

由於 `task` 的表現就像智慧型指標，因此在複製指派之後，這個 `task` 物件和 `_Other` 一樣，都表示相同的實際工作。

##  <a name="operator_eq_eq"></a>operator = =

判斷兩個 `task` 物件是否表示相同的內部工作。

```
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的工作。

### <a name="return-value"></a>傳回值

如果物件參考相同的基礎工作,**則為 true** , 否則為**false** 。

##  <a name="scheduler"></a>task:: 排程器方法 (並行執行階段)

傳回此工作的排程器

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>傳回值

排程器的指標

##  <a name="ctor"></a>任務

建構 `task` 物件。

```
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
從中要建構工作的參數。 如果您在 Windows 執行階段應用程式中使用工作, 這`task_completion_event<result_type>`可能是 lambda、函式物件、物件或 Windows:: Foundation:: IAsyncInfo。 Lambda 或函式物件應該是相當於`std::function<X(void)>`的類型, 其中 X 可以是`task<result_type>`類型`result_type`的變數、或 Windows 執行階段應用程式中的 Windows:: Foundation:: IAsyncInfo。

*_TaskOptions*<br/>
工作選項包括取消語彙基元、排程器等等

*_Other*<br/>
來源 `task` 物件。

### <a name="remarks"></a>備註

出現 `task` 的預設建構函式，只是為了讓工作在容器內使用。 只有在指派有效的工作給預設建構的工作之後，您才能使用它。 在預設的已`wait`建立`then`工作上呼叫時,或等方法將會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外`get`狀況。

從 `task_completion_event` 建立的工作，會在設定工作完成事件後完成 (並排定其接續作業)。

接受取消語彙基元的建構函式版本，會建立可以透過使用 `cancellation_token_source` (語彙基元取得來源) 取消的工作。 在沒有取消語彙基元的情況下建立的工作，無法取消。

從 `Windows::Foundation::IAsyncInfo` 介面或從傳回 `IAsyncInfo` 介面的 Lambda 建立的工作，當內含的 Windows 執行階段非同步作業或動作完成時，該工作會到達其終止狀態。 同樣地，從傳回 `task<result_type>` 的 Lambda 建立的工作，會在內部工作到達終止狀態時，而不是在 Lambda 傳回時，到達其終止狀態。

`task` 的行為就像智慧型指標，可透過傳值方式安全傳遞。 它可以由多個執行緒存取，而不需要鎖定。

採用 Windows:: Foundation:: IAsyncInfo 介面或傳回這類介面之 lambda 的函式多載僅適用于 Windows 執行階段應用程式。

如需詳細資訊, 請參閱工作[平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

##  <a name="then"></a>請

將接續工作加入至此工作。

```
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
指定執行接續作業位置的變數。 這個變數只有在 UWP 應用程式中使用時才有用。 如需詳細資訊, 請參閱[task_continuation_coNtext](task-continuation-context-class.md)

### <a name="return-value"></a>傳回值

新建立的接續工作。 所傳回工作的結果類型取決於 `_Func` 傳回哪些項目。

### <a name="remarks"></a>備註

`then`採用 lambda 或仿函數 (會傳回 Windows:: Foundation:: IAsyncInfo 介面) 的多載僅適用于 Windows 執行階段應用程式。

如需如何使用工作接續撰寫非同步工作的詳細資訊, 請參閱工作[平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

##  <a name="wait"></a>等候

等候這個工作到達終止狀態。 如果符合所有的工作相依性，而且未經選取供背景工作執行，則 `wait` 可以執行內嵌工作。

```
task_status wait() const;
```

### <a name="return-value"></a>傳回值

可能是 `task_status` 或 `completed` 的 `canceled` 值。 如果工作在執行時發生例外狀況，或例外狀況從前項工作傳播至它，則 `wait` 將會擲回該例外狀況。

### <a name="remarks"></a>備註

> [!IMPORTANT]
>  在通用 Windows 平臺 (UWP) 應用程式中, 請勿呼叫`wait`在使用者介面執行緒上執行之程式碼中的。 否則，因為這個方法會封鎖目前的執行緒，而且可能會導致應用程式沒有回應，所以執行階段會擲回 [concurrency::invalid_operation](invalid-operation-class.md) 。 不過，您可以呼叫 [concurrency::task::get](#get) 方法來以工作為基礎連續的形式接收前項工作的結果。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
