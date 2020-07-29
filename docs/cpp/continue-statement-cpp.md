---
title: continue 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 55a81338f1a0f9036a6d42c4bac7c99489c18d64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228995"
---
# <a name="continue-statement-c"></a>continue 陳述式 (C++)

強制將控制權轉移至最小封閉式[do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)或[while](../cpp/while-statement-cpp.md)迴圈的控制運算式。

## <a name="syntax"></a>語法

```
continue;
```

## <a name="remarks"></a>備註

目前反覆項目中其餘的任何陳述式都不會執行。 迴圈中下一個反覆項目的判斷方式如下：

- 在 **`do`** 或 **`while`** 迴圈中，下一個反復專案一開始會對或語句的控制運算式 **`do`** **`while`** 。

- 在 **`for`** 迴圈中（使用語法 `for( <init-expr> ; <cond-expr> ; <loop-expr> )` ）， `<loop-expr>` 會執行子句。 然後會重新求出 `<cond-expr>` 子句的值，而根據結果，迴圈會結束或另一個反覆項目會發生。

下列範例示範如何 **`continue`** 使用語句來略過程式碼區段，並開始進行迴圈的下一個反復專案。

## <a name="example"></a>範例

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>另請參閱

[跳躍陳述式](../cpp/jump-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
