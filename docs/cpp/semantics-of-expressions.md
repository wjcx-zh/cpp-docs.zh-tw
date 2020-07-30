---
title: 運算式的語意
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: 43bcd98e0dbf14dada2643c0b731d3f6bae863e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223599"
---
# <a name="semantics-of-expressions"></a>運算式的語意

運算式會根據其運算子的優先順序和群組進行評估。 （在[詞法慣例](../cpp/lexical-conventions.md)中，[運算子優先順序和關聯](../cpp/cpp-built-in-operators-precedence-and-associativity.md)性會顯示 c + + 運算子強加于運算式的關聯性）。

## <a name="order-of-evaluation"></a>評估順序

請思考此範例：

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![運算式中的評估順序](../cpp/media/vc38zv1.gif "運算式中的評估順序") <br/>
運算式評估順序

上圖中顯示運算式評估的順序可用來判斷運算子的優先順序和關聯性：

1. 在此運算式中，乘法 (*) 具有最高優先順序，因此會先評估子運算式 `b * c`。

1. 下一個最高優先順序的項目是加法 (+)，因此會將 `a` 與 `b` 和 `c` 的乘積相加。

1. 左移（<<）在運算式中的優先順序最低，但出現兩次。 由於左移運算子是由左至右來分組，因此會先評估左方的子運算式，再評估右邊的子運算式。

在子運算式的群組中使用括號時，會改變優先順序以及運算式的評估順序，如下圖所示。

![具有括號之運算式的評估順序](../cpp/media/vc38zv2.gif "具有括號之運算式的評估順序") <br/>
運算式-具有括弧的評估順序

運算式 (如上圖) 會單純地評估其副作用，在此例中，會將資訊傳送到標準輸出裝置。

## <a name="notation-in-expressions"></a>運算式中的標記法

指定運算元時，C++ 語言會指定特定的相容性。 下表顯示需要類型*為類型之*運算元的運算子可接受的運算元類型。

### <a name="operand-types-acceptable-to-operators"></a>運算子可接受的運算元類型

|預期的類型|允許的類型|
|-------------------|-------------------|
|*type*|**`const`***類型*<br /> **`volatile`***類型*<br /> *型*&<br /> **`const`***類型*&<br /> **`volatile`***類型*&<br /> `volatile const`*類型*<br /> `volatile const`*類型*&|
|*類型*\*|*類型*\*<br /> **`const`***類型*\*<br /> **`volatile`***類型*\*<br /> `volatile const`*類型*\*|
|**`const`***類型*|*type*<br /> **`const`***類型*<br />**`const`***類型*&|
|**`volatile`***類型*|*type*<br /> **`volatile`***類型*<br /> **`volatile`***類型*&|

由於上述規則一律可以搭配使用，因此可以在預期出現指標的位置提供 volatile 物件的 const 指標。

## <a name="ambiguous-expressions"></a>模稜兩可的運算式

某些運算式的意義模稜兩可。 若物件的值在同一個運算式中修改過一次以上，最容易出現這些運算式。 這些運算式依賴特定評估順序，而語言並未定義評估順序。 請考慮下列範例：

```
int i = 7;

func( i, ++i );
```

C++ 語言不保證函式呼叫引數的評估順序。 因此，在前述範例中，`func` 可能收到的參數值包括 7 和 8 或 8 和 8，需視是從左到右或從右到左評估參數而定。

## <a name="c-sequence-points-microsoft-specific"></a>C + + 序列點（Microsoft 專有）

運算式只能在連續「序列點」之間修改物件的值一次。

C++ 語言定義目前未指定序列點。 針對包含 C 運算子及未包含多載運算子的任何運算式，Microsoft C++ 使用與 ANSI C 相同的序列點。 當運算子經過多載時，其語意會從運算子序列變更為函式呼叫序列。 Microsoft C++ 使用下列序列點：

- 邏輯 AND 運算子的左運算元（&&）。 繼續之前會完整評估邏輯 AND 運算子的左運算元，並且完成所有副作用。 不保證會評估邏輯 AND 運算子的右運算元。

- 邏輯 OR 運算子的左運算元（&#124;&#124;）。 繼續之前會完整評估邏輯 OR 運算子的左運算元，並且完成所有副作用。 不保證會評估邏輯 OR 運算子的右運算元。

- 逗號運算子的左運算元。 繼續之前會完整評估逗號運算子的左運算元，並且完成所有副作用。 逗號運算子的兩個運算元會一律進行評估。

- 函式呼叫運算子。 在進入函式之前會先評估函式呼叫運算式和函式的所有引數 (包括預設引數)，並完成所有副作用。 其中並未指定引數或函式呼叫運算式之間的評估順序。

- 條件運算子的第一個運算元。 繼續之前會完整評估條件運算子的第一運算元，並且完成所有副作用。

- 完整初始化運算式的結尾，例如在宣告陳述式中初始化的結尾。

- 運算陳述式中的運算式。 運算式陳述式包含選擇性運算式且後面加上分號 (;)。 會針對運算式的副作用進行完整的評估。

- 選取範圍 (if 或 switch) 陳述式中的控制運算式。 會完整評估運算式，且其所有副作用會在執行與選取範圍相關的程式碼執行之前完成。

- while 或 do 陳述式的控制運算式。 會完整評估運算式，且其所有副作用會在執行 while 或 do 迴圈的下次反覆項目中的陳述式之前完成。

- for 陳述式的三個運算式中的每一個。 會完整評估每個運算式，且其所有副作用會在移至下一個運算式之前完成。

- return 陳述式中的運算式。 會完整評估運算式，且其所有副作用會在控制回到呼叫函式之前完成。

## <a name="see-also"></a>另請參閱

[運算式](../cpp/expressions-cpp.md)
