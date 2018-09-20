---
title: message_processor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3ff478b4471916fb51931ea59712be0d47d2b61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404029"
---
# <a name="messageprocessor-class"></a>message_processor 類別

`message_processor` 類別是處理 `message` 物件的抽象基底類別。 訊息順序方面沒有一定的保證。

## <a name="syntax"></a>語法

```
template<class T>
class message_processor;
```

#### <a name="parameters"></a>參數

*T*<br/>
訊息內裝載的資料型別由這個`message_processor`物件。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|類型別名`T`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[async_send](#async_send)|在衍生類別中覆寫時，會放在訊息成區塊以非同步的方式。|
|[sync_send](#sync_send)|在衍生類別中覆寫時，會放在訊息成區塊以同步方式。|
|[等候](#wait)|當在衍生類別中覆寫時，等候所有完成的非同步作業。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|當在衍生類別中覆寫時，會執行正向的訊息處理成區塊。 每次新增了新的訊息，並發現佇列是空的請呼叫一次。|

## <a name="inheritance-hierarchy"></a>繼承階層

`message_processor`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="async_send"></a> async_send

在衍生類別中覆寫時，會放在訊息成區塊以非同步的方式。

```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>參數

*_Msg*<br/>
A`message`以非同步方式傳送的物件。

### <a name="remarks"></a>備註

處理器實作應該覆寫這個方法。

##  <a name="process_incoming_message"></a> process_incoming_message

當在衍生類別中覆寫時，會執行正向的訊息處理成區塊。 每次新增了新的訊息，並發現佇列是空的請呼叫一次。

```
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>備註

訊息區塊的實作應該覆寫這個方法。

##  <a name="sync_send"></a> sync_send

在衍生類別中覆寫時，會放在訊息成區塊以同步方式。

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>參數

*_Msg*<br/>
A`message`以同步方式傳送的物件。

### <a name="remarks"></a>備註

處理器實作應該覆寫這個方法。

##  <a name="wait"></a> 等候

當在衍生類別中覆寫時，等候所有完成的非同步作業。

```
virtual void wait() = 0;
```

### <a name="remarks"></a>備註

處理器實作應該覆寫這個方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ordered_message_processor 類別](ordered-message-processor-class.md)
