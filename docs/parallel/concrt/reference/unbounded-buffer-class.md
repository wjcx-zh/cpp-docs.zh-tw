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
ms.openlocfilehash: e02fa1ffbf4c3e2c7d17dfe2d6ae66758945d9de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219516"
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

|名稱|說明|
|----------|-----------------|
|[unbounded_buffer](#ctor)|已多載。 結構 `unbounded_buffer` 訊息區塊。|
|[~ unbounded_buffer 的析構函式](#dtor)|損毀 `unbounded_buffer` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[清除佇列](#dequeue)|從訊息區塊中移除專案 `unbounded_buffer` 。|
|[加入佇列](#enqueue)|將專案加入至 `unbounded_buffer` 訊息區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此訊息區塊所提供的訊息 `unbounded_buffer` ，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|取用 `unbounded_buffer` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `unbounded_buffer` 訊息區塊。|
|[process_input_messages](#process_input_messages)|將放 `message` `_PMessage` 在此 `unbounded_buffer` 訊息區塊中，並嘗試將其提供給所有連結的目標。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞至此 `unbounded_buffer` 訊息區塊。 `propagate`當由來源區塊呼叫時，方法會叫用它。|
|[propagate_output_messages](#propagate_output_messages)|將放 `message` `_PMessage` 在此 `unbounded_buffer` 訊息區塊中，並嘗試將其提供給所有連結的目標。 （覆寫[source_block：:p ropagate_output_messages](source-block-class.md#propagate_output_messages)）。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此訊息區塊先前提供的訊息 `unbounded_buffer` 。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|以同步方式將訊息從 `ISource` 區塊傳遞到此 `unbounded_buffer` 訊息區塊。 `send`當由來源區塊呼叫時，方法會叫用它。|
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 （覆寫[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

如需詳細資訊，請參閱[非同步訊息區塊](../asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此訊息區塊所提供的訊息 `unbounded_buffer` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

取用 `unbounded_buffer` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在使用之物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

類似于 `accept` ，但一律會在的呼叫前面加上 `reserve` 。

## <a name="dequeue"></a><a name="dequeue"></a>去除

從訊息區塊中移除專案 `unbounded_buffer` 。

```cpp
_Type dequeue();
```

### <a name="return-value"></a>傳回值

從移除的訊息承載 `unbounded_buffer` 。

## <a name="enqueue"></a><a name="enqueue"></a>佇列

將專案加入至 `unbounded_buffer` 訊息區塊。

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>參數

*_Item*<br/>
要新增的項目。

### <a name="return-value"></a>傳回值

**`true`** 如果已接受專案，則 **`false`** 為，否則為。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `unbounded_buffer` 訊息區塊。

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
新連結目標的指標。

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞至此 `unbounded_buffer` 訊息區塊。 `propagate`當由來源區塊呼叫時，方法會叫用它。

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

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

將放 `message` `_PMessage` 在此 `unbounded_buffer` 訊息區塊中，並嘗試將其提供給所有連結的目標。

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>備註

如果另一個訊息已經在中，則在 `unbounded_buffer` 接受或取用任何先前的訊息之前，將不會傳播至連結的目標。 第一個連結目標成功 `accept` 或 `consume` 訊息會取得擁有權，而其他目標則無法取得訊息。

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

將放 `message` `_PMessage` 在此 `unbounded_buffer` 訊息區塊中，並嘗試將其提供給所有連結的目標。

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="release_message"></a><a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在釋放之物件的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此訊息區塊先前提供的訊息 `unbounded_buffer` 。

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

## <a name="send_message"></a><a name="send_message"></a>send_message

以同步方式將訊息從 `ISource` 區塊傳遞到此 `unbounded_buffer` 訊息區塊。 `send`當由來源區塊呼叫時，方法會叫用它。

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

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**`true`** 因為區塊不會延後提供的訊息。

## <a name="unbounded_buffer"></a><a name="ctor"></a>unbounded_buffer

結構 `unbounded_buffer` 訊息區塊。

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

類型是具有簽章的 `filter_method` 仿函數， `bool (_Type const &)` 此訊息區塊會叫用該簽章， `unbounded_buffer` 以判斷它是否應該接受提供的訊息。

## <a name="unbounded_buffer"></a><a name="dtor"></a>~ unbounded_buffer

損毀 `unbounded_buffer` 訊息區塊。

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[overwrite_buffer 類別](overwrite-buffer-class.md)<br/>
[single_assignment 類別](single-assignment-class.md)
