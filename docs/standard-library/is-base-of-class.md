---
title: is_base_of 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: 345301b5eeed7b66f18a54e56b9bee6346078634
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383668"
---
# <a name="isbaseof-class"></a>is_base_of 類別

測試某個類型是否為另一個類型的基底。

## <a name="syntax"></a>語法

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>參數

*基底*<br/>
要測試的基底類別。

*衍生*<br/>
要測試的衍生類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*基底*型別的基底類別*衍生*，否則為 false。

## <a name="example"></a>範例

```cpp
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
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_convertible 類別](../standard-library/is-convertible-class.md)<br/>
