---
title: target_block 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6cf1f5aadc566f1b09ad981f2431b2888b1661cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439584"
---
# <a name="targetblock-class"></a>target_block 類別

`target_block` 類別是一種抽象基底類別，可提供基本的連結管理功能和僅限目標區塊的錯誤檢查。

## <a name="syntax"></a>語法

```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>參數

*_SourceLinkRegistry*<br/>
要用於保存來源連結連結登錄中。

*_MessageProcessorType*<br/>
處理訊息的處理器類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`source_iterator`|迭代器的型別`source_link_manager`這個`target_block`物件。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[target_block](#ctor)|建構 `target_block` 物件。|
|[~ target_block 解構函式](#dtor)|終結`target_block`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[propagate](#propagate)|以非同步方式將訊息從來源區塊傳遞到此目標區塊。|
|[傳送](#send)|以同步方式將訊息從來源區塊傳遞到此目標區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|以非同步方式傳送訊息，以進行處理。|
|[decline_incoming_messages](#decline_incoming_messages)|表示區塊應該已拒絕新的訊息。|
|[enable_batched_processing](#enable_batched_processing)|啟用這個區塊的批次處理。|
|[initialize_target](#initialize_target)|初始化基底物件。 具體來說，`message_processor`需要初始化的物件。|
|[link_source](#link_source)|將指定的來源區塊連結至這個`target_block`物件。|
|[process_input_messages](#process_input_messages)|處理收到的輸入訊息。|
|[process_message](#process_message)|在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。|
|[propagate_message](#propagate_message)|此方法在衍生類別中覆寫，會以非同步方式傳遞的訊息`ISource`至此區塊`target_block`物件。 它由`propagate`方法中，當呼叫來源區塊。|
|[register_filter](#register_filter)|註冊將會叫用每個收到的訊息的篩選方法。|
|[remove_sources](#remove_sources)|等候未處理的非同步傳送作業完成之後，取消連結所有來源。|
|[send_message](#send_message)|此方法在衍生類別中覆寫，會以同步方式傳遞的訊息`ISource`至此區塊`target_block`物件。 它由`send`方法中，當呼叫來源區塊。|
|[sync_send](#sync_send)|以同步方式傳送訊息，以進行處理。|
|[unlink_source](#unlink_source)|取消連結此將指定的來源區塊`target_block`物件。|
|[unlink_sources](#unlink_sources)|取消連結所有來源區塊，從這個`target_block`物件。 (覆寫[itarget:: Unlink_sources](itarget-class.md#unlink_sources)。)|
|[wait_for_async_sends](#wait_for_async_sends)|等候所有完成的非同步傳用。|

## <a name="inheritance-hierarchy"></a>繼承階層

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="async_send"></a> async_send

以非同步方式傳送訊息，以進行處理。

```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
正在傳送的訊息指標。

##  <a name="decline_incoming_messages"></a> decline_incoming_messages

表示區塊應該已拒絕新的訊息。

```
void decline_incoming_messages();
```

### <a name="remarks"></a>備註

解構函式，以確保正在進行解構時，會拒絕新訊息會呼叫這個方法。

##  <a name="enable_batched_processing"></a> enable_batched_processing

啟用這個區塊的批次處理。

```
void enable_batched_processing();
```

##  <a name="initialize_target"></a> initialize_target

初始化基底物件。 具體來說，`message_processor`需要初始化的物件。

```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
要用於排程工作排程器。

*_PScheduleGroup*<br/>
要用於排程工作的排程群組。

##  <a name="link_source"></a> link_source

將指定的來源區塊連結至這個`target_block`物件。

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
指標`ISource`是要連結的區塊。

### <a name="remarks"></a>備註

此函式不應該直接在呼叫`target_block`物件。 區塊應該一起使用來連接`link_target`方法`ISource`區塊，將會叫用`link_source`相對應的目標上的方法。

##  <a name="process_input_messages"></a> process_input_messages

處理收到的輸入訊息。

```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
正在處理的訊息指標。

##  <a name="process_message"></a> process_message

在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。

```
virtual void process_message(message<_Source_type> *);
```

##  <a name="propagate"></a> 傳播

以非同步方式將訊息從來源區塊傳遞到此目標區塊。

```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息來源區塊的指標。

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

### <a name="remarks"></a>備註

方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果有任一`_PMessage`或是`_PSource`參數是`NULL`。

##  <a name="propagate_message"></a> propagate_message

此方法在衍生類別中覆寫，會以非同步方式傳遞的訊息`ISource`至此區塊`target_block`物件。 它由`propagate`方法中，當呼叫來源區塊。

```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息來源區塊的指標。

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

##  <a name="register_filter"></a> register_filter

註冊將會叫用每個收到的訊息的篩選方法。

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*篩選 （_f)*<br/>
篩選方法。

##  <a name="remove_sources"></a> remove_sources

等候未處理的非同步傳送作業完成之後，取消連結所有來源。

```
void remove_sources();
```

### <a name="remarks"></a>備註

所有的目標區塊應該呼叫這個常式，以移除其解構函式中的來源。

##  <a name="send"></a> 傳送

以同步方式將訊息從來源區塊傳遞到此目標區塊。

```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息來源區塊的指標。

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

### <a name="remarks"></a>備註

方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果有任一`_PMessage`或是`_PSource`參數是`NULL`。

使用`send`方法外部訊息起始，並傳播網路內的訊息很危險，有可能會導致死結。

當`send`傳回時，訊息可能是已接受，並傳輸至目標區塊，或已被拒絕的目標。

##  <a name="send_message"></a> send_message

此方法在衍生類別中覆寫，會以同步方式傳遞的訊息`ISource`至此區塊`target_block`物件。 它由`send`方法中，當呼叫來源區塊。

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

### <a name="remarks"></a>備註

根據預設，此區塊會傳回`declined`除非由衍生類別中覆寫。

##  <a name="sync_send"></a> sync_send

以同步方式傳送訊息，以進行處理。

```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
正在傳送的訊息指標。

##  <a name="ctor"></a> target_block

建構 `target_block` 物件。

```
target_block();
```

##  <a name="dtor"></a> ~ target_block

終結`target_block`物件。

```
virtual ~target_block();
```

##  <a name="unlink_source"></a> unlink_source

取消連結此將指定的來源區塊`target_block`物件。

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>參數

*_PSource*<br/>
指標`ISource`要取消連結的區塊。

##  <a name="unlink_sources"></a> unlink_sources

取消連結所有來源區塊，從這個`target_block`物件。

```
virtual void unlink_sources();
```

##  <a name="wait_for_async_sends"></a> wait_for_async_sends

等候所有完成的非同步傳用。

```
void wait_for_async_sends();
```

### <a name="remarks"></a>備註

訊息區塊解構函式會使用這個方法，以確保所有的非同步作業已完成，然後再終結該區塊的時間。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ITarget 類別](itarget-class.md)
