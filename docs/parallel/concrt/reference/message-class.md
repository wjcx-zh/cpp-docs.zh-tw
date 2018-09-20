---
title: message 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
dev_langs:
- C++
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5acca6c01b41b34c17aa5e7f949b9dab94362fa2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400948"
---
# <a name="message-class"></a>message 類別

基本訊息封套，其中包含在傳訊區塊之間傳遞的資料承載。

## <a name="syntax"></a>語法

```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

#### <a name="parameters"></a>參數

*T*<br/>
訊息內裝載的資料型別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|類型別名`T`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[message](#ctor)|多載。 建構 `message` 物件。|
|[~ message 解構函式](#dtor)|終結`message`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[add_ref](#add_ref)|將加入的參考計數`message`物件。 用於需要參考計數來判斷訊息的存留期的訊息區塊。|
|[msg_id](#msg_id)|傳回的識別碼`message`物件。|
|[remove_ref](#remove_ref)|參考計數中減去`message`物件。 用於需要參考計數來判斷訊息的存留期的訊息區塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[承載](#payload)|承載`message`物件。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`message`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="add_ref"></a> add_ref

將加入的參考計數`message`物件。 用於需要參考計數來判斷訊息的存留期的訊息區塊。

```
long add_ref();
```

### <a name="return-value"></a>傳回值

參考計數的新值。

##  <a name="ctor"></a> 訊息

建構 `message` 物件。

```
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
此訊息的承載。

*識別碼 （_i)*<br/>
這個訊息的唯一 ID。

*_Msg*<br/>
參考或指標`message`物件。

### <a name="remarks"></a>備註

使用變數的指標，建構函式`message`物件的引數會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_Msg`是`NULL`。

##  <a name="dtor"></a> ~ 訊息

終結`message`物件。

```
virtual ~message();
```

##  <a name="msg_id"></a> msg_id

傳回的識別碼`message`物件。

```
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>傳回值

`runtime_object_identity`的`message`物件。

##  <a name="payload"></a> 承載

承載`message`物件。

```
T const payload;
```

##  <a name="remove_ref"></a> remove_ref

參考計數中減去`message`物件。 用於需要參考計數來判斷訊息的存留期的訊息區塊。

```
long remove_ref();
```

### <a name="return-value"></a>傳回值

參考計數的新值。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
