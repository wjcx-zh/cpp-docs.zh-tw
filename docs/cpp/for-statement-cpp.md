---
title: for 陳述式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: e3dfdb45bdf8a508eca9d29e90b3f7c05e7b147d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179909"
---
# <a name="for-statement-c"></a>for 陳述式 (C++)

重複執行陳述式，直到條件變成 false。 如需以範圍為基礎的 for 語句的詳細資訊，請參閱以[範圍C++為基礎的 for 語句（）](../cpp/range-based-for-statement-cpp.md)。

## <a name="syntax"></a>語法

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>備註

使用**for**語句來建造必須執行指定次數的迴圈。

**For**語句是由三個選擇性元件所組成，如下表所示。

### <a name="for-loop-elements"></a>for 迴圈項目

|語法名稱|何時執行|描述|
|-----------------|-------------------|-----------------|
|`init-expression`|在**for**語句的任何其他元素之前，`init-expression` 只會執行一次。 之後就會將控制項傳遞給 `cond-expression`。|通常用來初始迴圈索引。 它可能包含運算式或宣告。|
|`cond-expression`|在執行 `statement` 的每個反覆項目之前，包括第一個反覆項目。 除非 `statement` 判斷值為 true (非零)，否則不會執行 `cond-expression`。|判斷值為整數類型的運算式或具有整數類型明確轉換的類別類型。 通常用來測試迴圈終止準則。|
|`loop-expression`|每個 `statement` 反覆項目的結尾。 在 `loop-expression` 執行後會評估 `cond-expression`。|通常用來遞增迴圈索引。|

下列範例示範使用**for**語句的不同方式。

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

執行 `statement` 中的[break](../cpp/break-statement-cpp.md)、 [return](../cpp/return-statement-cpp.md)或[goto](../cpp/goto-statement-cpp.md) （至**for**迴圈以外的標籤語句）時， **for**迴圈就會終止。 **For**迴圈中的[continue](../cpp/continue-statement-cpp.md)語句只會終止目前的反復專案。

如果省略 `cond-expression`，則會將它視為 true，而**for**迴圈不會在 `statement`中的**break**、 **return**或**goto**的情況下終止。

雖然**for**語句的三個欄位通常用於初始化、測試終止和遞增，但它們並不限於這些用途。 例如，下列程式碼會列印數字 0 到 4。 在這個範例中，`statement` 是 Null 陳述式：

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

標準指出在**for 迴圈中**宣告的變數，在 for 迴圈結束之後，應該超出範圍。 **for** C++ 例如：

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

根據預設，在[/ze](../build/reference/za-ze-disable-language-extensions.md)之下，在**for**迴圈中宣告的變數會保留在範圍內，直到**for**迴圈的封閉範圍結束為止。

[/Zc： forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)啟用 for 迴圈中宣告之變數的標準行為，而不需要指定 `/Za`。

您也可以使用**for**迴圈的範圍差異，在 `/Ze` 下重新宣告變數，如下所示：

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

這會更密切地模擬在**for**迴圈中宣告之變數的標準行為，而這需要在**for**迴圈中宣告的變數在迴圈完成之後移出範圍。 在**for**迴圈中宣告變數時，編譯器會在內部將它升級為**for**迴圈封閉範圍中的區域變數，即使已經有相同名稱的本機變數也一樣。

## <a name="see-also"></a>另請參閱

[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[while 陳述式 (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)
