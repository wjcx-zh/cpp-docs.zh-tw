---
title: :::no-loc(switch):::語句（c + +）
description: :::no-loc(switch):::Microsoft Visual Studio c + + 中標準 c + + 語句的參考。
ms.date: 04/25/2020
f1_keywords:
- :::no-loc(default):::_cpp
- :::no-loc(switch):::_cpp
- :::no-loc(case):::_cpp
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C++]'
- ':::no-loc(case)::: keyword [C++], in :::no-loc(switch)::: statements'
- ':::no-loc(default)::: keyword [C++]'
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
- ':::no-loc(while):::'
- ':::no-loc(opt):::'
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d71989b6d8af0213c4cd6d4fbd8d5a84b318701a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223586"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`語句（c + +）

根據整數運算式的值，允許在多個程式碼區段中選取範圍。

## <a name="syntax"></a>語法

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;**`:::no-loc(switch):::`**&nbsp;**`(`**&nbsp;*`init-statement`*<sub>:::no-loc(opt):::</sub><sup>C + + 17</sup>&nbsp;*`condition`*&nbsp;**`)`**&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>:::no-loc(opt):::</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>備註

**`:::no-loc(switch):::`** 語句會 *`labeled-statement`* 根據的值，讓控制項在其語句主體中傳送至其中一個 *`condition`* 。

*`condition`* 必須有整數類型，或必須是明確轉換成整數類資料類型的類別類型。 整數升級會依照[標準轉換](standard-conversions.md)中的說明進行。

**`:::no-loc(switch):::`** 語句主體是由一系列 **`:::no-loc(case):::`** 標籤和 :::no-loc(opt)::: ional **`:::no-loc(default):::`** 標籤所組成。 *`labeled-statement`* 是下列其中一個標籤和後面的語句。 標記的語句不是語法需求，但是 **`:::no-loc(switch):::`** 語句沒有意義。 *`constant-expression`* 語句中的兩個值 **`:::no-loc(case):::`** 都不能評估為相同的值。 **`:::no-loc(default):::`** 標籤可能只會出現一次。 **`:::no-loc(default):::`** 語句通常會放在結尾，但它可以出現在語句主體中的任何位置 **`:::no-loc(switch):::`** 。 **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 標籤只能出現在語句內 **`:::no-loc(switch):::`** 。

*`constant-expression`* 每個 **`:::no-loc(case):::`** 標籤中的會轉換成與相同類型的常數值 *`condition`* 。 然後，它會與 *`condition`* 相等進行比較。 控制權會傳遞給 **`:::no-loc(case):::`** *`constant-expression`* 符合值之值後面的第一個語句 *`condition`* 。 產生的行為如下表所示。

### <a name="no-locswitch-statement-behavior"></a>`:::no-loc(switch):::`語句行為

| 條件 | 動作 |
|--|--|
| 轉換的值與升級之控制運算式的值相符。 | 控制權會轉移至標籤後面的陳述式。 |
| 沒有任何常數符合標籤中的常數 **`:::no-loc(case):::`** ; **`:::no-loc(default):::`** 標籤存在。 | 控制項會傳送至 **`:::no-loc(default):::`** 標籤。 |
| 沒有任何常數符合標籤中的常數 **`:::no-loc(case):::`** ; 不 **`:::no-loc(default):::`** 存在任何標籤。 | 控制權會傳送至語句之後的語句 **`:::no-loc(switch):::`** 。 |

如果找到相符的運算式，執行可以繼續到稍後 **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 標籤。 [`:::no-loc(break):::`](../cpp/:::no-loc(break):::-statement-cpp.md)語句是用來停止執行，並將控制權轉移給語句後面的語句 **`:::no-loc(switch):::`** 。 如果沒有 **`:::no-loc(break):::`** 語句， **`:::no-loc(case):::`** 則會執行符合的標籤到結尾的每個語句 **`:::no-loc(switch):::`** （包括 **`:::no-loc(default):::`** ）。 例如：

