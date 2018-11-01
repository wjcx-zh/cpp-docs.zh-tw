---
title: is_bind_expression 類別
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: f547b6f74a86612174cb0f510870171158678f7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519414"
---
# <a name="isbindexpression-class"></a>is_bind_expression 類別

測試類型是否是透過呼叫 `bind` 來產生的。

## <a name="syntax"></a>語法

範本<class Ty>結構 is_bind_expression {靜態 const bool 值;};

## <a name="remarks"></a>備註

如果類型 `Ty` 是對 `bind` 的呼叫所傳回的類型，常數成員 `value` 便為 true，否則為 false。

## <a name="example"></a>範例

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[bind](../standard-library/functional-functions.md#bind)<br/>
