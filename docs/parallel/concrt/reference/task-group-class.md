---
title: task_group 類別
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142572"
---
# <a name="task_group-class"></a>task_group 類別

`task_group` 類別表示可以等候或取消的平行工作集合。

## <a name="syntax"></a>語法

```cpp
class task_group;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_group](#ctor)|已多載。 建構新的 `task_group` 物件。|
|[~ task_group 的析構函式](#dtor)|終結 `task_group` 物件。 在執行析構函式之前，您應該先在物件上呼叫 `wait` 或 `run_and_wait` 方法，除非因例外狀況而將析構函數當做堆疊回溯的結果執行。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[cancel](#cancel)|盡全力嘗試取消根節點的子樹，而此工作群組為 root。 可能的話，在工作組上排程的每個工作都將被取消傳遞。|
|[is_canceling](#is_canceling)|通知呼叫者，工作群組目前是否在取消作業的過程中。 這不一定表示已在 `task_group` 物件上呼叫 `cancel` 方法（雖然這當然會限定此方法以傳回 `true`）。 在此情況下，`task_group` 物件是以內嵌方式執行，而且已取消工作樹狀結構中的工作組。 在這類情況下，執行時間可以提早判斷取消作業會流經此 `task_group` 物件的情況，也會傳回 `true`。|
|[run](#run)|已多載。 在 `task_group` 物件上排定工作。 如果 `task_handle` 物件當做參數傳遞至 `run`，呼叫端就會負責管理 `task_handle` 物件的存留期。 接受函式物件參考做為參數的方法版本牽涉到執行時間內的堆積配置，而此版本可能比使用取得 `task_handle` 物件參考的版本還少。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|
|[run_and_wait](#run_and_wait)|已多載。 將工作排程在呼叫內容上以內嵌方式執行，並具有 `task_group` 物件的協助，以提供完整的取消支援。 然後，函式會等到 `task_group` 物件上的所有工作都已完成或已取消為止。 如果 `task_handle` 物件當做參數傳遞至 `run_and_wait`，呼叫端就會負責管理 `task_handle` 物件的存留期。|
|[等候](#wait)|等到 `task_group` 物件上的所有工作都已完成或已取消為止。|

## <a name="remarks"></a>備註

不同于嚴格限制的 `structured_task_group` 類別，`task_group` 類別是較為一般的結構。 它沒有[structured_task_group](structured-task-group-class.md)所描述的任何限制。 `task_group` 物件可以安全地跨執行緒使用，並以自由形式的方式運用。 `task_group` 結構的缺點是，它可能不會執行，也不會針對執行少量工作的工作進行 `structured_task_group` 結構。

如需詳細資訊，請參閱工作[平行](../task-parallelism-concurrency-runtime.md)處理原則。

## <a name="inheritance-hierarchy"></a>繼承階層

`task_group`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** concurrency

## <a name="cancel"></a>取消

盡全力嘗試取消根節點的子樹，而此工作群組為 root。 可能的話，在工作組上排程的每個工作都將被取消傳遞。

```cpp
void cancel();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。

## <a name="is_canceling"></a>is_canceling

通知呼叫者，工作群組目前是否在取消作業的過程中。 這不一定表示已在 `task_group` 物件上呼叫 `cancel` 方法（雖然這當然會限定此方法以傳回 `true`）。 在此情況下，`task_group` 物件是以內嵌方式執行，而且已取消工作樹狀結構中的工作組。 在這類情況下，執行時間可以提早判斷取消作業會流經此 `task_group` 物件的情況，也會傳回 `true`。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>傳回值

指出 `task_group` 物件是否在取消作業的過程中（或在不久後保證會）。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。

## <a name="run"></a>進行

在 `task_group` 物件上排定工作。 如果 `task_handle` 物件當做參數傳遞至 `run`，呼叫端就會負責管理 `task_handle` 物件的存留期。 接受函式物件參考做為參數的方法版本牽涉到執行時間內的堆積配置，而此版本可能比使用取得 `task_handle` 物件參考的版本還少。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的型別，將叫用此類型來執行工作控制碼的主體。

*_Func*<br/>
將呼叫以叫用工作主體的函式。 這可能是 lambda 運算式或其他物件，它支援具有簽章 `void operator()()`之函式呼叫運算子的版本。

*_Placement*<br/>
位置的參考，這是 `_Func` 參數代表的工作應該執行的位置。

*_Task_handle*<br/>
要排程之工作的控制碼。 請注意，呼叫端具有此物件存留期的責任。 執行時間會繼續預期其存留，直到在這個 `task_group` 物件上呼叫 `wait` 或 `run_and_wait` 方法為止。

