---
title: SafeInt 函式
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: c1c5593aee19254d4348d4e8658ffe9c3f0cf1b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368244"
---
# <a name="safeint-functions"></a>SafeInt 函式

SafeInt 程式庫提供幾個您不需要建立 [SafeInt 類別](../safeint/safeint-class.md)的執行個體就能使用的函式。 如果想要保護單一數學運算防止發生整數溢位，就可以使用這些函式。 如果想要保護多個數學運算，則應建立 `SafeInt` 物件。 建立 `SafeInt` 物件會比多次使用這些函式更有效率。

這些函式可讓您在兩個不同型別的參數上，比較或執行數學運算，不需要先將它們轉換成相同型別。

這些函式每一個都有兩種範本型別：`T` 和 `U`。 每一種型別都可以是布林值、字元或整數型別。 整數型別不一定要帶正負號，且大小從 8 位元到 64 位元均可。

> [!NOTE]
> 此函式庫的最新[https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)版本 。

## <a name="in-this-section"></a>本節內容

函式                      | 描述
----------------------------- | --------------------------------------------------------------
[安全新增](#safeadd)           | 可將兩個數字相加並防止溢位。
[安全廣播](#safecast)         | 可將某個型別的參數轉換成另一種型別。
[安全分流](#safedivide)     | 可將兩個數字相除並防止將它們除以零。
[SafeEquals](#safeequals)、[SafeGreaterThan](#safegreaterthan)、[SafeGreaterThanEquals](#safegreaterthanequals)、[SafeLessThan](#safelessthan)、[SafeLessThanEquals](#safelessthanequals)、[SafeNotEquals](#safenotequals) | 比較兩個數字。 這些函式可讓您比較兩種不同型別的數字，而不需要變更它們的型別。
[安全性Modulus](#safemodulus)   | 可在兩個數字上執行模數運算。
[安全乘法](#safemultiply) | 可將兩個數字相乘並防止溢位。
[安全減法](#safesubtract) | 可將兩個數字相減並防止溢位。

## <a name="related-sections"></a>相關章節

區段                                                  | 描述
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | `SafeInt` 類別。
[SafeIntException](../safeint/safeintexception-class.md) | SafeInt 程式庫特定的例外狀況類別。

## <a name="safeadd"></a><a name="safeadd"></a>安全新增

可透過防止溢位的方式將兩個數字相加。

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要相加的第一個數字。 這必須為類型 T。

*u*<br/>
[in] 要相加的第二個數字。 這必須為類型 U。

*result*<br/>
[out] `SafeAdd` 儲存結果的參數。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 **true**；如果發生錯誤則為 **false**。

## <a name="safecast"></a><a name="safecast"></a>安全廣播

可將某個型別的數字轉換成另一種型別。

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>參數

*從*<br/>
[in] 要轉換的來源數字。 它必須是 `T` 型別。

*自*<br/>
[out] 對新數字型別的參考。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 **true**；如果發生錯誤則為 **false**。

## <a name="safedivide"></a><a name="safedivide"></a>安全分流

可透過防止除以零的方式將兩個數字相除。

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 除數。 這必須為類型 T。

*u*<br/>
[in] 被除數。 這必須為類型 U。

*result*<br/>
[out] `SafeDivide` 儲存結果的參數。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 **true**；如果發生錯誤則為 **false**。

## <a name="safeequals"></a><a name="safeequals"></a>安全平等

比較兩個數字以判斷它們是否相等。

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要比較的第一個數字。 這必須為類型 T。

*u*<br/>
[in] 要比較的第二個數字。 這必須為類型 U。

### <a name="return-value"></a>傳回值

如果 *t* 與 *u* 相等，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

因為 `==` 可讓您比較兩種不同類型的數字，所以此方法會增強 `SafeEquals`。

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>安全大於

比較兩個數字。

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要比較的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要比較的第二個數字。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果 *t* 大於 *u*，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

`SafeGreaterThan` 可透過讓您比較兩個不同型別的數字，來延伸一般比較運算子。

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>安全大於均等

比較兩個數字。

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要比較的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要比較的第二個數字。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果 *t* 大於或等於 *u*，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

`SafeGreaterThanEquals` 可增強標準比較運算子，因為它可以讓您比較兩個不同型別的數字。

## <a name="safelessthan"></a><a name="safelessthan"></a>安全不點

可判斷某個數字是否小於另一個。

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 第二個數字。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果 *t* 小於 *u*，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

此方法可增強標準比較運算子，因為 `SafeLessThan` 可以讓您比較兩個不同型別的數字。

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>安全不相等

比較兩個數字。

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要比較的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要比較的第二個數字。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果 *t* 小於或等於 *u*，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

`SafeLessThanEquals` 可透過讓您比較兩個不同型別的數字，來延伸一般比較運算子。

## <a name="safemodulus"></a><a name="safemodulus"></a>安全性Modulus

可在兩個數字上執行模數運算。

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 除數。 它必須是 `T` 型別。

*u*<br/>
[in] 被除數。 它必須是 `U` 型別。

*result*<br/>
[out] `SafeModulus` 儲存結果的參數。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 **true**；如果發生錯誤則為 **false**。

## <a name="safemultiply"></a><a name="safemultiply"></a>安全乘法

可透過防止溢位的方式將兩個數字相乘。

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要相乘的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要相乘的第二個數字。 它必須是 `U` 型別。

*result*<br/>
[out] `SafeMultiply` 儲存結果的參數。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 `true`；發生錯誤則為 `false`。

## <a name="safenotequals"></a><a name="safenotequals"></a>安全不相等

判斷兩個數字是否不相等。

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 要比較的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要比較的第二個數字。 它必須是 `U` 型別。

### <a name="return-value"></a>傳回值

如果 *t* 與 *u* 不相等，為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

因為 `!=` 可讓您比較兩種不同類型的數字，所以此方法會增強 `SafeNotEquals`。

## <a name="safesubtract"></a><a name="safesubtract"></a>安全減法

可透過防止溢位的方式將兩個數字相減。

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in] 減法中的第一個數字。 它必須是 `T` 型別。

*u*<br/>
[in] 要從 *t* 中減去的數字。 它必須是 `U` 型別。

*result*<br/>
[out] `SafeSubtract` 儲存結果的參數。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤為 **true**；如果發生錯誤則為 **false**。
