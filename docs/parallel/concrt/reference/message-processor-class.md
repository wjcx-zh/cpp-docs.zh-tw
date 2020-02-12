---
title: message_processor 類別
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: 88944b2d935eebd0e031be1431c2a0f4efa3d760
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139474"
---
# <a name="message_processor-class"></a>message_processor 類別

`message_processor` 類別是處理 `message` 物件的抽象基底類別。 訊息順序方面沒有一定的保證。

## <a name="syntax"></a>語法

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>參數

*T*<br/>
這個 `message_processor` 物件所處理之訊息內裝載的資料類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|`T`的類型別名。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|在衍生類別中覆寫時，會以非同步方式將訊息放入區塊中。|
|[sync_send](#sync_send)|在衍生類別中覆寫時，會以同步方式將訊息放入區塊中。|
|[等候](#wait)|在衍生類別中覆寫時，等候所有非同步作業完成。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|在衍生類別中覆寫時，執行訊息到區塊中的正向處理。 每次新增新訊息，且發現佇列為空白時呼叫一次。|

## <a name="inheritance-hierarchy"></a>繼承階層

`message_processor`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="async_send"></a>async_send

在衍生類別中覆寫時，會以非同步方式將訊息放入區塊中。

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>參數

*_Msg*<br/>
要以非同步方式傳送的 `message` 物件。

### <a name="remarks"></a>備註

處理器的執行應該覆寫此方法。

## <a name="process_incoming_message"></a>process_incoming_message

在衍生類別中覆寫時，執行訊息到區塊中的正向處理。 每次新增新訊息，且發現佇列為空白時呼叫一次。

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>備註

訊息區塊的執行應該會覆寫這個方法。

## <a name="sync_send"></a>sync_send

在衍生類別中覆寫時，會以同步方式將訊息放入區塊中。

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>參數

*_Msg*<br/>
要以同步方式傳送的 `message` 物件。

### <a name="remarks"></a>備註

處理器的執行應該覆寫此方法。

## <a name="wait"></a>等候

在衍生類別中覆寫時，等候所有非同步作業完成。

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>備註

處理器的執行應該覆寫此方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ordered_message_processor 類別](ordered-message-processor-class.md)
