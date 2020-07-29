---
title: agent 類別
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f1d98cdc6237f182e0240a85f2fdce3410232195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213888"
---
# <a name="agent-class"></a>agent 類別

適合做為所有獨立代理程式之基底類別的類別。 它用來對其他代理程式隱藏狀態，並使用訊息傳遞互動。

## <a name="syntax"></a>語法

```cpp
class agent;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[代理程式](#ctor)|已多載。 構造代理程式。|
|[~ agent 析構函式](#dtor)|終結代理程式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[cancel](#cancel)|將代理程式從 `agent_created` 或狀態移 `agent_runnable` 至 `agent_canceled` 狀態。|
|[開始](#start)|將代理程式從 `agent_created` 狀態移至 `agent_runnable` 狀態，並排定它執行。|
|[status](#status)|來自代理程式之狀態資訊的同步來源。|
|[status_port](#status_port)|來自代理程式之狀態資訊的非同步來源。|
|[等候](#wait)|等候代理程式完成其工作。|
|[wait_for_all](#wait_for_all)|等候所有指定的代理程式完成其工作。|
|[wait_for_one](#wait_for_one)|等候任何一個指定的代理程式完成其工作。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[完成](#done)|將代理程式移至 `agent_done` 狀態，表示代理程式已完成。|
|[進行](#run)|代表代理程式的主要工作。 `run`應該在衍生類別中覆寫，並指定代理程式在啟動後應執行的動作。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步代理](../../../parallel/concrt/asynchronous-agents.md)程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`agent`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="agent"></a><a name="ctor"></a>代理程式

構造代理程式。

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
`Scheduler`要在其中排程代理程式之執行工作的物件。

*_PGroup*<br/>
`ScheduleGroup`要在其中排程代理程式之執行工作的物件。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PGroup` 參數，執行階段會使用預設排程器。

## <a name="agent"></a><a name="dtor"></a>~ 代理程式

終結代理程式。

```cpp
virtual ~agent();
```

### <a name="remarks"></a>備註

終結不是處於終止狀態的代理程式（或）時，會發生錯誤 `agent_done` `agent_canceled` 。 您可以等候代理程式在繼承自類別的類別的析構函式中，達到終止狀態，藉此避免這種情況 `agent` 。

## <a name="cancel"></a><a name="cancel"></a>取消

將代理程式從 `agent_created` 或狀態移 `agent_runnable` 至 `agent_canceled` 狀態。

```cpp
bool cancel();
```

### <a name="return-value"></a>傳回值

**`true`** 如果已取消代理程式，則 **`false`** 為，否則為。 如果代理程式已經開始執行或已經完成，就無法取消。

## <a name="done"></a><a name="done"></a>即可

將代理程式移至 `agent_done` 狀態，表示代理程式已完成。

```cpp
bool done();
```

### <a name="return-value"></a>傳回值

**`true`** 如果代理程式已移至 `agent_done` 狀態，則為， **`false`** 否則為。 已取消的代理程式無法移至 `agent_done` 狀態。

### <a name="remarks"></a>備註

`run`當您知道代理程式的執行已完成時，應該在方法的結尾呼叫這個方法。

## <a name="run"></a><a name="run"></a>進行

代表代理程式的主要工作。 `run`應該在衍生類別中覆寫，並指定代理程式在啟動後應執行的動作。

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>備註

代理程式狀態會在叫 `agent_started` 用此方法之前變更為右方。 方法應該在傳回 `done` 之前以適當的狀態在代理程式上叫用，而且可能不會擲回任何例外狀況。

## <a name="start"></a><a name="start"></a>「

將代理程式從 `agent_created` 狀態移至 `agent_runnable` 狀態，並排定它執行。

```cpp
bool start();
```

### <a name="return-value"></a>傳回值

**`true`** 如果代理程式已正確啟動，則 **`false`** 為，否則為。 無法啟動已取消的代理程式。

## <a name="status"></a><a name="status"></a>狀態

來自代理程式之狀態資訊的同步來源。

```cpp
agent_status status();
```

### <a name="return-value"></a>傳回值

傳回代理程式的目前狀態。 請注意，這個傳回的狀態可能會在傳回之後立即變更。

## <a name="status_port"></a><a name="status_port"></a>status_port

來自代理程式之狀態資訊的非同步來源。

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>傳回值

傳回訊息來源，可以傳送關於代理程式目前狀態的訊息。

## <a name="wait"></a><a name="wait"></a>等候

等候代理程式完成其工作。

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_PAgent*<br/>
要等候之代理程式的指標。

*_Timeout*<br/>
等待的時間上限（以毫秒為單位）。

### <a name="return-value"></a>傳回值

`agent_status`等候完成時，代理程式的。 這可以是 `agent_canceled` 或 `agent_done` 。

### <a name="remarks"></a>備註

當代理程式進入或狀態時，就會完成代理程式工作 `agent_canceled` `agent_done` 。

如果參數的 `_Timeout` 值不是常數 `COOPERATIVE_TIMEOUT_INFINITE` ，則如果指定的時間量在代理程式完成其工作之前過期，就會擲回例外狀況[operation_timed_out](operation-timed-out-class.md) 。

## <a name="wait_for_all"></a><a name="wait_for_all"></a>wait_for_all

等候所有指定的代理程式完成其工作。

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*計數*<br/>
陣列中存在的代理程式指標數目 `_PAgents` 。

*_PAgents*<br/>
要等候之代理程式的指標陣列。

*_PStatus*<br/>
代理程式狀態陣列的指標。 當方法傳回時，每個狀態值都會代表對應代理程式的狀態。

*_Timeout*<br/>
等待的時間上限（以毫秒為單位）。

### <a name="remarks"></a>備註

當代理程式進入或狀態時，就會完成代理程式工作 `agent_canceled` `agent_done` 。

如果參數的 `_Timeout` 值不是常數 `COOPERATIVE_TIMEOUT_INFINITE` ，則如果指定的時間量在代理程式完成其工作之前過期，就會擲回例外狀況[operation_timed_out](operation-timed-out-class.md) 。

## <a name="wait_for_one"></a><a name="wait_for_one"></a>wait_for_one

等候任何一個指定的代理程式完成其工作。

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*計數*<br/>
陣列中存在的代理程式指標數目 `_PAgents` 。

*_PAgents*<br/>
要等候之代理程式的指標陣列。

*_Status*<br/>
將放置代理程式狀態之變數的參考。

*_Index*<br/>
將放置代理程式索引之變數的參考。

*_Timeout*<br/>
等待的時間上限（以毫秒為單位）。

### <a name="remarks"></a>備註

當代理程式進入或狀態時，就會完成代理程式工作 `agent_canceled` `agent_done` 。

如果參數的 `_Timeout` 值不是常數 `COOPERATIVE_TIMEOUT_INFINITE` ，則如果指定的時間量在代理程式完成其工作之前過期，就會擲回例外狀況[operation_timed_out](operation-timed-out-class.md) 。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
