---
title: is_integral 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a3d618b77d69f5d80736ac20304c9184c5963b25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217762"
---
# <a name="is_integral-class"></a>is_integral 類別

測試類型是否為整數。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是其中一個整數類型，或是其中一個整數類型的形式，則類型述詞的實例為 true `cv-qualified` ，否則為 false。

整數類資料類型是、、、、、、、、、和的其中一個 **`bool`** **`char`** **`unsigned char`** **`signed char`** **`wchar_t`** **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** **`unsigned long`** 。 此外，透過提供這些專案的編譯器，整數類資料類型可以是 **`long long`** 、 **`unsigned long long`** 、和不 **`__int64`** **帶正負號 __int64**的其中一個。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_enum 類別](../standard-library/is-enum-class.md)\
[is_floating_point 類別](../standard-library/is-floating-point-class.md)
