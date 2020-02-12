---
title: message 類別
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139534"
---
# <a name="message-class"></a>message 類別

基本訊息封套，其中包含在傳訊區塊之間傳遞的資料承載。

## <a name="syntax"></a>語法

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>參數

*T*<br/>
訊息內裝載的資料類型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

|名字|描述|
|----------|-----------------|
|`type`|`T`的類型別名。|

### <a name="public-constructors"></a>公用建構函式

|名字|描述|
|----------|-----------------|
|[message](#ctor)|多載。 建構 `message` 物件。|
|[~ 訊息的析構函式](#dtor)|終結 `message` 物件。|

### <a name="public-methods"></a>公用方法

|名字|描述|
|----------|-----------------|
|[add_ref](#add_ref)|將加入至 `message` 物件的參考計數。 用於需要參考計數的訊息區塊，以判斷訊息存留期。|
|[msg_id](#msg_id)|傳回 `message` 物件的識別碼。|
|[remove_ref](#remove_ref)|從 `message` 物件的參考計數減去。 用於需要參考計數的訊息區塊，以判斷訊息存留期。|

### <a name="public-data-members"></a>公用資料成員

|名字|描述|
|----------|-----------------|
|[payload](#payload)|`message` 物件的承載。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`message`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="add_ref"></a>add_ref

將加入至 `message` 物件的參考計數。 用於需要參考計數的訊息區塊，以判斷訊息存留期。

```cpp
long add_ref();
```

### <a name="return-value"></a>傳回值

參考計數的新值。

## <a name="ctor"></a>消息

建構 `message` 物件。

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>參數

*_P*<br/>
此訊息的裝載。

*_Id*<br/>
這個訊息的唯一 ID。

*_Msg*<br/>
`message` 物件的參考或指標。

### <a name="remarks"></a>備註

如果 `NULL`參數 `_Msg`，接受 `message` 物件之指標當做引數的函式會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

## <a name="dtor"></a>~ 訊息

終結 `message` 物件。

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

傳回 `message` 物件的識別碼。

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>傳回值

`runtime_object_identity` 物件的 `message`。

## <a name="payload"></a>作用

`message` 物件的承載。

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

從 `message` 物件的參考計數減去。 用於需要參考計數的訊息區塊，以判斷訊息存留期。

```cpp
long remove_ref();
```

### <a name="return-value"></a>傳回值

參考計數的新值。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