```cpp
// :::no-loc(switch):::_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, other;
   char c;
   upper:::no-loc(case):::_A = lower:::no-loc(case):::_a = other = 0;

   :::no-loc(while)::: ( c = *buffer++ )   // Walks buffer until NULL
   {
      :::no-loc(switch)::: ( c )
      {
         :::no-loc(case)::: 'A':
            upper:::no-loc(case):::_A++;
            :::no-loc(break):::;
         :::no-loc(case)::: 'a':
            lower:::no-loc(case):::_a++;
            :::no-loc(break):::;
         :::no-loc(default)::::
            other++;
      }
   }
   printf_s( "\nUpper:::no-loc(case)::: A: %d\nLower:::no-loc(case)::: a: %d\nTotal: %d\n",
      upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, (upper:::no-loc(case):::_A + lower:::no-loc(case):::_a + other) );
}
```

在上述範例中， `upper:::no-loc(case):::_A` 如果 `c` 是上限，會遞增 :::no-loc(case)::: `'A'` 。 **`:::no-loc(break):::`** 之後的語句會 `upper:::no-loc(case):::_A++` 終止 **`:::no-loc(switch):::`** 語句主體的執行，並將控制權傳遞給 **`:::no-loc(while):::`** 迴圈。 如果沒有 **`:::no-loc(break):::`** 語句，執行會「流經」到下一個加上標籤的語句，因此 `lower:::no-loc(case):::_a` 和 `other` 也會遞增。 的語句會提供類似的目的 **`:::no-loc(break):::`** `:::no-loc(case)::: 'a'` 。 如果較 `c` 低 :::no-loc(case)::: `'a'` ， `lower:::no-loc(case):::_a` 會遞增，而且 **`:::no-loc(break):::`** 語句會終止 **`:::no-loc(switch):::`** 語句主體。 如果 `c` 不是 `'a'` 或 `'A'` ，則 **`:::no-loc(default):::`** 會執行語句。

**Visual Studio 2017 和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)） `[[fallthrough]]` 屬性是以 c + + 17 標準指定。 您可以在語句中使用它 **`:::no-loc(switch):::`** 。 這是編譯器的提示，或讀取程式碼的任何人，都是故意的行為。 Microsoft c + + 編譯器目前不會警告 fallthrough 行為，因此這個屬性不會影響編譯器行為。 在此範例中，屬性會套用至未結束標記之語句內的空白語句。 換句話說，這是必要的分號。

```cpp
int main()
{
    int n = 5;
    :::no-loc(switch)::: (n)
    {

    :::no-loc(case)::: 1:
        a();
        :::no-loc(break):::;
    :::no-loc(case)::: 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    :::no-loc(case)::: 3:
        c();
        :::no-loc(break):::;
    :::no-loc(default)::::
        d();
        :::no-loc(break):::;
    }

    return 0;
}
```

**Visual Studio 2017 15.3 版和更新**版本（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）。 **`:::no-loc(switch):::`** 語句可能會有一個以 *`init-statement`* 分號結尾的子句。 它會引進並初始化變數，其範圍僅限於語句的區塊 **`:::no-loc(switch):::`** ：

```cpp
    :::no-loc(switch)::: (Gadget gadget(args); auto s = gadget.get_status())
    {
    :::no-loc(case)::: status::good:
        gadget.zip();
        :::no-loc(break):::;
    :::no-loc(case)::: status::bad:
        throw BadGadget();
    };
```

語句的內部區塊 **`:::no-loc(switch):::`** 可以包含具有初始化運算式的定義，只要它們可連線*reachable*，也就是所有可能的執行路徑都不會略過。 使用這些宣告引入的名稱有區域範圍。 例如：

```cpp
// :::no-loc(switch):::_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    :::no-loc(switch):::( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    :::no-loc(case)::: 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        :::no-loc(break):::;

    :::no-loc(case)::: 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        :::no-loc(break):::;

    :::no-loc(default)::::
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        :::no-loc(break):::;
    }
}
```

**`:::no-loc(switch):::`** 語句可以嵌套。 當加上 nested 時， **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 標籤會與包圍它們的最接近語句產生關聯 **`:::no-loc(switch):::`** 。

### <a name="microsoft-specific-behavior"></a>Microsoft 特有的行為

Microsoft c + + 不會限制 **`:::no-loc(case):::`** 語句中的值數目 **`:::no-loc(switch):::`** 。 此數目會受到可用記憶體的限制。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
