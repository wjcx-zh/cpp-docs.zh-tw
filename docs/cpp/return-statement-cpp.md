---
title: return 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 6a1ed4f374f133abd0233826d1b58896d49576cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225861"
---
# <a name="return-statement-c"></a>return 陳述式 (C++)

終止函式執行並將控制項傳回至進行呼叫的函式 (或者，如果您是從 `main` 函式傳送控制項，則傳回至作業系統)。 執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。

## <a name="syntax"></a>語法

```
return [expression];
```

## <a name="remarks"></a>備註

`expression` 子句 (如果有的話) 會轉換成函式宣告中指定的類型，就像執行初始化一般。 從運算式的類型轉換成 **`return`** 函數的類型，可以建立暫存物件。 如需如何和何時建立而暫存物件的詳細資訊，請參閱[暫存物件](../cpp/temporary-objects.md)。

`expression` 子句的值會傳回至進行呼叫的函式。 如果省略運算式，則函式的傳回值會是未定義。 函式和析構函式以及類型的函式 **`void`** ，無法在語句中指定運算式 **`return`** 。 所有其他類型的函式都必須在語句中指定運算式 **`return`** 。

當控制流程結束封閉函式定義的區塊時，其結果會與未 **`return`** 執行運算式的語句相同。 這對於宣告為傳回值的函式是無效的。

函數可以有任意數目的 **`return`** 語句。

下列範例會使用運算式搭配 **`return`** 語句來取得兩個整數的最大值。

## <a name="example"></a>範例

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>另請參閱

[跳躍陳述式](../cpp/jump-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
