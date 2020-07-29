---
title: structured_task_group 類別
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 44fd2a42f4c98a569e985449f0c55102a9cbc3a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231672"
---
# <a name="structured_task_group-class"></a>structured_task_group 類別

`structured_task_group` 類別代表平行工作的高度結構化集合。 您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。

## <a name="syntax"></a>語法

```cpp
class structured_task_group;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[structured_task_group](#ctor)|已多載。 建構新的 `structured_task_group` 物件。|
|[~ structured_task_group 的析構函式](#dtor)|終結 `structured_task_group` 物件。 在 `wait` `run_and_wait` 執行析構函式之前，您應該在物件上呼叫或方法，除非因為發生例外狀況而導致因為堆疊回溯而執行的析構函數。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[cancel](#cancel)|盡全力嘗試取消根節點的子樹，而此工作群組為 root。 可能的話，在工作組上排程的每個工作都將被取消傳遞。|
|[is_canceling](#is_canceling)|通知呼叫者，工作群組目前是否在取消作業的過程中。 這不一定表示 `cancel` 已在物件上呼叫方法（不過，這種方法肯定會傳回 `structured_task_group` **`true`** ）。 在此情況下， `structured_task_group` 物件是以內嵌方式執行，而且已取消工作樹狀結構中的工作組。 在這類情況下，執行時間可以在這種情況下判斷取消將流經此 `structured_task_group` 物件的情況，也 **`true`** 會傳回。|
|[進行](#run)|已多載。 在物件上排定工作 `structured_task_group` 。 呼叫端會管理 `task_handle` 參數中傳遞之物件的存留期 `_Task_handle` 。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|
|[run_and_wait](#run_and_wait)|已多載。 使用物件的協助，將工作排程在呼叫內容上以內嵌方式執行，以 `structured_task_group` 提供完整的取消支援。 如果 `task_handle` 物件當做參數傳遞至 `run_and_wait` ，呼叫端會負責管理物件的存留期 `task_handle` 。 然後，函式會等到物件上的所有工作 `structured_task_group` 都已完成或已取消。|
|[等候](#wait)|等到上的所有工作 `structured_task_group` 都完成或取消為止。|

## <a name="remarks"></a>備註

使用物件時，有一些嚴重的限制是為了 `structured_task_group` 取得效能：

- 單一 `structured_task_group` 物件無法由多個執行緒使用。 物件上的所有作業都 `structured_task_group` 必須由建立物件的執行緒執行。 這項規則的兩個例外是成員函式 `cancel` 和 `is_canceling` 。 除非工作是使用其中一個取消作業，否則物件可能不會在 lambda 運算式的 capture 清單中，並且在工作中使用。

- 所有排程至物件的 `structured_task_group` 工作都是透過使用 `task_handle` 您必須明確管理其存留期的物件來排程。

- 多個群組只能以絕對的嵌套順序使用。 如果宣告了兩個 `structured_task_group` 物件，則第二個宣告的（內部）必須在 `cancel` `is_canceling` 第一個方法（外部）上呼叫或以外的任何方法之前，先進行析構。 這種情況在案例中，只要宣告 `structured_task_group` 相同或功能的嵌套範圍內的多個物件，以及透過或方法排入佇列至的工作案例，都適用 `structured_task_group` `run` `run_and_wait` 。

- 不同于一般 `task_group` 類別，類別中的所有狀態 `structured_task_group` 都是最終的。 您將工作佇列至群組並等候工作完成之後，就不能再使用同一個群組。

如需詳細資訊，請參閱工作[平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`structured_task_group`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** 並行

## <a name="cancel"></a><a name="cancel"></a>取消

盡全力嘗試取消根節點的子樹，而此工作群組為 root。 可能的話，在工作組上排程的每個工作都將被取消傳遞。

```cpp
void cancel();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

通知呼叫者，工作群組目前是否在取消作業的過程中。 這不一定表示 `cancel` 已在物件上呼叫方法（不過，這種方法肯定會傳回 `structured_task_group` **`true`** ）。 在此情況下， `structured_task_group` 物件是以內嵌方式執行，而且已取消工作樹狀結構中的工作組。 在這類情況下，執行時間可以在這種情況下判斷取消將流經此 `structured_task_group` 物件的情況，也 **`true`** 會傳回。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>傳回值

指出 `structured_task_group` 物件是否在取消的過程中（或在不久後保證會）。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="run"></a><a name="run"></a>進行

在物件上排定工作 `structured_task_group` 。 呼叫端會管理 `task_handle` 參數中傳遞之物件的存留期 `_Task_handle` 。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。

