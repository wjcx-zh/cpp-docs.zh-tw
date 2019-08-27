---
title: is_base_of 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: d56222f218033d00583e5e3def9790720ef7bb94
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456614"
---
# <a name="isbaseof-class"></a>is_base_of 類別

測試某個類型是否為另一個類型的基底。

## <a name="syntax"></a>語法

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>參數

*群體*\
要測試的基底類別。

*源于*\
要測試的衍生類型。

## <a name="remarks"></a>備註

如果類型*基底*為*衍生*類型的基類, 則類型述詞的實例為 true, 否則為 false。

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

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[is_convertible 類別](../standard-library/is-convertible-class.md)
