---
title: call 類別
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: 445e368ced9d9c8faf30351ecaeecc4e1b8a59f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142841"
---
# <a name="call-class"></a>call 類別

`call` 傳訊區塊是一個多來源的排序 `target_block`，它在接收訊息時會叫用指定的函式。

## <a name="syntax"></a>語法

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>參數

*T*<br/>
傳播至此區塊之訊息的裝載類型。

*_FunctorType*<br/>
此區塊可以接受之函式的簽章。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[拜訪](#ctor)|已多載。 建構 `call` 傳訊區塊。|
|[~ 呼叫析構函式](#dtor)|損毀 `call` 訊息區塊。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|在輸入訊息上執行 call 函數。|
|[process_message](#process_message)|處理此 `call` 訊息區塊所接受的訊息。|
|[propagate_message](#propagate_message)|以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。|
|[send_message](#send_message)|以同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。|
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 （覆寫[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="ctor"></a>拜訪

建構 `call` 傳訊區塊。

```cpp
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>參數

*_Func*<br/>
會針對每個接受的訊息叫用的函式。

*_Filter*<br/>
篩選函數，決定是否應接受所提供的訊息。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `call` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `call` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

類型 `_Call_method` 是具有簽章 `void (T const &)` 的仿函數，此 `call` 訊息區塊會叫用此方法來處理訊息。

類型 `filter_method` 是具有簽章 `bool (T const &)` 的仿函數，此 `call` 訊息區塊會叫用此方法，以判斷是否應該接受提供的訊息。

## <a name="dtor"></a>~ 呼叫

損毀 `call` 訊息區塊。

```cpp
~call();
```

## <a name="process_input_messages"></a>process_input_messages

在輸入訊息上執行 call 函數。

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="process_message"></a>process_message

處理此 `call` 訊息區塊所接受的訊息。

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
要處理之訊息的指標。

## <a name="propagate_message"></a>propagate_message

以非同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 的訊息區塊。 它是由來源區塊呼叫時，由 `propagate` 方法叫用。

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

## <a name="send_message"></a>send_message

以同步方式將訊息從 `ISource` 區塊傳遞到這個 `call` 的訊息區塊。 它是由來源區塊呼叫時，由 `send` 方法叫用。

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

## <a name="supports_anonymous_source"></a>supports_anonymous_source

覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**true** ，因為區塊不會延後提供的訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[transformer 類別](transformer-class.md)
