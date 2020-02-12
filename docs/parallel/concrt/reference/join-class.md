---
title: join 類別
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139855"
---
# <a name="join-class"></a>join 類別

`join` 傳訊區塊是單一目標、多來源的排序 `propagator_block`，會與來自其每個來源的 `T` 類型訊息合併。

## <a name="syntax"></a>語法

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>參數

*T*<br/>
區塊所聯結和傳播之訊息的裝載類型。

*_Jtype*<br/>
`join` 封鎖這種情況，`greedy` 或 `non_greedy`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[join](#ctor)|已多載。 建構 `join` 傳訊區塊。|
|[~ 聯結析構函式](#dtor)|損毀 `join` 區塊。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `join` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|取用 `join` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `join` 訊息區塊。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `join` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|當每個來源的輸入訊息全部傳播一則訊息時，就會建立輸出訊息。 將輸出訊息傳送給它的每個目標。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `join` 訊息區塊先前提供的訊息。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept_message"></a>accept_message

接受此 `join` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

## <a name="consume_message"></a>consume_message

取用 `join` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所使用之 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

類似于 `accept`，但一律會在 `reserve`的呼叫前面加上。

## <a name="ctor"></a>接入

建構 `join` 傳訊區塊。

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_NumInputs*<br/>
將允許此 `join` 區塊的輸入數目。

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `join` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型 `filter_method` 是具有簽章 `bool (T const &)` 的仿函數，此 `join` 訊息區塊會叫用此方法，以判斷是否應該接受提供的訊息。

## <a name="dtor"></a>~ 聯結

損毀 `join` 區塊。

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `join` 訊息區塊。

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `join` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

當每個來源的輸入訊息全部傳播一則訊息時，就會建立輸出訊息。 將輸出訊息傳送給它的每個目標。

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

保留此 `join` 訊息區塊先前提供的訊息。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

如果成功保留訊息，**則為 true** ，否則為**false** 。

### <a name="remarks"></a>備註

呼叫 `reserve` 之後，如果傳回**true**，`consume` 或 `release` 必須呼叫以取得或釋放訊息的擁有權。

## <a name="resume_propagation"></a>resume_propagation

在發行保留專案之後繼續傳播。

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[choice 類別](choice-class.md)<br/>
[multitype_join 類別](multitype-join-class.md)
