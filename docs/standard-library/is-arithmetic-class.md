---
title: is_arithmetic 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_arithmetic
dev_langs:
- C++
helpviewer_keywords:
- is_arithmetic class
- is_arithmetic
ms.assetid: ea427b7e-0141-4a04-848f-561054c53001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 161551747455bae1347e5059ec3afffd2649294c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845293"
---
# <a name="isarithmetic-class"></a>is_arithmetic 類別

測試類型是否為算術。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_arithmetic;
```

### <a name="parameters"></a>參數

`Ty` 要查詢的類型。

## <a name="remarks"></a>備註

如果類型 `Ty` 是算術類型，也就是整數類型、浮點類型或其中之一的 `cv-qualified` 形式，則類型述詞的執行個體為 true，否則會為 false。

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

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_floating_point 類別](../standard-library/is-floating-point-class.md)<br/>
[is_integral 類別](../standard-library/is-integral-class.md)<br/>
