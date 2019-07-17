---
title: _1 物件
ms.date: 11/04/2016
f1_keywords:
- _1
- std::_1
- functional/std::_1
helpviewer_keywords:
- _1 object
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
ms.openlocfilehash: 1c1f13d40e02ec6e099ef1e2c20fe1cac4a4ef93
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246542"
---
# <a name="1-object"></a>_1 物件

可取代引數的預留位置。

## <a name="syntax"></a>語法

```cpp
namespace placeholders {
    extern unspecified _1, _2, ... _M
} // namespace placeholders (within std)
```

## <a name="remarks"></a>備註

物件`_1, _2, ... _M`會指定第一次，第二個、...、 第 m 個引數，分別在函式呼叫所傳回的物件預留位置[繫結](../standard-library/functional-functions.md#bind)。 您可以使用 `_N` 來指定在評估繫結運算式時，應該插入第 N 個引數的位置。

在此實作中，`M` 的值為 20。

## <a name="example"></a>範例

```cpp
// std__functional_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
    {
    std::cout << x << "^2 == " << x * x << std::endl;
    }

void product(double x, double y)
    {
    std::cout << x << "*" << y << " == " << x * y << std::endl;
    }

int main()
    {
    double arg[] = {1, 2, 3};

    std::for_each(&arg[0], &arg[3], square);
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(square, _1));

    return (0);
    }
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```
