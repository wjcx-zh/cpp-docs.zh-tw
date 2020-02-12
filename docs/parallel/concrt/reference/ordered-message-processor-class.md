---
title: ordered_message_processor 類別
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138789"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor 類別

`ordered_message_processor` 是 `message_processor`，可讓訊息區塊按照接收順序處理訊息。

## <a name="syntax"></a>語法

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>參數

*T*<br/>
處理器所處理之訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|`T`的類型別名。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[ordered_message_processor](#ctor)|建構 `ordered_message_processor` 物件。|
|[~ ordered_message_processor 的析構函式](#dtor)|終結 `ordered_message_processor` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|以非同步方式將訊息排入佇列並啟動處理工作（如果尚未這麼做）。 （覆寫[message_processor：： async_send](message-processor-class.md#async_send)。）|
|[格式化](#initialize)|使用適當的回呼函式、排程器和排程群組，初始化 `ordered_message_processor` 物件。|
|[initialize_batched_processing](#initialize_batched_processing)|初始化批次訊息處理|
|[sync_send](#sync_send)|同步將訊息排入佇列並啟動處理工作（如果尚未這麼做）。 （覆寫[message_processor：： sync_send](message-processor-class.md#sync_send)。）|
|[等候](#wait)|在訊息區塊的析構函數中使用的處理器特定微調等候，以確保所有非同步處理工作在終結區塊之前都有時間完成。 （覆寫[message_processor：： wait](message-processor-class.md#wait)。）|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|以非同步方式呼叫的處理函式。 它會清除訊息並開始處理。 （覆寫[message_processor：:p rocess_incoming_message](message-processor-class.md#process_incoming_message)）。|

## <a name="inheritance-hierarchy"></a>繼承階層

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="async_send"></a>async_send

以非同步方式將訊息排入佇列並啟動處理工作（如果尚未這麼做）。

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
訊息的指標。

## <a name="initialize"></a>格式化

使用適當的回呼函式、排程器和排程群組，初始化 `ordered_message_processor` 物件。

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
要用於排程輕量工作的排程器指標。

*_PScheduleGroup*<br/>
要用於排程輕量工作的排程群組指標。

*_Handler*<br/>
回呼期間叫用的處理常式仿函數。

## <a name="initialize_batched_processing"></a>initialize_batched_processing

初始化批次訊息處理

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>參數

*_Processor*<br/>
回呼期間叫用的處理器仿函數。

*_Propagator*<br/>
在回呼期間叫用的傳播仿函數。

## <a name="ctor"></a>ordered_message_processor

建構 `ordered_message_processor` 物件。

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>備註

這個 `ordered_message_processor` 在呼叫 `initialize` 函數之前，不會排程非同步或同步處理常式。

## <a name="dtor"></a>~ ordered_message_processor

終結 `ordered_message_processor` 物件。

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>備註

在終結處理器之前，等候所有未完成的非同步作業。

## <a name="process_incoming_message"></a>process_incoming_message

以非同步方式呼叫的處理函式。 它會清除訊息並開始處理。

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

同步將訊息排入佇列並啟動處理工作（如果尚未這麼做）。

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
訊息的指標。

## <a name="wait"></a>等候

在訊息區塊的析構函數中使用的處理器特定微調等候，以確保所有非同步處理工作在終結區塊之前都有時間完成。

```cpp
virtual void wait();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
