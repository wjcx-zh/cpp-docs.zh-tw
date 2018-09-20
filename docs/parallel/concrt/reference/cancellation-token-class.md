---
title: cancellation_token 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9b438725a5a725597a81f0587936618a06cbb4b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414299"
---
# <a name="cancellationtoken-class"></a>cancellation_token 類別

`cancellation_token` 類別表示可判斷某個作業是否已要求取消的能力。 特定語彙基元可以與 `task_group`、`structured_task_group` 或 `task` 產生關聯，來提供隱含取消作業。 如果與相關聯的 `cancellation_token_source` 已取消，也可以向它輪詢取消，或為它註冊回呼。

## <a name="syntax"></a>語法

```
class cancellation_token;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token 解構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|根據註冊時傳回的 `register` 物件，移除先前透過 `cancellation_token_registration` 方法註冊的回呼。|
|[is_cancelable](#is_cancelable)|傳回這個語彙基元是否可以取消的指示。|
|[is_canceled](#is_canceled)|如果語彙基元已取消，則傳回 `true`。|
|[none](#none)|傳回永不需取消的取消語彙基元。|
|[register_callback](#register_callback)|使用語彙基元註冊回呼函式。 如果這個語彙基元已取消，將會進行回呼。 請注意，如果語彙基元已經在呼叫此方法的時間點取消，將會立即同步進行回呼。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>繼承階層

`cancellation_token`

## <a name="requirements"></a>需求

**標頭：** pplcancellation_token.h

**命名空間：** concurrency

##  <a name="dtor"></a> ~ cancellation_token

```
~cancellation_token();
```

##  <a name="ctor"></a> cancellation_token

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要複製或移動 cancellation_token。

##  <a name="deregister_callback"></a> deregister_callback

根據註冊時傳回的 `register` 物件，移除先前透過 `cancellation_token_registration` 方法註冊的回呼。

```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>參數

*_Registration*<br/>
`cancellation_token_registration` 物件，對應於要取消註冊的回呼。 這個語彙基元必須已經由 `register` 方法呼叫所傳回。

##  <a name="is_cancelable"></a> is_cancelable

傳回這個語彙基元是否可以取消的指示。

```
bool is_cancelable() const;
```

### <a name="return-value"></a>傳回值

表示這個語彙基元是否可以取消。

##  <a name="is_canceled"></a> is_canceled

如果語彙基元已取消，則傳回 `true`。

```
bool is_canceled() const;
```

### <a name="return-value"></a>傳回值

如果語彙基元被取消，則為 `true` 值，否則為 `false` 值。

##  <a name="none"></a> None

傳回永不需取消的取消語彙基元。

```
static cancellation_token none();
```

### <a name="return-value"></a>傳回值

無法取消的取消語彙基元。

##  <a name="operator_neq"></a> 運算子 ！ =

```
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>參數

*_Src*<br/>
要比較的 `cancellation_token`。

### <a name="return-value"></a>傳回值

##  <a name="operator_eq"></a> 運算子 =

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
`cancellation_token`指派。

### <a name="return-value"></a>傳回值

##  <a name="operator_eq_eq"></a> 運算子 = =

```
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>參數

*_Src*<br/>
要比較的 `cancellation_token`。

### <a name="return-value"></a>傳回值

##  <a name="register_callback"></a> register_callback

使用語彙基元註冊回呼函式。 如果這個語彙基元已取消，將會進行回呼。 請注意，如果語彙基元已經在呼叫此方法的時間點取消，將會立即同步進行回呼。

```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>參數

*_Function*<br/>
當取消這個 `cancellation_token` 時，會被回呼的函式物件的類型。

*_Func*<br/>
當取消這個 `cancellation_token` 時，會被回呼的函式物件。

### <a name="return-value"></a>傳回值

`cancellation_token_registration` 物件，可在 `deregister` 方法中用來取消註冊先前註冊的回呼，並防止進行此回呼。 方法會擲回[invalid_operation](invalid-operation-class.md)如果已呼叫方法的例外狀況`cancellation_token`使用所建立的物件[invalid_operation](#none)方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
