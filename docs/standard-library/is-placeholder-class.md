---
title: is_placeholder 類別
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 9fa7d4aaade6244fe26f89f3a667598d39471a47
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245167"
---
# <a name="isplaceholder-class"></a>is_placeholder 類別

測試類型是否是預留位置。

## <a name="syntax"></a>語法

結構 is_placeholder {靜態 const int 值;};

## <a name="remarks"></a>備註

如果類型 `Ty` 不是預留位置，常數值 `value` 就會是 0；否則其值會是它所繫結之函式呼叫引數的位置。 您可以使用它來判斷第 N 個預留位置 `_N` 的值 `N`。

## <a name="example"></a>範例

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
