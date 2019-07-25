---
title: is_same 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_same
helpviewer_keywords:
- is_same class
- is_same
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
ms.openlocfilehash: f4e4babeef89960762ebb2ccf0f733f60eadfa47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450050"
---
# <a name="issame-class"></a>is_same 類別

測試兩個類型是否相同。

## <a name="syntax"></a>語法

```cpp
template <class Ty1, class Ty2>
struct is_same;
```

### <a name="parameters"></a>參數

*Ty1*\
要查詢的第一個類型。

*Ty2*\
要查詢的第二個類型。

## <a name="remarks"></a>備註

如果類型*Ty1*和*Ty2*屬於相同類型, 則類型述詞的實例為 true, 否則為 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_same.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_same<base, base> == " << std::boolalpha
        << std::is_same<base, base>::value << std::endl;
    std::cout << "is_same<base, derived> == " << std::boolalpha
        << std::is_same<base, derived>::value << std::endl;
    std::cout << "is_same<derived, base> == " << std::boolalpha
        << std::is_same<derived, base>::value << std::endl;
    std::cout << "is_same<int, int> == " << std::boolalpha
        << std::is_same<int, int>::value << std::endl;
    std::cout << "is_same<int, const int> == " << std::boolalpha
        << std::is_same<int, const int>::value << std::endl;

    return (0);
    }
```

```Output
is_same<base, base> == true
is_same<base, derived> == false
is_same<derived, base> == false
is_same<int, int> == true
is_same<int, const int> == false
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_convertible 類別](../standard-library/is-convertible-class.md)\
[is_base_of 類別](../standard-library/is-base-of-class.md)
