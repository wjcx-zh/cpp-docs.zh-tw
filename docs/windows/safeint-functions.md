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
ms.openlocfilehash: 0cf1418e3bf00c037faaa67de2bc76ad2b7cc5e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578395"
---
# <a name="safeint-functions"></a>SafeInt 函式

SafeInt 程式庫提供數個您可以使用而建立的執行個體的函數[SafeInt 類別](../windows/safeint-class.md)。 如果您想要保護單一數學作業從整數的溢位時，您可以使用這些函式。 如果您想要保護多個數學運算，您應該建立`SafeInt`物件。 若要建立更有效率`SafeInt`比使用這些函式多次的物件。

這些功能可讓您比較，或執行而不需要先將它們轉換成相同類型的兩個不同類型的參數上的數學運算。

所有這些函式有兩種範本類型：`T`和`U`。 每一種類型可以是布林值、 字元或整數類資料類型。 可以帶正負號或不帶正負號整數類資料類型及任何大小從 8 位元到 64 位元。

> [!NOTE]
> 此程式庫的最新版本是位於[ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt)。

## <a name="in-this-section"></a>本節內容

功能                      | 描述
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | 兩個數字相加，並防止溢位。
[SafeCast](#safecast)         | 將轉換成另一個類型參數的一種。
[SafeDivide](#safedivide)     | 兩數相除並防止除以零。
[SafeEquals](#safeequals)， [SafeGreaterThan](#safegreaterthan)， [SafeGreaterThanEquals](#safegreaterthanequals)， [SafeLessThan](#safelessthan)， [SafeLessThanEquals](#safelessthanequals)， [SafeNotEquals](#safenotequals) | 比較兩個數字。 這些功能可讓您比較兩種不同的數字，而不需要變更其類型。
[SafeModulus](#safemodulus)   | 執行模數作業上兩個數字。
[SafeMultiply](#safemultiply) | 在一起的兩個數目相乘，並防止溢位。
[SafeSubtract](#safesubtract) | 兩個數字相減，並防止溢位。

## <a name="related-sections"></a>相關章節

區段                                                  | 描述
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../windows/safeint-class.md)                   | `SafeInt` 類別。
[SafeIntException](../windows/safeintexception-class.md) | SafeInt 程式庫的特定例外狀況類別。

## <a name="safeadd"></a>SafeAdd

兩個數字相加來防止溢位。

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
[in]要新增的第一個數字。 這必須為類型 T。

*u*<br/>
[in]若要新增第二個數字。 這必須為類型 U。

*結果*<br/>
[out]參數位置`SafeAdd`儲存結果。

### <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="safecast"></a>SafeCast

將一種類型的編號，另一種類型的轉換。

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>參數

*From*<br/>
[in]要轉換的來源點數。 這必須是型別`T`。

*若要*<br/>
[out]新的數字類型的參考。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="safedivide"></a>SafeDivide

兩數相除防止除以零的方式。

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
[in]除數。 這必須為類型 T。

*u*<br/>
[in]被除數。 這必須為類型 U。

*結果*<br/>
[out]參數位置`SafeDivide`儲存結果。

### <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="safeequals"></a>SafeEquals

比較兩個數字，以判斷它們是否相等。

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]要比較的第一個數字。 這必須為類型 T。

*u*<br/>
[in]要比較的第二個點數。 這必須為類型 U。

### <a name="return-value"></a>傳回值

**真**如果*t*並*u*相等，否則為**false**。

### <a name="remarks"></a>備註

因為 `==` 可讓您比較兩種不同類型的數字，所以此方法會增強 `SafeEquals`。

## <a name="safegreaterthan"></a>SafeGreaterThan

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
[in]要比較的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要比較的第二個點數。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**真**如果*t*大於*u*; 否則為**false**。

### <a name="remarks"></a>備註

`SafeGreaterThan` 延伸一般比較運算子，可讓您比較兩種不同的數字。

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

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
[in]要比較的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要比較的第二個點數。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**真**如果*t*大於或等於*u*; 否則為**false**。

### <a name="remarks"></a>備註

`SafeGreaterThanEquals` 增強的標準的比較運算子，因為它可讓您比較兩種不同的數字。

## <a name="safelessthan"></a>SafeLessThan

判斷一個數字是否小於另一個。

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]第一個數字。 這必須是型別`T`。

*u*<br/>
[in]第二個的號碼。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**真**如果*t*是小於*u*; 否則為**false**。

### <a name="remarks"></a>備註

這個方法會增強標準的比較運算子，因為`SafeLessThan`可讓您比較兩種不同的數字。

## <a name="safelessthanequals"></a>SafeLessThanEquals

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
[in]要比較的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要比較的第二個點數。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**真**如果*t*小於或等於*u*; 否則為**false**。

### <a name="remarks"></a>備註

`SafeLessThanEquals` 延伸一般比較運算子，可讓您比較兩種不同的數字。

## <a name="safemodulus"></a>SafeModulus

執行模數作業上兩個數字。

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
[in]除數。 這必須是型別`T`。

*u*<br/>
[in]被除數。 這必須是型別`U`。

*結果*<br/>
[out]參數位置`SafeModulus`儲存結果。

### <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="safemultiply"></a>SafeMultiply

兩個數目相乘，可防止溢位在一起。

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
[in]要相乘的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要相乘的第二個數字。 這必須是型別`U`。

*結果*<br/>
[out]參數位置`SafeMultiply`儲存結果。

### <a name="return-value"></a>傳回值

`true` 如果沒有發生錯誤;`false`發生錯誤。

## <a name="safenotequals"></a>SafeNotEquals

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
[in]要比較的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要比較的第二個點數。 這必須是型別`U`。

### <a name="return-value"></a>傳回值

**真**如果*t*並*u*不相等，否則為**false**。

### <a name="remarks"></a>備註

因為 `!=` 可讓您比較兩種不同類型的數字，所以此方法會增強 `SafeNotEquals`。

## <a name="safesubtract"></a>SafeSubtract

兩個數字的方式防止溢位。

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
[in]減法運算中的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要減去的數字*t*。 這必須是型別`U`。

*結果*<br/>
[out]參數位置`SafeSubtract`儲存結果。

### <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。
