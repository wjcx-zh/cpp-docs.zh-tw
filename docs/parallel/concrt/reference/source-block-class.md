---
title: source_block 類別
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 304bc65d969fa677d67bf578021a63f628e0a1f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228436"
---
# <a name="source_block-class"></a>source_block 類別

`source_block` 類別是僅限來源區塊的抽象基底類別。 類別會提供基本連結管理功能與常見的錯誤檢查功能。

## <a name="syntax"></a>語法

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>參數

*_TargetLinkRegistry*<br/>
用來存放目標連結的連結登錄。

*_MessageProcessorType*<br/>
訊息處理的處理器類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`target_iterator`|要引導已連接目標的反覆運算器。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[source_block](#ctor)|建構 `source_block` 物件。|
|[~ source_block 的析構函式](#dtor)|終結 `source_block` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[接受](#accept)|接受這個物件所提供的訊息 `source_block` ，並將擁有權轉移給呼叫者。|
|[acquire_ref](#acquire_ref)|取得此物件的參考計數 `source_block` ，以防止刪除。|
|[占](#consume)|使用此物件先前提供的訊息 `source_block` ，並由目標成功保留，並將擁有權轉移給呼叫者。|
|[link_target](#link_target)|將目標區塊連結至這個 `source_block` 物件。|
|[版本](#release)|釋放先前成功的訊息保留。|
|[release_ref](#release_ref)|釋放這個物件的參考計數 `source_block` 。|
|[留成](#reserve)|保留這個物件先前提供的訊息 `source_block` 。|
|[unlink_target](#unlink_target)|從這個物件取消目標區塊的與 `source_block`|
|[unlink_targets](#unlink_targets)|從這個物件取消所有目標區塊的 `source_block` （覆寫[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[accept_message](#accept_message)|在衍生類別中覆寫時，接受來源所提供的訊息。 訊息區塊應該覆寫這個方法，以驗證 `_MsgId` 並傳回訊息。|
|[async_send](#async_send)|以非同步方式將訊息排入佇列，並啟動傳播工作（如果尚未這麼做）|
|[consume_message](#consume_message)|在衍生類別中覆寫時，會使用先前保留的訊息。|
|[enable_batched_processing](#enable_batched_processing)|啟用這個區塊的批次處理。|
|[initialize_source](#initialize_source)|初始化 `message_propagator` 這個中的 `source_block` 。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `source_block` 物件。|
|[process_input_messages](#process_input_messages)|處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用|
|[propagate_output_messages](#propagate_output_messages)|將訊息傳播至目標。|
|[propagate_to_any_targets](#propagate_to_any_targets)|在衍生類別中覆寫時，將指定的訊息傳播至任何或所有連結的目標。 這是訊息區塊的主要傳播常式。|
|[release_message](#release_message)|在衍生類別中覆寫時，釋放先前的訊息保留。|
|[remove_targets](#remove_targets)|移除此來源區塊的所有目標連結。 這應該從「析構函式」呼叫。|
|[reserve_message](#reserve_message)|在衍生類別中覆寫時，保留這個物件先前提供的訊息 `source_block` 。|
|[resume_propagation](#resume_propagation)|在衍生類別中覆寫時，在釋放保留之後繼續傳播。|
|[sync_send](#sync_send)|同步將訊息排入佇列並啟動傳播工作（如果尚未這麼做）。|
|[unlink_target_notification](#unlink_target_notification)|回呼，會通知目標已從此物件取消連結 `source_block` 。|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|等候所有非同步傳播完成。 這項傳播程式特有的微調等候是用在訊息區塊的析構函數中，以確保所有非同步傳播在終結區塊之前都有時間完成。|

## <a name="remarks"></a>備註

訊息區塊應該衍生自這個區塊，以利用此類別所提供的連結管理和同步處理。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept"></a><a name="accept"></a>接受

接受這個物件所提供的訊息 `source_block` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `accept` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

`accept`當此區塊提供訊息時，目標會呼叫方法 `ISource` 。 `propagate` `ITarget` 如果此來源決定要建立訊息的複本，則傳回的訊息指標可能會與傳入區塊之方法的不同。

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

在衍生類別中覆寫時，接受來源所提供的訊息。 訊息區塊應該覆寫這個方法，以驗證 `_MsgId` 並傳回訊息。

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
物件的執行時間物件識別 `message` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

### <a name="remarks"></a>備註

若要轉移擁有權，應傳回原始訊息指標。 若要維護擁有權，必須提出並傳回訊息承載的複本。

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

取得此物件的參考計數 `source_block` ，以防止刪除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>備註

這個方法是由在 `ITarget` 方法期間連結至此來源的物件所呼叫 `link_target` 。

## <a name="async_send"></a><a name="async_send"></a>async_send

以非同步方式將訊息排入佇列，並啟動傳播工作（如果尚未這麼做）

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
`message`要以非同步方式傳送之物件的指標。

## <a name="consume"></a><a name="consume"></a>占

使用此物件先前提供的訊息 `source_block` ，並由目標成功保留，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `consume` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

如果參數不[bad_target](bad-target-class.md) `_PTarget` 代表呼叫的目標，方法會擲回 bad_target 例外狀況 `reserve` 。

`consume`方法與類似 `accept` ，但一定會在傳回的呼叫前面加上 `reserve` **`true`** 。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

在衍生類別中覆寫時，會使用先前保留的訊息。

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在使用之物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

### <a name="remarks"></a>備註

類似于 `accept` ，但一律會在的呼叫前面加上 `reserve` 。

## <a name="enable_batched_processing"></a><a name="enable_batched_processing"></a>enable_batched_processing

啟用這個區塊的批次處理。

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a><a name="initialize_source"></a>initialize_source

初始化 `message_propagator` 這個中的 `source_block` 。

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
用於排程工作的排程器。

*_PScheduleGroup*<br/>
用於排程工作的排程群組。

## <a name="link_target"></a><a name="link_target"></a>link_target

將目標區塊連結至這個 `source_block` 物件。

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要 `ITarget` 連結至此物件之區塊的指標 `source_block` 。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `source_block` 物件。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

將訊息傳播至目標。

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

在衍生類別中覆寫時，將指定的訊息傳播至任何或所有連結的目標。 這是訊息區塊的主要傳播常式。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要傳播之訊息的指標。

## <a name="release"></a><a name="release"></a>版本

釋放先前成功的訊息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `release` 。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

如果參數不[bad_target](bad-target-class.md) `_PTarget` 代表呼叫的目標，方法會擲回 bad_target 例外狀況 `reserve` 。

## <a name="release_message"></a><a name="release_message"></a>release_message

在衍生類別中覆寫時，釋放先前的訊息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在釋放之物件的。

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

釋放這個物件的參考計數 `source_block` 。

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由與 `ITarget` 此來源取消連結的物件所呼叫。 來源區塊可以釋放為目標區塊保留的任何資源。

## <a name="remove_targets"></a><a name="remove_targets"></a>remove_targets

移除此來源區塊的所有目標連結。 這應該從「析構函式」呼叫。

```cpp
void remove_targets();
```

## <a name="reserve"></a><a name="reserve"></a>留成

保留這個物件先前提供的訊息 `source_block` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `reserve` 。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

在您呼叫之後， `reserve` 如果成功，您必須呼叫 `consume` 或， `release` 以便分別接受或放棄訊息。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

在衍生類別中覆寫時，保留這個物件先前提供的訊息 `source_block` 。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 要保留之物件的。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

`reserve`呼叫之後，如果傳回，則 **`true`** `consume` `release` 必須呼叫或，才能取得或釋放訊息的擁有權。

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

在衍生類別中覆寫時，在釋放保留之後繼續傳播。

```cpp
virtual void resume_propagation() = 0;
```

## <a name="source_block"></a><a name="ctor"></a>source_block

建構 `source_block` 物件。

```cpp
source_block();
```

## <a name="source_block"></a><a name="dtor"></a>~ source_block

終結 `source_block` 物件。

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a><a name="sync_send"></a>sync_send

同步將訊息排入佇列並啟動傳播工作（如果尚未這麼做）。

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
`message`要同步傳送之物件的指標。

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

從這個物件取消目標區塊的與 `source_block`

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要與 `ITarget` 這個物件取消連結之區塊的指標 `source_block` 。

### <a name="remarks"></a>備註

如果參數為，則方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況 `_PTarget` `NULL` 。

## <a name="unlink_target_notification"></a><a name="unlink_target_notification"></a>unlink_target_notification

回呼，會通知目標已從此物件取消連結 `source_block` 。

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
`ITarget`未連結的區塊。

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

從這個物件取消所有目標區塊的 `source_block`

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a><a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

等候所有非同步傳播完成。 這項傳播程式特有的微調等候是用在訊息區塊的析構函數中，以確保所有非同步傳播在終結區塊之前都有時間完成。

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISource 類別](isource-class.md)
