---
title: for 語句（c + +）
description: Microsoft Visual Studio c + + 中的標準 c + + for 語句參考。
f1_keywords:
- for_cpp
ms.date: 07/31/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: b32a50e376113f9f9d550d4984d05fc8c675f14d
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520845"
---
# <a name="for-statement-c"></a>`for`語句（c + +）

重複執行陳述式，直到條件變成 false。 如需範圍架構語句的詳細資訊 **`for`** ，請參閱以[範圍為基礎的 `for` 語句（c + +）](../cpp/range-based-for-statement-cpp.md)。

## <a name="syntax"></a>Syntax

> **`for (`** *`init-expression`* **`;`** *`cond-expression`* **`;`** *`loop-expression`* **`)`**\
> &emsp;*`statement`*

## <a name="remarks"></a>備註

使用 **`for`** 語句來建立必須執行指定次數的迴圈。

**`for`** 語句是由三個選擇性元件所組成，如下表所示。

### <a name="for-loop-elements"></a>for 迴圈元素

| 語法名稱 | 執行時 | 說明 |
|--|--|--|
| *`init-expression`* | 在語句的任何其他元素之前 **`for`** ， *`init-expression`* 只會執行一次。 控制項接著會傳遞至 *`cond-expression`* 。 | 通常用來初始迴圈索引。 它可能包含運算式或宣告。 |
| *`cond-expression`* | 執行的每個反復專案之前 *`statement`* ，包括第一個反復專案。 *`statement`* 只有在 *`cond-expression`* 評估為 true （非零）時，才會執行。 | 判斷值為整數類型的運算式或具有整數類型明確轉換的類別類型。 通常用來測試迴圈終止準則。 |
| *`loop-expression`* | 在的每個反復專案結束時 *`statement`* 。 在 *`loop-expression`* 執行之後， *`cond-expression`* 會評估。 | 通常用來遞增迴圈索引。 |

下列範例示範使用語句的不同方式 **`for`** 。

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
    // Output: 01
}
```

*`init-expression`* 和 *`loop-expression`* 可以包含多個語句，並以逗號分隔。 例如：

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

*`loop-expression`* 可以遞增或遞減，或以其他方式修改。

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

**`for`** [`break`](../cpp/break-statement-cpp.md) 執行中的、 [return](../cpp/return-statement-cpp.md)或 [`goto`](../cpp/goto-statement-cpp.md) （指向迴圈外的標籤語句）時，迴圈 **`for`** 會終止 *`statement`* 。 [`continue`](../cpp/continue-statement-cpp.md)迴圈中的語句 **`for`** 只會終止目前的反復專案。

如果 *`cond-expression`* 省略，則會將它視為 **`true`** ，而且在 **`for`** 中，如果沒有 **`break`** 、或，迴圈就不會終止 **`return`** **`goto`** *`statement`* 。

雖然語句的三個欄位 **`for`** 通常用於初始化、測試終止和遞增，但它們並不限於這些用途。 例如，下列程式碼會列印數字 0 到 4。 在此情況下， *`statement`* 是 null 語句：

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

## <a name="for-loops-and-the-c-standard"></a>`for`迴圈和 c + + 標準

C + + 標準指出迴圈結束之後，在迴圈中宣告的變數 **`for`** 應該超出範圍 **`for`** 。 例如：

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

根據預設，在[/ze](../build/reference/za-ze-disable-language-extensions.md)底下，在迴圈中宣告的變數會 **`for`** 保留在範圍內，直到 **`for`** 迴圈的封閉範圍結束為止。

[/Zc： forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)可啟用 for 迴圈中宣告之變數的標準行為，而不需要指定 `/Za` 。

您也可以使用迴圈的範圍差異來重新宣告底下的 **`for`** 變數 `/Ze` ，如下所示：

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

這種行為更嚴格地模仿迴圈中宣告之變數的標準行為 **`for`** ，而這需要迴圈中宣告的變數在迴圈 **`for`** 完成之後移出範圍。 在迴圈中宣告變數時 **`for`** ，編譯器會在內部將它升級為 **`for`** 迴圈封閉範圍中的區域變數。 即使已經有相同名稱的本機變數，它還是會升級。

## <a name="see-also"></a>另請參閱

[反復專案語句](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[while 語句（c + +）](../cpp/while-statement-cpp.md)<br/>
[do while 語句（c + +）](../cpp/do-while-statement-cpp.md)<br/>
[以範圍為基礎的 for 語句（c + +）](../cpp/range-based-for-statement-cpp.md)
