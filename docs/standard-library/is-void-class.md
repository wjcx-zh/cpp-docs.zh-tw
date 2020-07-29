---
title: is_void 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_void
helpviewer_keywords:
- is_void class
- is_void
ms.assetid: 99b0de3b-1b38-4949-b053-080e5363174e
ms.openlocfilehash: 49fef050393f7196fe26aa172ac02792ae5c717e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212224"
---
# <a name="is_void-class"></a>is_void 類別

測試類型是否為 void。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_void;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是或的 cv 限定格式，則類型述詞的實例為 true **`void`** **`void`** ，否則為 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_void.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_void<trivial> == " << std::boolalpha
        << std::is_void<trivial>::value << std::endl;
    std::cout << "is_void<void()> == " << std::boolalpha
        << std::is_void<void()>::value << std::endl;
    std::cout << "is_void<void> == " << std::boolalpha
        << std::is_void<void>::value << std::endl;

    return (0);
    }
```

```Output
is_void<trivial> == false
is_void<void()> == false
is_void<void> == true
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
