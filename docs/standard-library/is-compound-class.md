---
title: is_compound 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: ae2e3c66b3abf22bbefbcb0fcd3292f0a3dbdbe2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215708"
---
# <a name="is_compound-class"></a>is_compound 類別

測試指定的類型是否不是基本。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

**`false`** 如果*Ty*的類型是基本類型（也就是，如果[is_fundamental](../standard-library/is-fundamental-class.md)保留），則類型述詞的實例會保留 \<Ty> **`true`** ，否則會保留 **`true`** 。 因此， **`true`** 如果*Ty*是陣列類型、函式類型、或物件或函式的指標 **`void`** 、參考、類別、等位、列舉或非靜態類別成員的指標，或其中一個的*cv 限定*形式，則此述詞會保存。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_class 類別](../standard-library/is-class-class.md)
