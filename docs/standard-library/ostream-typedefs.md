---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: a61eeb98dfd275b10749e86043a3f7042be84ab9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224652"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

從特殊化 **`char`** 並 `char_traits` 在上特殊化的 basic_ostream 建立類型 **`char`** 。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專門用於 **`char`** 具有預設字元特性之類型的元素。

## <a name="wostream"></a><a name="wostream"></a>wostream

從特殊化 **`wchar_t`** 並 `char_traits` 在上特殊化的 basic_ostream 建立類型 **`wchar_t`** 。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專門用於 **`wchar_t`** 具有預設字元特性之類型的元素。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
