---
title: is_convertible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_convertible
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
ms.openlocfilehash: c90fe5687992e4df49e8655387cfdd14b40aa529
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454616"
---
# <a name="isconvertible-class"></a>is_convertible 類別

測試某個型別是否可轉換為另一個型別。

## <a name="syntax"></a>語法

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>參數

*從*\
要轉換的來源型別。

*Ty*\
要轉換的目標類型。

## <a name="remarks"></a>備註

如果運算式 `To to = from;` (其中 `from` 是型別 `From` 的物件) 格式正確，則 predicate 型別的執行個體保留 true。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }
```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_base_of 類別](../standard-library/is-base-of-class.md)
