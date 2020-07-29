---
title: timer 類別
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: 026aef03bb813585decb206c1691835330a4dd05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224938"
---
# <a name="timer-class"></a>timer 類別

`timer` 傳訊區塊是單一目標 `source_block`，能夠在經過指定的時間長度或在特定時間間隔，將訊息傳送至它的目標。

## <a name="syntax"></a>語法

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>參數

*T*<br/>
此區塊之輸出訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[timer](#ctor)|已多載。 `timer`建立將在指定的間隔之後引發指定訊息的訊息區塊。|
|[~ 計時器的析構函式](#dtor)|終結 `timer` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[pause](#pause)|停止 `timer` 訊息區塊。 如果它是重複的 `timer` 訊息區塊，則可以使用後續呼叫來重新開機 `start()` 。 對於非重複計時器，這與呼叫的效果相同 `stop` 。|
|[開始](#start)|啟動 `timer` 訊息區塊。 呼叫這個的指定毫秒數之後，指定的值將會以的形式傳播到下游 `message` 。|
|[停止](#stop)|停止 `timer` 訊息區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此訊息區塊所提供的訊息 `timer` ，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|使用先前由提供的訊息 `timer` ，並由目標保留，將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `timer` 訊息區塊。|
|[propagate_to_any_targets](#propagate_to_any_targets)|嘗試將區塊所產生的訊息提供 `timer` 給所有連結的目標。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此訊息區塊先前提供的訊息 `timer` 。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此訊息區塊所提供的訊息 `timer` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

使用先前由提供的訊息 `timer` ，並由目標保留，將擁有權轉移給呼叫者。

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在使用之物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

類似于 `accept` ，但一律會在的呼叫前面加上 `reserve` 。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `timer` 訊息區塊。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
新連結目標的指標。

## <a name="pause"></a><a name="pause"></a>中斷

停止 `timer` 訊息區塊。 如果它是重複的 `timer` 訊息區塊，則可以使用後續呼叫來重新開機 `start()` 。 對於非重複計時器，這與呼叫的效果相同 `stop` 。

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

嘗試將區塊所產生的訊息提供 `timer` 給所有連結的目標。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在釋放之物件的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此訊息區塊先前提供的訊息 `timer` 。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 要保留之物件的。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

`reserve`呼叫之後，如果傳回，則 **`true`** `consume` `release` 必須呼叫或，才能取得或釋放訊息的擁有權。

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

在發行保留專案之後繼續傳播。

```cpp
virtual void resume_propagation();
```

## <a name="start"></a><a name="start"></a>「

啟動 `timer` 訊息區塊。 呼叫這個的指定毫秒數之後，指定的值將會以的形式傳播到下游 `message` 。

```cpp
void start();
```

## <a name="stop"></a><a name="stop"></a>停止

停止 `timer` 訊息區塊。

```cpp
void stop();
```

## <a name="timer"></a><a name="ctor"></a>timer

`timer`建立將在指定的間隔之後引發指定訊息的訊息區塊。

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>參數

*_Ms*<br/>
要在指定的訊息開始傳播下游之後，必須經過的毫秒數。

*value*<br/>
當計時器過期時，將會傳播下游的值。

*_PTarget*<br/>
計時器將傳播其訊息的目標。

*_Repeating*<br/>
若為 true，表示計時器會每毫秒定期引發 `_Ms` 。

*_Scheduler*<br/>
排程 `Scheduler` 訊息區塊之傳播工作的物件 `timer` 。

*_ScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `timer` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_Scheduler` 或 `_ScheduleGroup` 參數，執行階段會使用預設排程器。

## <a name="timer"></a><a name="dtor"></a>~ 計時器

終結 `timer` 訊息區塊。

```cpp
~timer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
