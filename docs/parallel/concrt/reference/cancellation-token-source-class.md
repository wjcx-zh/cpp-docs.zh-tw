---
title: cancellation_token_source 類別
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 131c4155ad902221d14f90f750f89c31479e2067
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142223"
---
# <a name="cancellation_token_source-class"></a>cancellation_token_source 類別

`cancellation_token_source` 類別代表取消某個可取消作業的能力。

## <a name="syntax"></a>語法

```cpp
class cancellation_token_source;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[cancellation_token_source](#ctor)|已多載。 建構新 `cancellation_token_source`。 來源可用於將某個可取消作業的取消加上標幟。|
|[~ cancellation_token_source 的析構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[cancel](#cancel)|取消語彙基元。 任何使用語彙基元的 `task_group`、`structured_task_group` 或 `task` 都會在進行這個呼叫時取消，並在下一個中斷點擲回例外狀況。|
|[create_linked_source](#create_linked_source)|已多載。 建立 `cancellation_token_source`，其會在提供的語彙基元已取消時取消。|
|[get_token](#get_token)|傳回與此來源相關聯的取消語彙基元。 傳回的語彙基元可用於輪詢取消或在發生取消時提供回呼。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>繼承階層

`cancellation_token_source`

## <a name="requirements"></a>需求

**標頭：** pplcancellation_token。h

**命名空間：** concurrency

## <a name="dtor"></a>~ cancellation_token_source

```cpp
~cancellation_token_source();
```

## <a name="cancel"></a>取消

取消語彙基元。 任何使用語彙基元的 `task_group`、`structured_task_group` 或 `task` 都會在進行這個呼叫時取消，並在下一個中斷點擲回例外狀況。

```cpp
void cancel() const;
```

## <a name="ctor"></a>cancellation_token_source

建構新 `cancellation_token_source`。 來源可用於將某個可取消作業的取消加上標幟。

```cpp
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要複製或移動的物件。

## <a name="create_linked_source"></a>create_linked_source

建立 `cancellation_token_source`，其會在提供的語彙基元已取消時取消。

```cpp
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>參數

*_Iter*<br/>
Iterator 類型。

*_Src*<br/>
語彙基元，其取消作業將會導致取消傳回的語彙基元來源。 請注意，傳回的語彙基元來源也可以獨立取消，不受此參數包含的來源影響。

*_Begin*<br/>
C++標準程式庫反覆運算器，對應至要接聽取消之標記範圍的開頭。

*_End*<br/>
C++標準程式庫反覆運算器，對應至要接聽取消之標記範圍的結尾。

### <a name="return-value"></a>傳回值

`cancellation_token_source`，其會在 `_Src` 參數提供的語彙基元已取消時取消。

## <a name="get_token"></a>get_token

傳回與此來源相關聯的取消語彙基元。 傳回的語彙基元可用於輪詢取消或在發生取消時提供回呼。

```cpp
cancellation_token get_token() const;
```

### <a name="return-value"></a>傳回值

與此來源相關聯的取消語彙基元。

## <a name="operator_neq"></a>operator！ =

```cpp
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>參數

*_Src*<br/>
運算元.

### <a name="return-value"></a>傳回值

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
運算元.

### <a name="return-value"></a>傳回值

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>參數

*_Src*<br/>
運算元.

### <a name="return-value"></a>傳回值

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
