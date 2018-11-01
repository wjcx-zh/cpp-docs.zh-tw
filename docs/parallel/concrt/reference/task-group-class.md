---
title: task_group 類別
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 1ba7251afca80c561bd8861968c35e3242c1507a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588847"
---
# <a name="taskgroup-class"></a>task_group 類別

`task_group` 類別表示可以等候或取消的平行工作集合。

## <a name="syntax"></a>語法

```
class task_group;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_group](#ctor)|多載。 建構新`task_group`物件。|
|[~ task_group 解構函式](#dtor)|終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前，除非解構函式執行時的堆疊回溯，因為發生例外狀況結果的物件上的方法。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[[取消]](#cancel)|會盡力嘗試取消子樹狀結構的根目錄位於此工作群組的工作。 排定的工作群組上的每項工作將會取消間接的話。|
|[is_canceling](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定表示所`cancel`上呼叫方法`task_group`物件 (雖然這類當然限定此方法以傳回`true`)。 它可能會發生情況的`task_group`物件以內嵌方式執行及工作群組的進一步設定工作樹狀目錄中已取消。 在這些位置等的情況下，執行階段可以判斷事先取消將會流經這`task_group`物件，`true`會一併傳回。|
|[run](#run)|多載。 排程工作上`task_group`物件。 如果`task_handle`物件會傳遞做為參數`run`，呼叫端會負責管理的存留期`task_handle`物件。 函式物件的參考當成參數包含堆積配置，這可能是在執行階段內方法之版本的執行效能比使用會參考的版本不佳`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|
|[run_and_wait](#run_and_wait)|多載。 排程工作將內嵌在環境中執行呼叫的協助`task_group`完整的取消支援的物件。 函式，然後等待直到所有處理`task_group`物件已完成或已取消。 如果`task_handle`物件會傳遞做為參數`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。|
|[等候](#wait)|等待所有工作`task_group`物件已完成或已取消。|

## <a name="remarks"></a>備註

不同於大量受限`structured_task_group`類別，`task_group`類別是範圍更為廣泛的建構。 它未包含任何所描述的限制[structured_task_group](structured-task-group-class.md)。 `task_group` 物件可能安全地使用多個執行緒和自由格式的方式使用。 缺點`task_group`建構是它可能無法執行，以及`structured_task_group`建構之工作的執行少量的工作。

如需詳細資訊，請參閱 <<c0> [ 工作平行處理原則](../task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`task_group`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="cancel"></a> [取消]

會盡力嘗試取消子樹狀結構的根目錄位於此工作群組的工作。 排定的工作群組上的每項工作將會取消間接的話。

```
void cancel();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 取消](../cancellation-in-the-ppl.md)。

##  <a name="is_canceling"></a> is_canceling

通知呼叫端工作群組是目前在取消作業。 這不一定表示所`cancel`上呼叫方法`task_group`物件 (雖然這類當然限定此方法以傳回`true`)。 它可能會發生情況的`task_group`物件以內嵌方式執行及工作群組的進一步設定工作樹狀目錄中已取消。 在這些位置等的情況下，執行階段可以判斷事先取消將會流經這`task_group`物件，`true`會一併傳回。

```
bool is_canceling();
```

### <a name="return-value"></a>傳回值

指出是否`task_group`物件正取消 （或一定會短時間內）。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 取消](../cancellation-in-the-ppl.md)。

##  <a name="run"></a> 執行

排程工作上`task_group`物件。 如果`task_handle`物件會傳遞做為參數`run`，呼叫端會負責管理的存留期`task_handle`物件。 函式物件的參考當成參數包含堆積配置，這可能是在執行階段內方法之版本的執行效能比使用會參考的版本不佳`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。

```
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
若要執行的工作控制代碼的主體就會叫用的函式物件類型。

*_Func*<br/>
要叫用工作的主體所呼叫函式。 這可能是 lambda 運算式或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。

*放置 （_p)*<br/>
位置的參考，這是 `_Func` 參數代表的工作應該執行的位置。

*_Task_handle*<br/>
這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續直到存留預期`wait`或是`run_and_wait`呼叫此方法`task_group`物件。

### <a name="remarks"></a>備註

執行階段排程在稍後的時間，可以呼叫的函式傳回之後，執行所提供的工作函式。 這個方法會使用[task_handle](task-handle-class.md)物件來保存一份所提供的工作函式。 因此，您將傳遞給這個方法的函式物件中發生的任何狀態變更不會出現該函式物件的複本中。 此外，請確定您傳遞指標或參考的工作函式的任何物件的存留期保持有效，直到工作函式傳回。

如果`task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證，呼叫至任一`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消，並等候工作由`_Task_handle`參數來完成。

方法會擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果工作處理的例外狀況提供`_Task_handle`透過將工作群組物件上的參數已排定`run`方法而且沒有任何中間呼叫至任一`wait`或`run_and_wait`該工作群組上的方法。

##  <a name="run_and_wait"></a> run_and_wait

排程工作將內嵌在環境中執行呼叫的協助`task_group`完整的取消支援的物件。 函式，然後等待直到所有處理`task_group`物件已完成或已取消。 如果`task_handle`物件會傳遞做為參數`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。

```
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
這會在呼叫的內容上執行內嵌工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續存留的預期`run_and_wait`方法完成執行。

*_Func*<br/>
要叫用工作的主體所呼叫函式。 這可能是 lambda 運算式或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。

### <a name="return-value"></a>傳回值

指出是否滿意等待結果或工作群組已取消，因為明確的取消作業或其中一個工作擲回例外狀況。 如需詳細資訊，請參閱 < [task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>備註

請注意的一或多個工作排定這`task_group`物件可能會在呼叫的內容中執行內嵌。

如果一或多個排定的工作至此`task_group`物件會擲回的例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並傳播到呼叫`run_and_wait`方法。

傳回從時`run_and_wait`方法`task_group`物件，執行階段的物件重設成可重複使用的初始狀態。 這包括大小寫，`task_group`物件已取消。

在非例外狀況的執行路徑中，您有必要呼叫這個方法或`wait`方法之前的解構函式`task_group`執行。

##  <a name="ctor"></a> task_group

建構新`task_group`物件。

```
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

##  <a name="dtor"></a> ~ task_group

終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前，除非解構函式執行時的堆疊回溯，因為發生例外狀況結果的物件上的方法。

```
~task_group();
```

### <a name="remarks"></a>備註

如果解構函式而執行的一般執行 （例如，沒有堆疊回溯因為發生例外狀況） 和都`wait`也`run_and_wait`已呼叫方法、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。

##  <a name="wait"></a> 等候

等待所有工作`task_group`物件已完成或已取消。

```
task_group_status wait();
```

### <a name="return-value"></a>傳回值

指出是否滿意等待結果或工作群組已取消，因為明確的取消作業或其中一個工作擲回例外狀況。 如需詳細資訊，請參閱 < [task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>備註

請注意的一或多個工作排定這`task_group`物件可能會在呼叫的內容中執行內嵌。

如果一或多個排定的工作至此`task_group`物件會擲回的例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並傳播到呼叫`wait`方法。

呼叫`wait`上`task_group`物件將它重設成可重複使用的初始狀態。 這包括大小寫，`task_group`物件已取消。

在非例外狀況的執行路徑中，您有必要呼叫這個方法或`run_and_wait`方法之前的解構函式`task_group`執行。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)<br/>
[task_handle 類別](task-handle-class.md)