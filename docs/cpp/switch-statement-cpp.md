---
title: switch語句（c + +）
description: switchMicrosoft Visual Studio c + + 中標準 c + + 語句的參考。
ms.date: 04/25/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83389697"
---
# <a name="switch-statement-c"></a>`switch`語句（c + +）

根據整數運算式的值，允許在多個程式碼區段中選取範圍。

## <a name="syntax"></a>語法

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub><sup>C + + 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>備註

__`switch`__ 語句會 *`labeled-statement`* 根據的值，讓控制項在其語句主體中傳送至其中一個 *`condition`* 。

*`condition`* 必須有整數類型，或必須是明確轉換成整數類資料類型的類別類型。 整數升級會依照[標準轉換](standard-conversions.md)中的說明進行。

__`switch`__ 語句主體是由一系列 __`case`__ 標籤和選擇性 __`default`__ 標籤所組成。 *`labeled-statement`* 是下列其中一個標籤和後面的語句。 標記的語句不是語法需求，但是 __`switch`__ 語句沒有意義。 *`constant-expression`* 語句中的兩個值 __`case`__ 都不能評估為相同的值。 __`default`__ 標籤可能只會出現一次。 __`default`__ 語句通常會放在結尾，但它可以出現在語句主體中的任何位置 __`switch`__ 。 __`case`__ 或 __`default`__ 標籤只能出現在語句內 __`switch`__ 。

*`constant-expression`* 每個 __`case`__ 標籤中的會轉換成與相同類型的常數值 *`condition`* 。 然後，它會與 *`condition`* 相等進行比較。 控制權會傳遞給 __`case`__ *`constant-expression`* 符合值之值後面的第一個語句 *`condition`* 。 產生的行為如下表所示。

### <a name="switch-statement-behavior"></a>`switch`語句行為

| 條件 | 動作 |
|--|--|
| 轉換的值與升級之控制運算式的值相符。 | 控制權會轉移至標籤後面的陳述式。 |
| 沒有任何常數符合標籤中的常數 __`case`__ ; __`default`__ 標籤存在。 | 控制項會傳送至 __`default`__ 標籤。 |
| 沒有任何常數符合標籤中的常數 __`case`__ ; 不 __`default`__ 存在任何標籤。 | 控制權會傳送至語句之後的語句 __`switch`__ 。 |

如果找到相符的運算式，執行可以繼續到稍後 __`case`__ 或 __`default`__ 標籤。 [`break`](../cpp/break-statement-cpp.md)語句是用來停止執行，並將控制權轉移給語句後面的語句 __`switch`__ 。 如果沒有 __`break`__ 語句， __`case`__ 則會執行符合的標籤到結尾的每個語句 __`switch`__ （包括 __`default`__ ）。 例如：

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

在上述範例中，如果 `uppercase_A` 是大寫 `c`，則遞增 `'A'`。 __`break`__ 之後的語句會 `uppercase_A++` 終止 __`switch`__ 語句主體的執行，並將控制權傳遞給 __`while`__ 迴圈。 如果沒有 __`break`__ 語句，執行會「流經」到下一個加上標籤的語句，因此 `lowercase_a` 和 `other` 也會遞增。 的語句會提供類似的目的 __`break`__ `case 'a'` 。 如果 `c` 是小寫 `'a'` ， `lowercase_a` 會遞增，而 __`break`__ 語句會終止 __`switch`__ 語句主體。 如果 `c` 不是 `'a'` 或 `'A'` ，則 __`default`__ 會執行語句。

**Visual Studio 2017 和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)） `[[fallthrough]]` 屬性是以 c + + 17 標準指定。 您可以在語句中使用它 __`switch`__ 。 這是編譯器的提示，或讀取程式碼的任何人，都是故意的行為。 Microsoft c + + 編譯器目前不會警告 fallthrough 行為，因此這個屬性不會影響編譯器行為。 在此範例中，屬性會套用至未結束標記之語句內的空白語句。 換句話說，這是必要的分號。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 15.3 版和更新**版本（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）。 __`switch`__ 語句可能會有一個以 *`init-statement`* 分號結尾的子句。 它會引進並初始化變數，其範圍僅限於語句的區塊 __`switch`__ ：

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

語句的內部區塊 __`switch`__ 可以包含具有初始化運算式的定義，只要它們可連線*reachable*，也就是所有可能的執行路徑都不會略過。 使用這些宣告引入的名稱有區域範圍。 例如：

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

__`switch`__ 語句可以嵌套。 當加上 nested 時， __`case`__ 或 __`default`__ 標籤會與包圍它們的最接近語句產生關聯 __`switch`__ 。

### <a name="microsoft-specific-behavior"></a>Microsoft 特有的行為

Microsoft c + + 不會限制 __`case`__ 語句中的值數目 __`switch`__ 。 此數目會受到可用記憶體的限制。

## <a name="see-also"></a>請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
