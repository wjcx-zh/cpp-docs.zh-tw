---
title: Platform::Box 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 6afc12dbc3f6980bb7fd42d7f0a8fdc9e6d0e284
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232166"
---
# <a name="platformbox-class"></a>Platform::Box 類別

讓實值型別（例如）或純量 `Windows::Foundation::DateTime` 型別（例如） **`int`** 儲存在型別中 `Platform::Object` 。 通常不需要明確使用 `Box` ，因為當您將實值類型轉換成 `Object^`時，將會隱含地進行 Boxing 作業。

### <a name="syntax"></a>語法

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

**命名空間：** Platform

### <a name="members"></a>成員

|成員|說明|
|------------|-----------------|
|[Box](#ctor) | 建立可封裝指定類型之值的 `Box`。 |
|[運算子 Box &lt; Const T&gt;^](#box-const-t) | 啟用從實 **`const`** 值類別 `T` 或 **`enum`** 類別到的 `T` 裝箱轉換 `Box<T>` 。 |
|[運算子 Box &lt; const Volatile T&gt;^](#box-const-volatile-t) | 啟用從實 **`const volatile`** 值類別 `T` 或 **`enum`** 類型到的 `T` 裝箱轉換 `Box<T>` 。 |
|[運算子方塊 &lt; T&gt;^](#box-t) | 可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。 |
|[運算子 Box &lt; Volatile T&gt;^](#box-volatile-t) | 啟用從實 **`volatile`** 值類別 `T` 或 **`enum`** 類型到的 `T` 裝箱轉換 `Box<T>` 。 |
|[Box：： operator T](#t) | 啟用從實值類別 `T` 或類別到的裝箱轉換 **`enum`** `T` `Box<T>` 。 |
|[Value 屬性](#value) | 傳回 `Box` 物件中封裝的值。 |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box：： Box 函數

建立可封裝指定類型之值的 `Box`。

### <a name="syntax"></a>語法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>參數

*valueArg*<br/>
要進行裝箱的數值型別，例如、、 **`int`** **`bool`** `float64` 、 `DateTime` 。

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box：： operator Box &lt; Const T &gt; ^ 運算子

啟用從實 **`const`** 值類別 `T` 或 **`enum`** 類別到的 `T` 裝箱轉換 `Box<T>` 。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何實值類別、實值結構或列舉類型。 在[預設命名空間](../cppcx/default-namespace.md)中包含內建類型。

### <a name="return-value"></a>傳回值

`Platform::Box<T>^`實例，表示 ref 類別中所裝箱的原始值。

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box：： operator Box &lt; const Volatile T- &gt; ^ 運算子

啟用從實 **`const volatile`** 值類別 `T` 或 **`enum`** 類型到的 `T` 裝箱轉換 `Box<T>` 。

### <a name="syntax"></a>語法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包含內建類型。

### <a name="return-value"></a>傳回值

`Platform::Box<T>^`實例，表示 ref 類別中所裝箱的原始值。

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box：： operator Box &lt; T &gt; ^ 運算子

可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。

### <a name="syntax"></a>語法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包含內建類型。

### <a name="return-value"></a>傳回值

`Platform::Box<T>^`實例，表示 ref 類別中所裝箱的原始值。

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box：： operator Box &lt; Volatile T &gt; ^ 運算子

啟用從實 **`volatile`** 值類別 `T` 或 **`enum`** 類型到的 `T` 裝箱轉換 `Box<T>` 。

### <a name="syntax"></a>語法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包含內建類型。

### <a name="return-value"></a>傳回值

`Platform::Box<T>^`實例，表示 ref 類別中所裝箱的原始值。

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box：： operator T 運算子

啟用從實值類別 `T` 或類別到的裝箱轉換 **`enum`** `T` `Box<T>` 。

### <a name="syntax"></a>語法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>參數

*T*<br/>
任何列舉類型、實值類別或實值結構。 在[預設命名空間](../cppcx/default-namespace.md)中包含內建類型。

### <a name="return-value"></a>傳回值

`Platform::Box<T>^`實例，表示 ref 類別中所裝箱的原始值。

## <a name="boxvalue-property"></a><a name="value"></a>Box：： Value 屬性

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
[Box 處理](../cppcx/boxing-c-cx.md)
