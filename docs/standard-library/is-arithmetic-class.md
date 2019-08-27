---
title: is_arithmetic 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_arithmetic
helpviewer_keywords:
- is_arithmetic class
- is_arithmetic
ms.assetid: ea427b7e-0141-4a04-848f-561054c53001
ms.openlocfilehash: e2c148b7cb58cf38e5f73d4e3d2297eac099ef7e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456681"
---
# <a name="isarithmetic-class"></a>is_arithmetic 類別

測試類型是否為算術。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_arithmetic;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是算術類型 (也就是整數類型或浮點類型) 或`cv-qualified`其中之一的形式, 則類型述詞的實例會保留 true, 否則會保留 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_arithmetic.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_arithmetic<trivial> == " << std::boolalpha
        << std::is_arithmetic<trivial>::value << std::endl;
    std::cout << "is_arithmetic<int> == " << std::boolalpha
        << std::is_arithmetic<int>::value << std::endl;
    std::cout << "is_arithmetic<float> == " << std::boolalpha
        << std::is_arithmetic<float>::value << std::endl;

    return (0);
    }
```

```Output
is_arithmetic<trivial> == false
is_arithmetic<int> == true
is_arithmetic<float> == true
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_floating_point 類別](../standard-library/is-floating-point-class.md)\
[is_integral 類別](../standard-library/is-integral-class.md)
