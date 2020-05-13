---
title: Platform::Box 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354752"
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

|member|描述|
|------------|-----------------|
|[Box](#ctor) | 建立可封裝指定類型之值的 `Box`。 |
|[運算子盒&lt;形 T&gt;^](#box-const-t) | 可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。 |
|[運算子&lt;盒收縮揮發 T&gt;^](#box-const-volatile-t) | 可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。 |
|[操作員盒&lt;T&gt;^](#box-t) | 可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。 |
|[運算子&lt;盒揮發 T&gt;^](#box-volatile-t) | 可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。 |
|[框::運算子 T](#t) | 可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。 |
|[值屬性](#value) | 傳回 `Box` 物件中封裝的值。 |

## <a name="boxbox-constructor"></a><a name="ctor"></a>框::框建構函數

建立可封裝指定類型之值的 `Box`。

### <a name="syntax"></a>語法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>參數

*值阿格*<br/>
要處理為 boxed 之值的類型，例如 `int`、`bool`、`float64`、`DateTime`。

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>框::運算子盒&lt;同&gt;T = 運算子

可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何實值類別、實值結構或列舉類型。 在[預設命名空間](../cppcx/default-namespace.md)中包括內建類型。

### <a name="return-value"></a>傳回值

表示`Platform::Box<T>^`在 ref 類中裝箱的原始值的實例。

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>框::運算符盒&lt;收縮揮發性&gt;T = 運算子

可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包括內建類型。

### <a name="return-value"></a>傳回值

表示`Platform::Box<T>^`在 ref 類中裝箱的原始值的實例。

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>框::運算子框&lt;&gt;T = 運算子

可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包括內建類型。

### <a name="return-value"></a>傳回值

表示`Platform::Box<T>^`在 ref 類中裝箱的原始值的實例。

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>框::運算符框&lt;揮發&gt;T = 運算子

可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包括內建類型。

### <a name="return-value"></a>傳回值

表示`Platform::Box<T>^`在 ref 類中裝箱的原始值的實例。

## <a name="boxoperator-t-operator"></a><a name="t"></a>框::運算子 T 運算子

可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包括內建類型。

### <a name="return-value"></a>傳回值

表示`Platform::Box<T>^`在 ref 類中裝箱的原始值的實例。

## <a name="boxvalue-property"></a><a name="value"></a>框::值屬性

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

[平台命名空間](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
