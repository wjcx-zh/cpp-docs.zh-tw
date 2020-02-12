---
title: cancellation_token_registration 類別
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142243"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration 類別

`cancellation_token_registration` 類別表示來自 `cancellation_token` 的回呼通知。 當 `register` 的 `cancellation_token` 方法用來接收發生取消的通知時，則會傳回 `cancellation_token_registration` 物件做為回呼的控制代碼，讓呼叫端可以要求不再透過使用 `deregister` 方法發出的特定回呼。

## <a name="syntax"></a>語法

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration 的析構函式](#dtor)||

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>繼承階層

`cancellation_token_registration`

## <a name="requirements"></a>需求

**標頭：** pplcancellation_token。h

**命名空間：** concurrency

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要複製或移動的 `cancellation_token_registration`。

## <a name="operator_neq"></a>operator！ =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的 `cancellation_token_registration`。

### <a name="return-value"></a>傳回值

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要指派的 `cancellation_token_registration`。

### <a name="return-value"></a>傳回值

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要比較的 `cancellation_token_registration`。

### <a name="return-value"></a>傳回值

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
