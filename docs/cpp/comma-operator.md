---
title: 逗號運算子：,
ms.date: 11/04/2016
f1_keywords:
- '%2C'
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
ms.openlocfilehash: 6ea2bd5c0e7653ba7f81531a5c39df2da41662a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189763"
---
# <a name="comma-operator-"></a>逗號運算子：,

允許將兩個陳述式設為群組，其中一個是必要項。

## <a name="syntax"></a>語法

```
expression , expression
```

## <a name="remarks"></a>備註

逗號運算子具有由左到右的順序關聯性 (Associativity)。 以逗號分隔的兩個運算式會由左至右求值。 左運算元一定會進行求值，而且所有副作用都會在右運算元求值之前完成。

逗號可以在某些內容中做為分隔符號使用，例如，函式引數清單。 請勿混淆做為分隔符號使用的逗號，與做為運算子使用的逗號，這兩種用法完全不同。

以 `e1, e2` 運算式為例。 運算式的類型和值是*e2*的類型和值。會捨棄評估*e1*的結果。 如果右運算元是左值，則結果會是左值。

逗號通常做為分隔符號使用 (例如，在函式的實際引數中或彙總初始設定式中)，而逗號運算子及其運算元必須以括號括住。 例如：

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

在上面 `func_one` 的函式呼叫中，會傳遞三個以逗號分隔的引數：`x`、`y + 2` 和 `z`。 在 `func_two` 的函式呼叫中，括號會強制編譯器將第一個逗號解譯為循序求值運算子。 這個函式呼叫會傳遞兩個引數至 `func_two`。 第一個引數是循序求值運算 `(x--, y + 2)` 的結果，具有 `y + 2` 運算式的值和類型，而第二個引數為 `z`。

## <a name="example"></a>範例

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[循序評估運算子](../c-language/sequential-evaluation-operator.md)
