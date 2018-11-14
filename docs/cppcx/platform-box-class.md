---
title: Platform::Box 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 29cbe852dcd606ea5cf2953c709fc8e47b89e1f1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327027"
---
# <a name="platformbox-class"></a>Platform::Box 類別

允許將實值類型 (例如 `Windows::Foundation::DateTime` ) 或純量類型 (例如 `int` ) 儲存在 `Platform::Object` 類型中。 通常不需要明確使用 `Box` ，因為當您將實值類型轉換成 `Object^`時，將會隱含地進行 Boxing 作業。

### <a name="syntax"></a>語法

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

**命名空間：** Platform

### <a name="members"></a>成員

|成員|描述|
|------------|-----------------|
|[Box](#ctor) | 建立可封裝指定類型之值的 `Box`。 |
|[運算子方塊&lt;const T&gt;^](#box-const-t) | 可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。 |
|[運算子方塊&lt;const volatile T>&gt;^](#box-const-volatile-t) | 可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。 |
|[運算子方塊&lt;T&gt;^](#box-t) | 可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。 |
|[運算子方塊&lt;volatile T&gt;^](#box-volatile-t) | 可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。 |
|[Box:: operator T](#t) | 可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。 |
|[Value 屬性](#value) | 傳回 `Box` 物件中封裝的值。 |

## <a name="ctor"></a> Box:: box 建構函式

建立可封裝指定類型之值的 `Box`。

### <a name="syntax"></a>語法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>參數

*valueArg*<br/>
要處理為 boxed 之值的類型，例如 `int`、`bool`、`float64`、`DateTime`。

## <a name="box-const-t"></a> :: Operator box<const 方塊&lt;const T>&gt;^ 運算子

可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何實值類別、實值結構或列舉類型。 包含中的內建型別[預設命名空間](../cppcx/default-namespace.md)。

### <a name="return-value"></a>傳回值

A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。

## <a name="box-const-volatile-t"></a> :: Operator box<const 方塊&lt;const volatile T>&gt;^ 運算子

可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 包含中的內建型別[預設命名空間](../cppcx/default-namespace.md)。

### <a name="return-value"></a>傳回值

A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。

## <a name="box-t"></a> :: Operator box<const 方塊&lt;T&gt;^ 運算子

可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 包含中的內建型別[預設命名空間](../cppcx/default-namespace.md)。

### <a name="return-value"></a>傳回值

A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。

## <a name="box-volatile-t"></a> :: Operator box<const 方塊&lt;volatile T&gt;^ 運算子

可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 包含中的內建型別[預設命名空間](../cppcx/default-namespace.md)。

### <a name="return-value"></a>傳回值

A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。

## <a name="t"></a>  Box:: operator T 運算子

可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 包含中的內建型別[預設命名空間](../cppcx/default-namespace.md)。

### <a name="return-value"></a>傳回值

A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。

## <a name="value"></a> Box:: value 屬性

傳回 `Box` 物件中封裝的值。

### <a name="syntax"></a>語法

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>傳回值

傳回 Boxed 值，與該值進行 Boxed 處理之前的原始類型相同。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)