---
title: is_function 類別
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_function
helpviewer_keywords:
- is_function class
- is_function
ms.assetid: e5c0dbcd-829b-415f-853f-8c5be47c5040
ms.openlocfilehash: 6e436d205c7569aeac7b9dc65b122f3fe289f334
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456263"
---
# <a name="isfunction-class"></a>is_function 類別

測試類型是否為函式類型。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_function;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是函式類型, 則類型述詞的實例會保留 true, 否則會保留 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_function.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_function<trivial> == " << std::boolalpha
        << std::is_function<trivial>::value << std::endl;
    std::cout << "is_function<functional> == " << std::boolalpha
        << std::is_function<functional>::value << std::endl;
    std::cout << "is_function<float()> == " << std::boolalpha
        << std::is_function<float()>::value << std::endl;

    return (0);
    }
```

```Output
is_function<trivial> == false
is_function<functional> == false
is_function<float()> == true
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_object 類別](../standard-library/is-object-class.md)
