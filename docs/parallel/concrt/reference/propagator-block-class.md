---
title: propagator_block 類別
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138747"
---
# <a name="propagator_block-class"></a>propagator_block 類別

`propagator_block` 類別是同時為來源和目標之訊息區塊的抽象基底類別。 它結合 `source_block` 和 `target_block` 類別的功能。

## <a name="syntax"></a>語法

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>參數

*_TargetLinkRegistry*<br/>
用來保存目標連結的連結登錄。

*_SourceLinkRegistry*<br/>
用來保存來源連結的連結登錄。

*_MessageProcessorType*<br/>
訊息處理的處理器類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`source_iterator`|這個 `propagator_block`之 `source_link_manager` 的反覆運算器類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[propagator_block](#ctor)|建構 `propagator_block` 物件。|
|[~ propagator_block 的析構函式](#dtor)|終結 `propagator_block` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[傳遞](#propagate)|以非同步方式將訊息從來源區塊傳遞至此目標區塊。|
|[傳送](#send)|以同步方式對此區塊起始訊息。 由 `ISource` 區塊呼叫。 當此函式完成時，訊息就已經傳播到區塊中。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|向區塊指示新訊息應被拒絕。|
|[initialize_source_and_target](#initialize_source_and_target)|初始化基底物件。 具體而言，必須初始化 `message_processor` 物件。|
|[link_source](#link_source)|將指定的來源區塊連結至此 `propagator_block` 物件。|
|[process_input_messages](#process_input_messages)|處理輸入訊息。 這僅適用于衍生自 source_block 的傳播程式區塊（覆寫[source_block：:p rocess_input_messages](source-block-class.md#process_input_messages)）。|
|[propagate_message](#propagate_message)|在衍生類別中覆寫時，這個方法會以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `propagator_block` 物件。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[register_filter](#register_filter)|註冊將在每個收到的訊息上叫用的篩選方法。|
|[remove_network_links](#remove_network_links)|從這個 `propagator_block` 物件移除所有來源和目標網路連結。|
|[send_message](#send_message)|在衍生類別中覆寫時，這個方法會以同步方式將訊息從 `ISource` 區塊傳遞到這個 `propagator_block` 物件。 它是由來源區塊呼叫時，由 `send` 方法叫用。|
|[unlink_source](#unlink_source)|從這個 `propagator_block` 物件將指定的來源區塊取消與其之間的。|
|[unlink_sources](#unlink_sources)|將此 `propagator_block` 物件中的所有來源區塊取消此元素。 （覆寫[ITarget：： unlink_sources](itarget-class.md#unlink_sources)。）|

## <a name="remarks"></a>備註

為避免多重繼承，`propagator_block` 類別會繼承自 `source_block` 類別並 `ITarget` 抽象類別。 這裡會複寫 `target_block` 類別中的大部分功能。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="decline_incoming_messages"></a>decline_incoming_messages

向區塊指示新訊息應被拒絕。

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>備註

這個方法是由析構函式呼叫，以確保在進行銷毀時，會拒絕新的訊息。

## <a name="initialize_source_and_target"></a>initialize_source_and_target

初始化基底物件。 具體而言，必須初始化 `message_processor` 物件。

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
用於排程工作的排程器。

*_PScheduleGroup*<br/>
用於排程工作的排程群組。

## <a name="link_source"></a>link_source

將指定的來源區塊連結至此 `propagator_block` 物件。

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
要連結之 `ISource` 區塊的指標。

## <a name="process_input_messages"></a>process_input_messages

處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

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

連結的來源區塊會在目標區塊上叫用 `propagate` 方法。 它會將非同步工作排入佇列，以處理訊息（如果尚未在佇列中或正在執行的話）。

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

## <a name="propagate_message"></a>propagate_message

在衍生類別中覆寫時，這個方法會以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `propagator_block` 物件。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

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

## <a name="ctor"></a>propagator_block

建構 `propagator_block` 物件。

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

終結 `propagator_block` 物件。

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

註冊將在每個收到的訊息上叫用的篩選方法。

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_Filter*<br/>
篩選方法。

## <a name="remove_network_links"></a>remove_network_links

從這個 `propagator_block` 物件移除所有來源和目標網路連結。

```cpp
void remove_network_links();
```

## <a name="send"></a>發送

以同步方式對此區塊起始訊息。 由 `ISource` 區塊呼叫。 當此函式完成時，訊息就已經傳播到區塊中。

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

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，這個方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

## <a name="send_message"></a>send_message

在衍生類別中覆寫時，這個方法會以同步方式將訊息從 `ISource` 區塊傳遞到這個 `propagator_block` 物件。 它是由來源區塊呼叫時，由 `send` 方法叫用。

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

根據預設，除非由衍生類別覆寫，否則此區塊會傳回 `declined`。

## <a name="unlink_source"></a>unlink_source

從這個 `propagator_block` 物件將指定的來源區塊取消與其之間的。

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
要取消連結之 `ISource` 區塊的指標。

## <a name="unlink_sources"></a>unlink_sources

將此 `propagator_block` 物件中的所有來源區塊取消此元素。

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[source_block 類別](source-block-class.md)<br/>
[ITarget 類別](itarget-class.md)
