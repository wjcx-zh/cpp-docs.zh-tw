---
title: timer 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b821dcc3426c6e1d9f3cd2f2ff8eb057197ca8d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416197"
---
# <a name="timer-class"></a>timer 類別

`timer` 傳訊區塊是單一目標 `source_block`，能夠在經過指定的時間長度或在特定時間間隔，將訊息傳送至它的目標。

## <a name="syntax"></a>語法

```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

#### <a name="parameters"></a>參數

*T*<br/>
此區塊輸出訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[timer](#ctor)|多載。 建構`timer`傳訊區塊，將指定的間隔之後引發指定的訊息。|
|[~ timer 解構函式](#dtor)|終結`timer`傳訊區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[pause](#pause)|停駐點`timer`傳訊區塊。 如果它是重複`timer`傳訊區塊，它可以重新啟動，後續`start()`呼叫。 對於非重複的計時器，這會有相同的效果`stop`呼叫。|
|[start](#start)|啟動`timer`傳訊區塊。 呼叫指定在此之後的毫秒數，就會傳送指定的值為下游`message`。|
|[stop](#stop)|停駐點`timer`傳訊區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受的訊息，由此`timer`傳訊區塊，將擁有權傳送給呼叫者。|
|[consume_message](#consume_message)|會使用先前所提供訊息`timer`和目標，將擁有權傳送給呼叫者所保留。|
|[link_target_notification](#link_target_notification)|通知新目標，已連結至這個回呼`timer`傳訊區塊。|
|[propagate_to_any_targets](#propagate_to_any_targets)|嘗試提供所產生的訊息`timer`所有連結的目標區塊。|
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留先前由此訊息`timer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|保留區釋出之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="accept_message"></a> accept_message

接受的訊息，由此`timer`傳訊區塊，將擁有權傳送給呼叫者。

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

##  <a name="consume_message"></a> consume_message

會使用先前所提供訊息`timer`和目標，將擁有權傳送給呼叫者所保留。

```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件被取用。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

### <a name="remarks"></a>備註

類似於`accept`，但一律置於呼叫`reserve`。

##  <a name="link_target_notification"></a> link_target_notification

通知新目標，已連結至這個回呼`timer`傳訊區塊。

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
新連結的目標指標。

##  <a name="pause"></a> 暫停

停駐點`timer`傳訊區塊。 如果它是重複`timer`傳訊區塊，它可以重新啟動，後續`start()`呼叫。 對於非重複的計時器，這會有相同的效果`stop`呼叫。

```
void pause();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

嘗試提供所產生的訊息`timer`所有連結的目標區塊。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

##  <a name="release_message"></a> release_message

釋放先前的訊息保留。

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件被釋放。

##  <a name="reserve_message"></a> reserve_message

保留先前由此訊息`timer`傳訊區塊。

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件所保留。

### <a name="return-value"></a>傳回值

`true` 如果已成功保留訊息，`false`否則。

### <a name="remarks"></a>備註

在後`reserve`呼叫時，如果它傳回`true`，可以是`consume`或`release`採取，或釋放訊息的擁有權必須先呼叫。

##  <a name="resume_propagation"></a> resume_propagation

保留區釋出之後，請繼續傳播。

```
virtual void resume_propagation();
```

##  <a name="start"></a> 啟動

啟動`timer`傳訊區塊。 呼叫指定在此之後的毫秒數，就會傳送指定的值為下游`message`。

```
void start();
```

##  <a name="stop"></a> 停止

停駐點`timer`傳訊區塊。

```
void stop();
```

##  <a name="ctor"></a> 計時器

建構`timer`傳訊區塊，將指定的間隔之後引發指定的訊息。

```
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
在下游傳播到指定的訊息啟動的呼叫必須經過的毫秒數。

*值*<br/>
計時器耗盡時下游傳播值。

*_PTarget*<br/>
計時器會將其訊息傳送目標。

*_Repeating*<br/>
如果為 true，表示計時器會定期引發每`_Ms`毫秒為單位。

*_Scheduler*<br/>
`Scheduler`物件的傳播工作在其中`timer`傳訊區塊排程已排程。

*_ScheduleGroup*<br/>
`ScheduleGroup`物件的傳播工作在其中`timer`傳訊區塊已排程。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定，執行階段會使用預設排程器`_Scheduler`或`_ScheduleGroup`參數。

##  <a name="dtor"></a> ~ 計時器

終結`timer`傳訊區塊。

```
~timer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
