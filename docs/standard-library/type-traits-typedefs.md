---
title: '&lt;type_traits&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: 70894689f934ef8008bfa2d82ae63727c2e2605d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841736"
---
# <a name="lttype_traitsgt-typedefs"></a>&lt;type_traits&gt; typedef

[false_type](#false_type)\
[true_type](#true_type)

## <a name="false_type-typedef"></a><a name="false_type"></a> false_type Typedef

存有具有 False 值的整數常數。

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>備註

類型是樣板 `integral_constant` 的特製化同義字。

### <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type-typedef"></a><a name="true_type"></a> true_type Typedef

存有具有 True 值的整數常數。

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>備註

類型是樣板 `integral_constant` 的特製化同義字。

### <a name="example"></a>範例

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
