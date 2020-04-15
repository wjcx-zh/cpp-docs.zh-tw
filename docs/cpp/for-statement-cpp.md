---
title: for 陳述式 (C++)
description: 在 Microsoft 視覺工作室 C++中引用標準 C++。
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375389"
---
# <a name="for-statement-c"></a>for 陳述式 (C++)

重複執行陳述式，直到條件變成 false。 有關基於範圍的語句的資訊,請參閱[基於範圍的語句 (C++)](../cpp/range-based-for-statement-cpp.md)。

## <a name="syntax"></a>語法

> **`for (`***init 運算式***`;`***cond 表示式***`;`***循環式***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_宣告_**`;`**

## <a name="remarks"></a>備註

使用**for**語句構造必須執行指定次數的迴圈。

**for**語句由三個可選部分組成,如下表所示。

### <a name="for-loop-elements"></a>for 迴圈項目

|語法名稱|何時執行|描述|
|-----------------|-------------------|-----------------|
|`init-expression`|**在 for**語句的任何其他元素`init-expression`之前, 僅執行一次。 之後就會將控制項傳遞給 `cond-expression`。|通常用來初始迴圈索引。 它可能包含運算式或宣告。|
|`cond-expression`|在執行 `statement` 的每個反覆項目之前，包括第一個反覆項目。 除非 `statement` 判斷值為 true (非零)，否則不會執行 `cond-expression`。|判斷值為整數類型的運算式或具有整數類型明確轉換的類別類型。 通常用來測試迴圈終止準則。|
|`loop-expression`|每個 `statement` 反覆項目的結尾。 在 `loop-expression` 執行後會評估 `cond-expression`。|通常用來遞增迴圈索引。|

以下範例顯示了使用**for**語句的不同方法。

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
}
    // Output: 012
```

`init-expression` 和 `loop-expression` 可以包含以逗號分隔的多個陳述式。 例如：

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

`loop-expression` 可以遞增或遞減，也可以利用其他方式修改。

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

當在`statement`for 循環中[執行中斷](../cpp/break-statement-cpp.md)、[傳回](../cpp/return-statement-cpp.md)或[goto(](../cpp/goto-statement-cpp.md)到**for**循環外部標記的語句)時 **,for**迴圈將終止。 **for**迴圈中的[繼續](../cpp/continue-statement-cpp.md)語句僅終止當前反覆運算。

如果`cond-expression`省`true`略 ,則考慮 它,並且**for**迴圈不會在**break**中斷`statement`、**返回**或**轉到**內終止。

儘管**for**語句的三個字段通常用於初始化、終止測試和增量,但它們並不限於這些用途。 例如，下列程式碼會列印數字 0 到 4。 在這個範例中，`statement` 是 Null 陳述式：

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>for 迴圈和 C++ 標準

C++標準表示,**在 for**迴圈中聲明的變數應在**for**循環結束後超出範圍。 例如：

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

預設情況下,在[/Ze](../build/reference/za-ze-disable-language-extensions.md)下,**在 for**迴圈中聲明的變數將保留在作用域中,直到**for**迴圈的封閉作用域結束。

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)支援在循環中聲明的變數的標準行為,而無需指定`/Za`。

也可以使用**for**循環的範圍差異來重新聲明變數`/Ze`, 如下所示:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

此行為更緊密地類比**在 for**循環中聲明的變數的標準行為,該行為要求在**for**迴圈中聲明的變數在迴圈完成後超出範圍。 當變數在**for**循環中聲明時,編譯器在內部將其提升為**for**迴圈的封閉作用域中的局部變數。 即使已有同名的局部變數,也會升級它。

## <a name="see-also"></a>另請參閱

[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[而聲明(C++)](../cpp/while-statement-cpp.md)<br/>
[做-while 語句 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)
