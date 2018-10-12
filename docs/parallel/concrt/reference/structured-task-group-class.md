---
title: structured_task_group 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e87ebd4523b5211c94955b5bec7905ed848946
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161680"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group 類別

`structured_task_group` 類別代表平行工作的高度結構化集合。 您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。

## <a name="syntax"></a>語法

```
class structured_task_group;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[structured_task_group](#ctor)|多載。 建構新`structured_task_group`物件。|
|[~ structured_task_group 解構函式](#dtor)|終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前，物件上的方法，除非在執行解構函式的堆疊回溯，因為發生例外狀況。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[[取消]](#cancel)|會盡力嘗試取消子樹狀結構的根目錄位於此工作群組的工作。 排定的工作群組上的每項工作將會取消間接的話。|
|[is_canceling](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定表示所`cancel`上呼叫方法`structured_task_group`物件 (雖然這類當然限定此方法以傳回 **，則為 true**)。 它可能會發生情況的`structured_task_group`物件以內嵌方式執行及工作群組的進一步設定工作樹狀目錄中已取消。 在這些位置等的情況下，執行階段可以判斷事先取消將會流經這`structured_task_group`物件， **，則為 true**會一併傳回。|
|[run](#run)|多載。 排程工作上`structured_task_group`物件。 呼叫端管理的存留期`task_handle`傳入物件`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|
|[run_and_wait](#run_and_wait)|多載。 排程工作將內嵌在環境中執行呼叫的協助`structured_task_group`完整的取消支援的物件。 如果`task_handle`物件會傳遞做為參數`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。 函式，然後等待直到所有處理`structured_task_group`物件已完成或已取消。|
|[等候](#wait)|等待所有工作`structured_task_group`已完成或取消。|

## <a name="remarks"></a>備註

但有些嚴重的使用方式的限制`structured_task_group`才能獲得的效能物件：

- 單一`structured_task_group`物件不能由多個執行緒。 上的所有作業`structured_task_group`物件只能由建立物件的執行緒。 此規則的兩個例外狀況是成員函式`cancel`和`is_canceling`。 物件可能無法在 lambda 運算式的擷取清單，除非工作使用的其中一個取消作業，可用於工作。

- 所有排定的工作`structured_task_group`物件會使用排程`task_handle`物件，您必須明確地管理的存留期。

- 多個群組只用於絕對巢狀的順序。 如果兩個`structured_task_group`宣告的物件、 第二個宣告 （內部的那一個） 必須以外的任何方法之前解構`cancel`或`is_canceling`上第一個呼叫 （外部的那一個）。 在這兩個案例中的只將宣告多個這種情況成立`structured_task_group`內的相同或巢狀功能的範圍，以及已排入佇列工作的大小寫的物件`structured_task_group`透過`run`或`run_and_wait`方法。

- 不同於一般`task_group`類別中的所有狀態`structured_task_group`都類別是最後一個。 您將工作佇列至群組並等候工作完成之後，就不能再使用同一個群組。

如需詳細資訊，請參閱 <<c0> [ 工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`structured_task_group`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="cancel"></a> [取消]

會盡力嘗試取消子樹狀結構的根目錄位於此工作群組的工作。 排定的工作群組上的每項工作將會取消間接的話。

```
void cancel();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

##  <a name="is_canceling"></a> is_canceling

通知呼叫端工作群組是目前在取消作業。 這不一定表示所`cancel`上呼叫方法`structured_task_group`物件 (雖然這類當然限定此方法以傳回 **，則為 true**)。 它可能會發生情況的`structured_task_group`物件以內嵌方式執行及工作群組的進一步設定工作樹狀目錄中已取消。 在這些位置等的情況下，執行階段可以判斷事先取消將會流經這`structured_task_group`物件， **，則為 true**會一併傳回。

```
bool is_canceling();
```

### <a name="return-value"></a>傳回值

指出是否`structured_task_group`物件正取消 （或一定會短時間內）。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

##  <a name="run"></a> 執行

排程工作上`structured_task_group`物件。 呼叫端管理的存留期`task_handle`傳入物件`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。

```
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
若要執行的工作控制代碼的主體就會叫用的函式物件類型。

*_Task_handle*<br/>
這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續直到存留預期`wait`或是`run_and_wait`呼叫此方法`structured_task_group`物件。

*放置 （_p)*<br/>
位置的參考，這是 `_Task_handle` 參數代表的工作應該執行的位置。

### <a name="remarks"></a>備註

執行階段會建立一份您傳遞給此方法的工作函式。 您傳遞給此方法的函式物件中發生的任何狀態變更不會出現該函式物件的複本中。

如果`structured_task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證，呼叫至任一`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消，並等候工作由`_Task_handle`參數來完成。

會擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果工作處理的例外狀況提供`_Task_handle`透過將工作群組物件上的參數已排定`run`方法而且沒有任何介入呼叫請`wait`或`run_and_wait`該工作群組上的方法。

##  <a name="run_and_wait"></a> run_and_wait

排程工作將內嵌在環境中執行呼叫的協助`structured_task_group`完整的取消支援的物件。 如果`task_handle`物件會傳遞做為參數`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。 函式，然後等待直到所有處理`structured_task_group`物件已完成或已取消。

```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>參數

*_Function*<br/>
將要叫用以執行工作的函式物件類型。

*_Task_handle*<br/>
這會在呼叫的內容上執行內嵌工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續存留的預期`run_and_wait`方法完成執行。

*_Func*<br/>
要叫用工作的主體所呼叫函式。 這可能是 lambda 或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。

### <a name="return-value"></a>傳回值

指出是否滿意等待結果或工作群組已取消，因為明確的取消作業或其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>備註

請注意的一或多個工作排定這`structured_task_group`物件可能會在呼叫的內容中執行內嵌。

如果一或多個排定的工作至此`structured_task_group`物件會擲回的例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並傳播到呼叫`run_and_wait`方法。

這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意之後, 的使用量`run_and_wait`方法會傳回將會導致未定義的行為。

在非例外狀況的執行路徑中，您有必要呼叫這個方法或`wait`方法之前的解構函式`structured_task_group`執行。

##  <a name="ctor"></a> structured_task_group

建構新`structured_task_group`物件。

```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>參數

*_CancellationToken*<br/>
此結構化的工作群組相關聯的取消語彙基元。 當取消語彙基元時，將會取消結構化的工作群組。

### <a name="remarks"></a>備註

使用取消語彙基元的建構函式會建立 `structured_task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的取消語彙基元時，也會隔離參與從不同的語彙基元或沒有語彙基元的父群組隱含取消此結構化的工作群組。

##  <a name="dtor"></a> ~structured_task_group

終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前，物件上的方法，除非在執行解構函式的堆疊回溯，因為發生例外狀況。

```
~structured_task_group();
```

### <a name="remarks"></a>備註

如果解構函式而執行的一般執行 （例如，沒有堆疊回溯因為發生例外狀況） 和都`wait`也`run_and_wait`已呼叫方法、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。

##  <a name="wait"></a> 等候

等待所有工作`structured_task_group`已完成或取消。

```
task_group_status wait();
```

### <a name="return-value"></a>傳回值

指出是否滿意等待結果或工作群組已取消，因為明確的取消作業或其中一個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>備註

請注意的一或多個工作排定這`structured_task_group`物件可能會在呼叫的內容中執行內嵌。

如果一或多個排定的工作至此`structured_task_group`物件會擲回的例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並傳播到呼叫`wait`方法。

這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意之後, 的使用量`wait`方法會傳回將會導致未定義的行為。

在非例外狀況的執行路徑中，您有必要呼叫這個方法或`run_and_wait`方法之前的解構函式`structured_task_group`執行。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[task_handle 類別](task-handle-class.md)
