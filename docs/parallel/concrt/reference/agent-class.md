---
title: agent 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04202b647910914de8ebe92397efe1373e9508be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401364"
---
# <a name="agent-class"></a>agent 類別

適合做為所有獨立代理程式之基底類別的類別。 它用來對其他代理程式隱藏狀態，並使用訊息傳遞互動。

## <a name="syntax"></a>語法

```
class agent;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[agent](#ctor)|多載。 建構代理程式。|
|[~ agent 解構函式](#dtor)|終結代理程式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[[取消]](#cancel)|將代理程式從`agent_created`或是`agent_runnable`狀態來`agent_canceled`狀態。|
|[start](#start)|將代理程式`agent_created`狀態`agent_runnable`狀態，以及排程執行。|
|[status](#status)|從代理程式的狀態資訊的同步來源。|
|[status_port](#status_port)|從代理程式的狀態資訊的非同步來源。|
|[等候](#wait)|等候代理程式，以完成其工作。|
|[wait_for_all](#wait_for_all)|等待所有指定的代理程式，以完成其工作。|
|[wait_for_one](#wait_for_one)|等候任何一個指定的代理程式，以完成其工作。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[完成](#done)|移至代理程式`agent_done`狀態，表示代理程式已完成。|
|[run](#run)|表示代理程式的主要工作。 `run` 在衍生類別中，則應覆寫，並指定應該執行的代理程式已啟動之後。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步代理程式](../../../parallel/concrt/asynchronous-agents.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`agent`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="ctor"></a> 代理程式

建構代理程式。

```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
`Scheduler`物件內的代理程式執行工作排程。

*_PGroup*<br/>
`ScheduleGroup`物件內的代理程式執行工作排程。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定，執行階段會使用預設排程器`_PScheduler`或`_PGroup`參數。

##  <a name="dtor"></a> ~ 代理程式

終結代理程式。

```
virtual ~agent();
```

### <a name="remarks"></a>備註

是要終結程式不是處於終止狀態的代理程式錯誤 (請`agent_done`或`agent_canceled`)。 這可避免等候代理程式觸達終止狀態解構函式中的類別繼承自`agent`類別。

##  <a name="cancel"></a> [取消]

將代理程式從`agent_created`或是`agent_runnable`狀態來`agent_canceled`狀態。

```
bool cancel();
```

### <a name="return-value"></a>傳回值

`true` 如果代理程式已取消，`false`否則。 代理程式無法取消，如果它已經開始執行或已完成。

##  <a name="done"></a> 完成

移至代理程式`agent_done`狀態，表示代理程式已完成。

```
bool done();
```

### <a name="return-value"></a>傳回值

`true` 如果代理程式移至`agent_done`狀態，`false`否則。 已取消的代理程式無法移到`agent_done`狀態。

### <a name="remarks"></a>備註

這個方法應該呼叫在結尾`run`方法，當您知道您的代理程式執行時完成。

##  <a name="run"></a> 執行

表示代理程式的主要工作。 `run` 在衍生類別中，則應覆寫，並指定應該執行的代理程式已啟動之後。

```
virtual void run() = 0;
```

### <a name="remarks"></a>備註

代理程式狀態變更為`agent_started`叫用這個方法之前，以滑鼠右鍵。 此方法應該叫用`done`適當的狀態，在傳回之前，代理程式和可能不會擲回任何例外狀況。

##  <a name="start"></a> 啟動

將代理程式`agent_created`狀態`agent_runnable`狀態，以及排程執行。

```
bool start();
```

### <a name="return-value"></a>傳回值

`true` 如果代理程式正確地啟動`false`否則。 無法啟動代理程式已取消。

##  <a name="status"></a> 狀態

從代理程式的狀態資訊的同步來源。

```
agent_status status();
```

### <a name="return-value"></a>傳回值

傳回代理程式的目前狀態。 請注意，此傳回的狀態無法變更之後立即傳回。

##  <a name="status_port"></a> status_port

從代理程式的狀態資訊的非同步來源。

```
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>傳回值

傳回可將代理程式的目前狀態相關的訊息傳送的訊息來源。

##  <a name="wait"></a> 等候

等候代理程式，以完成其工作。

```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_PAgent*<br/>
等候代理程式 」 指標。

*逾時 _t*<br/>
要等待，以毫秒為單位的最大時間。

### <a name="return-value"></a>傳回值

`agent_status`等候完成時的代理程式。 這可以是`agent_canceled`或`agent_done`。

### <a name="remarks"></a>備註

代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。

如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。

##  <a name="wait_for_all"></a> wait_for_all

等待所有指定的代理程式，以完成其工作。

```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*count*<br/>
代理程式出現在陣列的指標的數目`_PAgents`。

*_PAgents*<br/>
等候代理程式的指標陣列。

*_PStatus*<br/>
代理程式狀態的陣列指標。 方法傳回時，每個狀態值會代表對應的代理程式的狀態。

*逾時 _t*<br/>
要等待，以毫秒為單位的最大時間。

### <a name="remarks"></a>備註

代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。

如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。

##  <a name="wait_for_one"></a> wait_for_one

等候任何一個指定的代理程式，以完成其工作。

```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*count*<br/>
代理程式出現在陣列的指標的數目`_PAgents`。

*_PAgents*<br/>
等候代理程式的指標陣列。

*_Status*<br/>
將放置代理程式狀態變數的參考。

*_Index*<br/>
代理程式索引放置變數的參考。

*逾時 _t*<br/>
要等待，以毫秒為單位的最大時間。

### <a name="remarks"></a>備註

代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。

如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
