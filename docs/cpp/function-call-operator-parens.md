---
title: 函式呼叫運算子：（）
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 5bb87795d3e91d853dc0d269ee9d2aa3ba025c0e
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813546"
---
# <a name="function-call-operator-"></a>函式呼叫運算子：()

函式呼叫是一種 *`postfix-expression`* ，由評估為函式或可呼叫物件後面接著函式呼叫運算子的運算式所組成 **`()`** 。 物件可以宣告函式 `operator ()` ，以提供物件的函式呼叫語義。

## <a name="syntax"></a>語法

> *`postfix-expression`*:\
> &emsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>備註

函式呼叫運算子的引數來自 *`argument-expression-list`* （以逗號分隔的運算式清單）。 這些運算式的值會當做引數傳遞至函式。 *引數運算式清單*可以是空的。 在 c + + 17 之前，函數運算式和引數運算式的評估順序並未指定，而且可能會以任何順序發生。 在 c + + 17 和更新版本中，函數運算式會在任何引數運算式或預設引數之前進行評估。 引數運算式會以不確定的順序進行評估。

會 *`postfix-expression`* 評估為要呼叫的函式。 它可以採用數種形式的其中一種：

- 函式識別碼，可在目前的範圍中看見，或在提供的任何函式引數範圍中顯示。
- 評估為函式、函式指標、可呼叫物件，或參考至其中一個的運算式
- 成員函式存取子（明確或隱含）
- 成員函式的解除引用指標。

*`postfix-expression`* 可能是多載函數識別碼或多載成員函式存取子。 多載解析的規則會決定要呼叫的實際函數。 如果成員函式是虛擬的，則會在執行時間決定要呼叫的函式。

一些範例宣告：

- 傳回類型 `T` 的函式。 如以下範例宣告所示

    ```cpp
    T func( int i );
    ```

- 傳回類型 `T` 之函式的指標。 如以下範例宣告所示

    ```cpp
    T (*func)( int i );
    ```

- 傳回類型 `T` 之函式的參考。 如以下範例宣告所示

    ```cpp
    T (&func)(int i);
    ```

- 傳回類型 `T` 的成員指標函式取值 (Dereference)。 函式呼叫的範例如下

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>範例

下列範例呼叫具有三個引數的標準程式庫函式 `strcat_s`：

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>函式呼叫結果

除非函式宣告為參考型別，否則函式呼叫會評估為右值。 具有參考傳回類型的函數會評估為左值。 這些函數可以在指派語句的左邊使用，如下所示：

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

上述程式碼會定義名為的類別 `Point` ，其中包含代表*x*和*y*座標的私用資料物件。 這些資料物件必須經過修改，而且必須擷取其值。 這個程式只是這種類別的數項設計之一，使用 `GetX` 和 `SetX` 或 `GetY` 和 `SetY` 則是另一種可能的設計方式。

傳回類別類型、類別類型的指標或類別類型的參考之函式可以做為成員選擇運算子的左運算元使用。 下列程式碼是合法的：

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

函式可以透過遞迴方式呼叫。 如需函式宣告的詳細資訊，請參閱[函數](functions-cpp.md)。 相關的資料位於[轉譯單位和連結](../cpp/program-and-linkage-cpp.md)中。

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C + + 內建運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[函式呼叫](../c-language/function-call-c.md)