### <a name="remarks"></a>備註

執行時間會將提供的工作函式排程在稍後執行，這可能會在呼叫函式傳回之後。 這個方法會使用[task_handle](task-handle-class.md)物件來保存所提供工作函式的複本。 因此，您傳遞給這個方法的函式物件中發生的任何狀態變更，都不會出現在該函式物件的複本中。 此外，請確定您在工作函式傳回之前，由指標傳遞或參考工作函式的任何物件存留期都維持有效。

如果 `task_group` destructs 為從例外狀況回溯堆疊的結果，您就不需要保證已對 `wait` 或 `run_and_wait` 方法進行呼叫。 在此情況下，析構函式會適當地取消，並等候 `_Task_handle` 參數所表示的工作完成。

如果已透過 `run` 方法將 `_Task_handle` 參數所指定的工作控制碼排程到工作組物件，而且該工作組上沒有任何對 `wait` 或 `run_and_wait` 方法的呼叫，此方法就會擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外狀況。

## <a name="run_and_wait"></a>run_and_wait

將工作排程在呼叫內容上以內嵌方式執行，並具有 `task_group` 物件的協助，以提供完整的取消支援。 然後，函式會等到 `task_group` 物件上的所有工作都已完成或已取消為止。 如果 `task_handle` 物件當做參數傳遞至 `run_and_wait`，呼叫端就會負責管理 `task_handle` 物件的存留期。

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的類型，將會叫用它來執行工作主體。

*_Task_handle*<br/>
將在呼叫內容上以內嵌方式執行之工作的控制碼。 請注意，呼叫端具有此物件存留期的責任。 執行時間會繼續預期其存留，直到 `run_and_wait` 方法完成執行為止。

*_Func*<br/>
將呼叫以叫用工作主體的函式。 這可能是 lambda 運算式或其他物件，它支援具有簽章 `void operator()()`之函式呼叫運算子的版本。

### <a name="return-value"></a>傳回值

指出是否已滿足等候或取消工作群組，原因是明確取消作業或從其其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>備註

請注意，排程至此 `task_group` 物件的一或多項工作，可能會在呼叫內容上以內嵌方式執行。

如果一或多個排程至此 `task_group` 物件的工作擲回例外狀況，則執行時間會從其選擇中選取其中一個例外狀況，並將其傳播到 `run_and_wait` 方法的呼叫之外。

從 `task_group` 物件上的 `run_and_wait` 方法傳回時，執行時間會將物件重設為可重複使用的清除狀態。 這包括取消 `task_group` 物件的情況。

在非例外的執行路徑中，您必須在執行 `task_group` 的析構函式之前，先呼叫這個方法或 `wait` 方法。

## <a name="ctor"></a>task_group

建構新的 `task_group` 物件。

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>參數

*_CancellationToken*<br/>
取消與這個工作群組相關聯的語彙基元。 取消語彙基元時，工作群組也會取消。

### <a name="remarks"></a>備註

使用取消語彙基元的建構函式會建立 `task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的取消語彙基元也會將這個工作群組隔離，使其無法參與具有不同語彙基元或沒有語彙基元之父群組的隱含取消。

## <a name="dtor"></a>~ task_group

終結 `task_group` 物件。 在執行析構函式之前，您應該先在物件上呼叫 `wait` 或 `run_and_wait` 方法，除非因例外狀況而將析構函數當做堆疊回溯的結果執行。

```cpp
~task_group();
```

### <a name="remarks"></a>備註

如果此析構函式是以正常執行的結果來執行（例如，因為例外狀況而不是堆疊回溯），而且尚未呼叫 `wait` 或 `run_and_wait` 方法，則此析構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。

## <a name="wait"></a>等候

等到 `task_group` 物件上的所有工作都已完成或已取消為止。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>傳回值

指出是否已滿足等候或取消工作群組，原因是明確取消作業或從其其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>備註

請注意，排程至此 `task_group` 物件的一或多項工作，可能會在呼叫內容上以內嵌方式執行。

如果一或多個排程至此 `task_group` 物件的工作擲回例外狀況，則執行時間會從其選擇中選取其中一個例外狀況，並將其傳播到 `wait` 方法的呼叫之外。

在 `task_group` 物件上呼叫 `wait`，會將它重設為可重複使用的狀態。 這包括取消 `task_group` 物件的情況。

在非例外的執行路徑中，您必須在執行 `task_group` 的析構函式之前，先呼叫這個方法或 `run_and_wait` 方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)<br/>
[task_handle 類別](task-handle-class.md)
