---
title: target_block 類別
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: 4009133161133a99aeb0ee040f0c82fdbabecaa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142646"
---
# <a name="target_block-class"></a>target_block 類別

`target_block` 類別是一種抽象基底類別，可提供基本的連結管理功能和僅限目標區塊的錯誤檢查。

## <a name="syntax"></a>語法

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>參數

*_SourceLinkRegistry*<br/>
用來保存來源連結的連結登錄。

*_MessageProcessorType*<br/>
訊息處理的處理器類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`source_iterator`|這個 `target_block` 物件之 `source_link_manager` 的反覆運算器類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[target_block](#ctor)|建構 `target_block` 物件。|
|[~ target_block 的析構函式](#dtor)|終結 `target_block` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[傳遞](#propagate)|以非同步方式將訊息從來源區塊傳遞至此目標區塊。|
|[傳送](#send)|以同步方式將訊息從來源區塊傳遞至此目標區塊。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|以非同步方式傳送訊息以進行處理。|
|[decline_incoming_messages](#decline_incoming_messages)|向區塊指示新訊息應被拒絕。|
|[enable_batched_processing](#enable_batched_processing)|啟用這個區塊的批次處理。|
|[initialize_target](#initialize_target)|初始化基底物件。 具體而言，必須初始化 `message_processor` 物件。|
|[link_source](#link_source)|將指定的來源區塊連結至此 `target_block` 物件。|
|[process_input_messages](#process_input_messages)|處理收到的輸入訊息。|
|[process_message](#process_message)|在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。|
|[propagate_message](#propagate_message)|在衍生類別中覆寫時，這個方法會以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `target_block` 物件。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[register_filter](#register_filter)|註冊將在每個收到的訊息上叫用的篩選方法。|
|[remove_sources](#remove_sources)|等候待處理的非同步傳送作業完成之後，將所有來源取消對應。|
|[send_message](#send_message)|在衍生類別中覆寫時，這個方法會以同步方式將訊息從 `ISource` 區塊傳遞到這個 `target_block` 物件。 它是由來源區塊呼叫時，由 `send` 方法叫用。|
|[sync_send](#sync_send)|同步傳送訊息以進行處理。|
|[unlink_source](#unlink_source)|從這個 `target_block` 物件將指定的來源區塊取消與其之間的。|
|[unlink_sources](#unlink_sources)|將此 `target_block` 物件中的所有來源區塊取消此元素。 （覆寫[ITarget：： unlink_sources](itarget-class.md#unlink_sources)。）|
|[wait_for_async_sends](#wait_for_async_sends)|等候所有非同步傳播完成。|

## <a name="inheritance-hierarchy"></a>繼承階層

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="async_send"></a>async_send

以非同步方式傳送訊息以進行處理。

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要傳送之訊息的指標。

## <a name="decline_incoming_messages"></a>decline_incoming_messages

向區塊指示新訊息應被拒絕。

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>備註

這個方法是由析構函式呼叫，以確保在進行銷毀時，會拒絕新的訊息。

## <a name="enable_batched_processing"></a>enable_batched_processing

啟用這個區塊的批次處理。

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a>initialize_target

初始化基底物件。 具體而言，必須初始化 `message_processor` 物件。

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
用於排程工作的排程器。

*_PScheduleGroup*<br/>
用於排程工作的排程群組。

## <a name="link_source"></a>link_source

將指定的來源區塊連結至此 `target_block` 物件。

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
要連結之 `ISource` 區塊的指標。

### <a name="remarks"></a>備註

此函式不應直接在 `target_block` 物件上呼叫。 區塊應該使用 `ISource` 區塊上的 `link_target` 方法連接在一起，這會在對應的目標上叫用 `link_source` 方法。

## <a name="process_input_messages"></a>process_input_messages

處理收到的輸入訊息。

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="process_message"></a>process_message

在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a>傳遞

以非同步方式將訊息從來源區塊傳遞至此目標區塊。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

## <a name="propagate_message"></a>propagate_message

在衍生類別中覆寫時，這個方法會以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `target_block` 物件。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

## <a name="register_filter"></a>register_filter

註冊將在每個收到的訊息上叫用的篩選方法。

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_Filter*<br/>
篩選方法。

## <a name="remove_sources"></a>remove_sources

等候待處理的非同步傳送作業完成之後，將所有來源取消對應。

```cpp
void remove_sources();
```

### <a name="remarks"></a>備註

所有的目標區塊都應該呼叫此常式，以移除其析構函式中的來源。

## <a name="send"></a>發送

以同步方式將訊息從來源區塊傳遞至此目標區塊。

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

在訊息初始外使用 `send` 方法，並在網路內傳播訊息是危險的，而且可能會導致鎖死。

當 `send` 傳回時，訊息可能已經被接受，並已傳送到目標區塊，或已被目標拒絕。

## <a name="send_message"></a>send_message

在衍生類別中覆寫時，這個方法會以同步方式將訊息從 `ISource` 區塊傳遞到這個 `target_block` 物件。 它是由來源區塊呼叫時，由 `send` 方法叫用。

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

根據預設，除非由衍生類別覆寫，否則此區塊會傳回 `declined`。

## <a name="sync_send"></a>sync_send

同步傳送訊息以進行處理。

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要傳送之訊息的指標。

## <a name="ctor"></a>target_block

建構 `target_block` 物件。

```cpp
target_block();
```

## <a name="dtor"></a>~ target_block

終結 `target_block` 物件。

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a>unlink_source

從這個 `target_block` 物件將指定的來源區塊取消與其之間的。

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
要取消連結之 `ISource` 區塊的指標。

## <a name="unlink_sources"></a>unlink_sources

將此 `target_block` 物件中的所有來源區塊取消此元素。

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a>wait_for_async_sends

等候所有非同步傳播完成。

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>備註

訊息區塊的析構函數會使用這個方法，以確保所有非同步作業在終結區塊之前都有時間完成。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ITarget 類別](itarget-class.md)
