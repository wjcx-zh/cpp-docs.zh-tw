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
ms.openlocfilehash: c07017539bc0125e9e8c27e208480a50ccc7a719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408065"
---
# <a name="transformer-class"></a>transformer 類別

`transformer` 傳訊區塊是多來源的單一目標排序 `propagator_block`，可以存放無限個不同類型訊息。

## <a name="syntax"></a>語法

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>參數

*_Input*<br/>
緩衝區所接受之訊息的裝載類型。

*_Output*<br/>
儲存及緩衝區所傳播之訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[transformer](#ctor)|多載。 建構 `transformer` 傳訊區塊。|
|[~ transformer 解構函式](#dtor)|終結`transformer`傳訊區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受的訊息，由此`transformer`傳訊區塊，將擁有權傳送給呼叫者。|
|[consume_message](#consume_message)|會使用先前所提供訊息`transformer`和目標，將擁有權傳送給呼叫者所保留。|
|[link_target_notification](#link_target_notification)|通知新目標，已連結至這個回呼`transformer`傳訊區塊。|
|[propagate_message](#propagate_message)|以非同步方式傳遞的訊息`ISource`至此區塊`transformer`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。|
|[propagate_to_any_targets](#propagate_to_any_targets)|在輸入訊息上執行轉換器函式。|
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留先前由此訊息`transformer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|保留區釋出之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|
|[send_message](#send_message)|以同步方式傳遞的訊息`ISource`至此區塊`transformer`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。|
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="accept_message"></a> accept_message

接受的訊息，由此`transformer`傳訊區塊，將擁有權傳送給呼叫者。

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

##  <a name="consume_message"></a> consume_message

會使用先前所提供訊息`transformer`和目標，將擁有權傳送給呼叫者所保留。

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件被取用。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

### <a name="remarks"></a>備註

類似於`accept`，但一律置於呼叫`reserve`。

##  <a name="link_target_notification"></a> link_target_notification

通知新目標，已連結至這個回呼`transformer`傳訊區塊。

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

以非同步方式傳遞的訊息`ISource`至此區塊`transformer`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息來源區塊的指標。

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

在輸入訊息上執行轉換器函式。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

保留先前由此訊息`transformer`傳訊區塊。

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件所保留。

### <a name="return-value"></a>傳回值

**真**已成功保留訊息，如果**false**否則。

### <a name="remarks"></a>備註

之後`reserve`呼叫時，如果它傳回 **，則為 true**可以`consume`或`release`必須呼叫採取，或釋放訊息的擁有權。

##  <a name="resume_propagation"></a> resume_propagation

保留區釋出之後，請繼續傳播。

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

以同步方式傳遞的訊息`ISource`至此區塊`transformer`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息來源區塊的指標。

### <a name="return-value"></a>傳回值

A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**true**因為區塊不會延後提供的訊息。

##  <a name="ctor"></a> 轉換程式

建構 `transformer` 傳訊區塊。

```
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
針對每個接受的訊息將會叫用函式。

*_PTarget*<br/>
要連結的轉換程式的目標區塊的指標。

*_Filter*<br/>
判斷是否應該接受所提供的訊息篩選器函式。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `transformer` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `transformer` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

型別`_Transform_method`是仿函式簽章`_Output (_Input const &)`由此叫用的所在`transformer`傳訊區塊處理的訊息。

型別`filter_method`是仿函式簽章`bool (_Input const &)`由此叫用的所在`transformer`傳訊區塊，以判斷是否應該接受接受所提供的訊息。

##  <a name="dtor"></a> ~transformer

終結`transformer`傳訊區塊。

```
~transformer();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[call 類別](call-class.md)
