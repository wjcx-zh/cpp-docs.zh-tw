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
ms.openlocfilehash: c65eed8abafe424fa27c5b9a72d3c73b7127b68e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219582"
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
這種類型的 `join` 區塊為，也就是 `greedy` 或`non_greedy`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[join](#ctor)|已多載。 建構 `join` 傳訊區塊。|
|[~ 聯結析構函式](#dtor)|損毀 `join` 區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此訊息區塊所提供的訊息 `join` ，並將擁有權轉移給呼叫者。|
|[consume_message](#consume_message)|取用 `join` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。|
|[link_target_notification](#link_target_notification)|回呼，會通知新的目標已連結至此 `join` 訊息區塊。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞至此 `join` 訊息區塊。 `propagate`當由來源區塊呼叫時，方法會叫用它。|
|[propagate_to_any_targets](#propagate_to_any_targets)|當每個來源的輸入訊息全部傳播一則訊息時，就會建立輸出訊息。 將輸出訊息傳送給它的每個目標。|
|[release_message](#release_message)|釋放先前的訊息保留。 （覆寫[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此訊息區塊先前提供的訊息 `join` 。 （覆寫[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|在發行保留專案之後繼續傳播。 （覆寫[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此訊息區塊所提供的訊息 `join` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

取用 `join` 訊息區塊先前提供並由目標保留的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在使用之物件的。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

類似于 `accept` ，但一律會在的呼叫前面加上 `reserve` 。

## <a name="join"></a><a name="ctor"></a>接入

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
將允許此區塊的輸入數目 `join` 。

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `join` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型是具有簽章的 `filter_method` 仿函數， `bool (T const &)` 此訊息區塊會叫用該簽章， `join` 以判斷它是否應該接受提供的訊息。

## <a name="join"></a><a name="dtor"></a>~ 聯結

損毀 `join` 區塊。

```cpp
~join();
```

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

回呼，會通知新的目標已連結至此 `join` 訊息區塊。

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞至此 `join` 訊息區塊。 `propagate`當由來源區塊呼叫時，方法會叫用它。

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

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

當每個來源的輸入訊息全部傳播一則訊息時，就會建立輸出訊息。 將輸出訊息傳送給它的每個目標。

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

釋放先前的訊息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在釋放之物件的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此訊息區塊先前提供的訊息 `join` 。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

`reserve`呼叫之後，如果傳回，則 **`true`** `consume` `release` 必須呼叫或，才能取得或釋放訊息的擁有權。

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

在發行保留專案之後繼續傳播。

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[choice 類別](choice-class.md)<br/>
[multitype_join 類別](multitype-join-class.md)
