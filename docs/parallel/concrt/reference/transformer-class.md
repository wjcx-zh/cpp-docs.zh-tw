---
title: transformer 類別
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: 75c7697087b8b3ad8ff15ae4d08f2b4701aaa36a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142360"
---
# <a name="transformer-class"></a>transformer 類別

`transformer` 傳訊區塊是多來源的單一目標排序 `propagator_block`，可以存放無限個不同類型訊息。

## <a name="syntax"></a>語法

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>參數

*_Input*<br/>
緩衝區接受之訊息的裝載類型。

*_Output*<br/>
由緩衝區儲存和傳播之訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[轉換器](#ctor)|已多載。 建構 `transformer` 傳訊區塊。|
|[~ 轉換器的析構函式](#dtor)|損毀 `transformer` 訊息區塊。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `transformer` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|取用 `transformer` 先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `transformer` 訊息區塊。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|在輸入訊息上執行轉換器函式。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `transformer` 訊息區塊先前提供的訊息。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。|
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 （覆寫[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept_message"></a>accept_message

接受此 `transformer` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

## <a name="consume_message"></a>consume_message

取用 `transformer` 先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所使用之 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

類似于 `accept`，但一律會在 `reserve`的呼叫前面加上。

## <a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `transformer` 訊息區塊。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

在輸入訊息上執行轉換器函式。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要釋放之 `message` 物件的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `transformer` 訊息區塊先前提供的訊息。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要保留之 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

如果成功保留訊息，**則為 true** ，否則為**false** 。

### <a name="remarks"></a>備註

呼叫 `reserve` 之後，如果傳回**true**，`consume` 或 `release` 必須呼叫以取得或釋放訊息的擁有權。

## <a name="resume_propagation"></a>resume_propagation

在發行保留專案之後繼續傳播。

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

以同步方式將訊息從 `ISource` 區塊傳遞到這個 `transformer` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**true** ，因為區塊不會延後提供的訊息。

## <a name="ctor"></a>轉換器

建構 `transformer` 傳訊區塊。

```cpp
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_Func*<br/>
會針對每個接受的訊息叫用的函式。

*_PTarget*<br/>
要與轉換器連結之目標區塊的指標。

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `transformer` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `transformer` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型 `_Transform_method` 是具有簽章 `_Output (_Input const &)` 的仿函數，此 `transformer` 訊息區塊會叫用此方法來處理訊息。

類型 `filter_method` 是具有簽章 `bool (_Input const &)` 的仿函數，此 `transformer` 訊息區塊會叫用此方法，以判斷是否應該接受提供的訊息。

## <a name="dtor"></a>~ 轉換器

損毀 `transformer` 訊息區塊。

```cpp
~transformer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[call 類別](call-class.md)
