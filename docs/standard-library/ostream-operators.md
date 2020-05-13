---
title: '&lt;ostream&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: d8b6f4e0f0b5bca41f8d895415fff4003231ad1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373611"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 運算子

||
|-|
|[算子&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>算子&lt;&lt;

將各種類型寫入資料流。

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>參數

*_Ch*\
字元。

*_Elem*\
元素類型。

*_Ostr*\
`basic_ostream` 物件。

*Str*\
字元字串。

*_Tr*\
字元特性。

*瓦爾*\
類型

### <a name="return-value"></a>傳回值

資料流。

### <a name="remarks"></a>備註

`basic_ostream` 類別也會定義數個插入運算子。 有關詳細資訊,請參閱[basic_ostream:運算子&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)。

樣板函式

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

確定序列的長度`traits_type::`N`str`=[長度](../standard-library/char-traits-struct.md#length)( ), 從*str*開始,然後插入序列。 如果 N < `_Ostr.`[width](../standard-library/ios-base-class.md#width)，則函式會另外插入重複的 `_Ostr.width` - N 填滿字元。 如果 (),`_Ostr`重複在序列之前。 [flags](../standard-library/ios-base-class.md#flags)標誌`adjustfield`!=[左](../standard-library/ios-functions.md#left) & 。 否則，重複項目會接在序列後面。 函數傳回 *_Ostr*。

樣板函式

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

插入項目 `_Ch`。 如果 1 < `_Ostr.width`，則函式會另外插入 `_Ostr.width` - 1 填滿字元的重複項目。 在以下情況重複項目會排在序列之前：當 `_Ostr.flags & adjustfield != left`。 否則，重複項目會接在序列後面。 傳回 *_Ostr*。

樣板函式

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

行為相同於

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

只不過,序列從*str*開始的每個元素`_Ostr.`*_Ch*通過調用`_Ch`[put(](../standard-library/basic-ostream-class.md#put)`_Ostr.`[加寬](../standard-library/basic-ios-class.md#widen)( ) ) 轉換為類型`Elem`的物件。

樣板函式

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

行為相同於

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

除非 *_Ch*_Ch`Elem`透過`_Ostr.put`呼叫`_Ostr.widen``_Ch`( ) 轉換為類型的物件。

樣板函式

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

行為相同於

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(插入項目之前並不需要擴展項目)。

樣板函式

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

行為相同於

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(在插入 *_Ch*之前,它不必加寬。

樣板函式

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

傳`_Ostr`回`const char *``str` << ( )

樣板函式

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

傳`_Ostr`回`char``_Ch` << ( )

範本函式：

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

傳`_Ostr`回`const char *``str` << ( )

範本函式：

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

傳`_Ostr`回`char``_Ch` << ( )

範本函式：

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

傳回 `_Ostr` `<<` `val` (並轉換[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md)為 `_Ostr` 到程序中的左值)。

### <a name="example"></a>範例

如需 `operator<<` 的使用範例，請參閱 [flush](../standard-library/ostream-functions.md#flush)。

## <a name="see-also"></a>另請參閱

[\<流>](../standard-library/ostream.md)
