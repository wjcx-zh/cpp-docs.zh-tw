---
title: unbounded_buffer 類別
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142326"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer 類別

`unbounded_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠存放無限個訊息。

## <a name="syntax"></a>語法

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>參數

*_Type*<br/>
緩衝區所儲存和傳播之訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unbounded_buffer](#ctor)|已多載。 構造 `unbounded_buffer` 的訊息區塊。|
|[~ unbounded_buffer 的析構函式](#dtor)|損毀 `unbounded_buffer` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[去除](#dequeue)|從 `unbounded_buffer` 的訊息區塊中移除專案。|
|[佇列](#enqueue)|將專案加入至 `unbounded_buffer` 的訊息區塊。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `unbounded_buffer` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|取用 `unbounded_buffer` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `unbounded_buffer` 訊息區塊。|
|[process_input_messages](#process_input_messages)|將 `message` `_PMessage` 放在此 `unbounded_buffer` 訊息塊中，並嘗試將其提供給所有連結的目標。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `unbounded_buffer` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[propagate_output_messages](#propagate_output_messages)|將 `message` `_PMessage` 放在此 `unbounded_buffer` 訊息塊中，並嘗試將其提供給所有連結的目標。 （覆寫[source_block：:p ropagate_output_messages](source-block-class.md#propagate_output_messages)）。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `unbounded_buffer` 訊息區塊先前提供的訊息。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `unbounded_buffer` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。|
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 （覆寫[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

如需詳細資訊，請參閱[非同步訊息區塊](../asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept_message"></a>accept_message

接受此 `unbounded_buffer` 訊息塊所提供的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

## <a name="consume_message"></a>consume_message

取用 `unbounded_buffer` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所使用之 `message` 物件的 `runtime_object_identity`。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

類似于 `accept`，但一律會在 `reserve`的呼叫前面加上。

## <a name="dequeue"></a>去除

從 `unbounded_buffer` 的訊息區塊中移除專案。

```cpp
_Type dequeue();
```

### <a name="return-value"></a>傳回值

從 `unbounded_buffer`中移除的訊息承載。

## <a name="enqueue"></a>佇列

將專案加入至 `unbounded_buffer` 的訊息區塊。

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>參數

*_Item*<br/>
要新增的項目。

### <a name="return-value"></a>傳回值

如果已接受專案，**則為 true** ，否則為**false** 。

## <a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `unbounded_buffer` 訊息區塊。

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
新連結目標的指標。

## <a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `unbounded_buffer` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md#message_status)指出目標決定要如何處理訊息。

## <a name="propagate_output_messages"></a>propagate_output_messages

將 `message` `_PMessage` 放在此 `unbounded_buffer` 訊息塊中，並嘗試將其提供給所有連結的目標。

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>備註

如果 `unbounded_buffer`中已經有另一個訊息，則必須等到任何先前的訊息被接受或取用之後，才會傳播到連結的目標。 成功 `accept` 或 `consume` 訊息的第一個連結目標會取得擁有權，而其他目標則無法取得訊息。

## <a name="process_input_messages"></a>process_input_messages

將 `message` `_PMessage` 放在此 `unbounded_buffer` 訊息塊中，並嘗試將其提供給所有連結的目標。

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要釋放之 `message` 物件的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `unbounded_buffer` 訊息區塊先前提供的訊息。

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

以同步方式將訊息從 `ISource` 區塊傳遞到這個 `unbounded_buffer` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md#message_status)指出目標決定要如何處理訊息。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**true** ，因為區塊不會延後提供的訊息。

## <a name="ctor"></a>unbounded_buffer

構造 `unbounded_buffer` 的訊息區塊。

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>參數

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `unbounded_buffer` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `unbounded_buffer` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型 `filter_method` 是具有簽章 `bool (_Type const &)` 的仿函數，此 `unbounded_buffer` 訊息區塊會叫用此方法，以判斷是否應該接受提供的訊息。

## <a name="dtor"></a>~ unbounded_buffer

損毀 `unbounded_buffer` 訊息區塊。

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[overwrite_buffer 類別](overwrite-buffer-class.md)<br/>
[single_assignment 類別](single-assignment-class.md)