```cpp
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的型別，將叫用此類型來執行工作控制碼的主體。

*_Task_handle*<br/>
要排程之工作的控制碼。 請注意，呼叫端具有此物件存留期的責任。 執行時間會繼續預期其存留，直到在 `wait` `run_and_wait` 此物件上呼叫或方法為止 `structured_task_group` 。

*_Placement*<br/>
位置的參考，這是 `_Task_handle` 參數代表的工作應該執行的位置。

### <a name="remarks"></a>備註

執行時間會建立您傳遞給這個方法的工作函式複本。 您傳遞給這個方法的函式物件中發生的任何狀態變更，都不會出現在該函式物件的複本中。

如果 `structured_task_group` destructs 是堆疊從例外狀況回溯的結果，您就不需要保證已對 `wait` 或方法進行呼叫 `run_and_wait` 。 在此情況下，析構函式會適當地取消，並等候參數所代表的工作 `_Task_handle` 完成。

如果參數[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)所指定的工作控制碼已透過 `_Task_handle` 方法排程到工作組物件 `run` ，而且沒有對 `wait` 該工作組的或方法進行中間呼叫，則會擲回 invalid_multiple_scheduling 例外狀況 `run_and_wait` 。

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

使用物件的協助，將工作排程在呼叫內容上以內嵌方式執行，以 `structured_task_group` 提供完整的取消支援。 如果 `task_handle` 物件當做參數傳遞至 `run_and_wait` ，呼叫端會負責管理物件的存留期 `task_handle` 。 然後，函式會等到物件上的所有工作 `structured_task_group` 都已完成或已取消。

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>參數

*_Function*<br/>
將要叫用以執行工作的函式物件類型。

*_Task_handle*<br/>
將在呼叫內容上以內嵌方式執行之工作的控制碼。 請注意，呼叫端具有此物件存留期的責任。 執行時間會繼續預期其存留，直到 `run_and_wait` 方法完成執行為止。

*_Func*<br/>
將呼叫以叫用工作主體的函式。 這可能是 lambda 或其他物件，可支援具有簽章的函式呼叫運算子版本 `void operator()()` 。

### <a name="return-value"></a>傳回值

指出是否已滿足等候或取消工作群組，原因是明確取消作業或從其其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>備註

請注意，排程至此物件的一或多個工作 `structured_task_group` 可能會在呼叫內容上以內嵌方式執行。

如果有一或多個排程至此物件的工作擲 `structured_task_group` 回例外狀況，則執行時間會選取其中一個這類例外狀況，並將其傳播到方法的呼叫之外 `run_and_wait` 。

這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意，在方法傳回後的使用率 `run_and_wait` 會導致未定義的行為。

在非例外的執行路徑中，您必須在執行的析構函式之前，先呼叫這個方法或 `wait` 方法 `structured_task_group` 。

## <a name="structured_task_group"></a><a name="ctor"></a>structured_task_group

建構新的 `structured_task_group` 物件。

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>參數

*_CancellationToken*<br/>
要與此結構化工作組產生關聯的解除標記。 解除標記時，將會取消結構化工作組。

### <a name="remarks"></a>備註

使用取消語彙基元的建構函式會建立 `structured_task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的解除標記也會隔離此結構化工作組，使其無法從具有不同標記或沒有標記的父群組參與隱含取消。

## <a name="structured_task_group"></a><a name="dtor"></a>~ structured_task_group

終結 `structured_task_group` 物件。 在 `wait` `run_and_wait` 執行析構函式之前，您應該在物件上呼叫或方法，除非因為發生例外狀況而導致因為堆疊回溯而執行的析構函數。

```cpp
~structured_task_group();
```

### <a name="remarks"></a>備註

如果函式是以正常執行的結果來執行（例如，因為例外狀況而不是堆疊回溯），而且 `wait` `run_and_wait` 尚未呼叫或方法，則此析構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。

## <a name="wait"></a><a name="wait"></a>等候

等到上的所有工作 `structured_task_group` 都完成或取消為止。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>傳回值

指出是否已滿足等候或取消工作群組，原因是明確取消作業或從其其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>備註

請注意，排程至此物件的一或多個工作 `structured_task_group` 可能會在呼叫內容上以內嵌方式執行。

如果有一或多個排程至此物件的工作擲 `structured_task_group` 回例外狀況，則執行時間會選取其中一個這類例外狀況，並將其傳播到方法的呼叫之外 `wait` 。

這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意，在方法傳回後的使用率 `wait` 會導致未定義的行為。

在非例外的執行路徑中，您必須在執行的析構函式之前，先呼叫這個方法或 `run_and_wait` 方法 `structured_task_group` 。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[task_handle 類別](task-handle-class.md)
