---
title: is_integral 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456244"
---
# <a name="isintegral-class"></a>is_integral 類別

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

如果類型*Ty*是其中一個整數類型, 或是`cv-qualified`其中一個整數類型的形式, 則類型述詞的實例為 true, 否則為 false。

整數類型為**bool**、 **char**、不**帶正負**號的 char、**帶正負**號的 char、 **wchar_t**、 **short**、不**帶正負**號的 short、 **int**、不**帶正負**號的 int、 **long**和不**帶正負**號 此外, 使用提供它們的編譯器, 整數類型可以是**long long**、不**帶正負**號的 long long、 **__int64**和不**帶正負號 __int64**的其中一個。

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

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_enum 類別](../standard-library/is-enum-class.md)\
[is_floating_point 類別](../standard-library/is-floating-point-class.md)
