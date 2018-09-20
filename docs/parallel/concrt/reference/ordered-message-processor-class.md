---
title: ordered_message_processor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d9340da3665135fc05182bdd6aa6d26c4e2cd76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445876"
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor 類別

`ordered_message_processor` 是 `message_processor`，可讓訊息區塊按照接收順序處理訊息。

## <a name="syntax"></a>語法

```
template<class T>
class ordered_message_processor : public message_processor<T>;
```

#### <a name="parameters"></a>參數

*T*<br/>
處理器處理訊息的裝載類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|類型別名`T`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[ordered_message_processor](#ctor)|建構 `ordered_message_processor` 物件。|
|[~ ordered_message_processor 解構函式](#dtor)|終結`ordered_message_processor`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|非同步訊息排入佇列並啟動的處理工作，如果這已經不做。 (覆寫[message_processor:: async_send](message-processor-class.md#async_send)。)|
|[初始化](#initialize)|初始化`ordered_message_processor`與適當的回呼函式、 排程器和排程群組的物件。|
|[initialize_batched_processing](#initialize_batched_processing)|初始化批次訊息處理|
|[sync_send](#sync_send)|同步訊息排入佇列並啟動的處理工作，如果這已經不做。 (覆寫[message_processor:: sync_send](message-processor-class.md#sync_send)。)|
|[等候](#wait)|特定處理器的旋轉等待，用於訊息區塊的解構函式，以確定所有的非同步處理工作已完成，然後再終結該區塊的時間。 (覆寫[message_processor:: wait](message-processor-class.md#wait)。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|以非同步方式呼叫處理函式。 它會清除佇列訊息，並開始處理它們。 (覆寫[message_processor:: process_incoming_message](message-processor-class.md#process_incoming_message)。)|

## <a name="inheritance-hierarchy"></a>繼承階層

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="async_send"></a> async_send

非同步訊息排入佇列並啟動的處理工作，如果這已經不做。

```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
訊息指標。

##  <a name="initialize"></a> 初始化

初始化`ordered_message_processor`與適當的回呼函式、 排程器和排程群組的物件。

```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>參數

*_PScheduler*<br/>
要用於排程輕量型工作排程器指標。

*_PScheduleGroup*<br/>
排程群組來排程輕量型工作的指標。

*_Handler*<br/>
在回呼期間叫用處理常式的函式。

##  <a name="initialize_batched_processing"></a> initialize_batched_processing

初始化批次訊息處理

```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>參數

*_Processor*<br/>
處理器仿函式叫用回呼時。

*_Propagator*<br/>
傳播程式仿函式叫用回呼時。

##  <a name="ctor"></a> ordered_message_processor

建構 `ordered_message_processor` 物件。

```
ordered_message_processor();
```

### <a name="remarks"></a>備註

這`ordered_message_processor`不會排定同步或非同步處理常式，直到`initialize`呼叫函式。

##  <a name="dtor"></a> ~ordered_message_processor

終結`ordered_message_processor`物件。

```
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>備註

等候所有未完成的非同步作業，然後再終結處理器。

##  <a name="process_incoming_message"></a> process_incoming_message

以非同步方式呼叫處理函式。 它會清除佇列訊息，並開始處理它們。

```
virtual void process_incoming_message();
```

##  <a name="sync_send"></a> sync_send

同步訊息排入佇列並啟動的處理工作，如果這已經不做。

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>參數

*_Msg*<br/>
訊息指標。

##  <a name="wait"></a> 等候

特定處理器的旋轉等待，用於訊息區塊的解構函式，以確定所有的非同步處理工作已完成，然後再終結該區塊的時間。

```
virtual void wait();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
