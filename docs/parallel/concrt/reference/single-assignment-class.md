---
title: single_assignment 類別
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142730"
---
# <a name="single_assignment-class"></a>single_assignment 類別

`single_assignment` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠儲存寫入一次的單一 `message`。

## <a name="syntax"></a>語法

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>參數

*T*<br/>
緩衝區所儲存和傳播之訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[single_assignment](#ctor)|已多載。 建構 `single_assignment` 傳訊區塊。|
|[~ single_assignment 的析構函式](#dtor)|損毀 `single_assignment` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[has_value](#has_value)|檢查此 `single_assignment` 訊息區塊是否已使用值進行初始化。|
|[value](#value)|取得目前儲存在 `single_assignment` 訊息區塊中之訊息承載的參考。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受這個 `single_assignment` 訊息塊所提供的訊息，並將訊息的複本傳回給呼叫者。|
|[consume_message](#consume_message)|使用先前由 `single_assignment` 提供並由目標所保留的訊息，並將訊息複本傳回給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `single_assignment` 訊息區塊。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|將 `message _PMessage` 放在此 `single_assignment` 訊息區塊中，並將其提供給所有連結的目標。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `single_assignment` 訊息區塊先前提供的訊息。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。|

## <a name="remarks"></a>備註

`single_assignment` 訊息塊會將其訊息的複本傳播到每個目標。

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept_message"></a>accept_message

接受這個 `single_assignment` 訊息塊所提供的訊息，並將訊息的複本傳回給呼叫者。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

`single_assignment` 訊息塊會將訊息的複本傳回至其目標，而不是轉移目前保留訊息的擁有權。

## <a name="consume_message"></a>consume_message

使用先前由 `single_assignment` 提供並由目標所保留的訊息，並將訊息複本傳回給呼叫者。

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所使用之 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

類似于 `accept`，但一律會在 `reserve`的呼叫前面加上。

## <a name="has_value"></a>has_value

檢查此 `single_assignment` 訊息區塊是否已使用值進行初始化。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>傳回值

如果區塊已收到值，**則為 true** ，否則為**false** 。

## <a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `single_assignment` 訊息區塊。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
新連結目標的指標。

## <a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

```cpp
virtual message_status propagate_message(
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

將 `message` `_PMessage` 放在此 `single_assignment` 訊息塊中，並將其提供給所有連結的目標。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
這個 `single_assignment` 訊息區塊已取得其擁有權之 `message` 的指標。

## <a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要釋放之 `message` 物件的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `single_assignment` 訊息區塊先前提供的訊息。

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

以同步方式將訊息從 `ISource` 區塊傳遞到這個 `single_assignment` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。

```cpp
virtual message_status send_message(
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

## <a name="ctor"></a>single_assignment

建構 `single_assignment` 傳訊區塊。

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `single_assignment` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `single_assignment` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型 `filter_method` 是具有簽章 `bool (T const &)` 的仿函數，此 `single_assignment` 訊息區塊會叫用此方法，以判斷是否應該接受提供的訊息。

## <a name="dtor"></a>~ single_assignment

損毀 `single_assignment` 訊息區塊。

```cpp
~single_assignment();
```

## <a name="value"></a>value

取得目前儲存在 `single_assignment` 訊息區塊中之訊息承載的參考。

```cpp
T const& value();
```

### <a name="return-value"></a>傳回值

預存訊息的裝載。

### <a name="remarks"></a>備註

如果目前沒有訊息儲存在 `single_assignment` 訊息區塊中，這個方法會等待訊息抵達。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[overwrite_buffer 類別](overwrite-buffer-class.md)<br/>
[unbounded_buffer 類別](unbounded-buffer-class.md)
