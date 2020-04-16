---
title: switch語句 (C++)
description: 在 Microsoftswitch視覺 工作室 C++中引用標準 C++語句。
ms.date: 04/15/2020
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
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480828"
---
# <a name="opno-locswitch-statement-c"></a>switch語句 (C++)

根據整數運算式的值，允許在多個程式碼區段中選取範圍。

## <a name="syntax"></a>語法

> **`switch (`**\[*初始化***`;`**=*運算式***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***常量運算***`:`***statement*\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***語句*|\
> **`}`**

## <a name="remarks"></a>備註

*表達式*必須具有積分類型,或者是具有明確轉換為積分類型的類類型。 積分提升如[標準轉換](standard-conversions.md)中所述。

語句**switch** 正文由一**case** 系列 標籤和**default** 可選 標籤組成。 總之,標籤后的聲明稱為*標記*語句。 標記的語句不是語法要求,但沒有這些語句則**switch** 毫無意義。 語句中的**case** 兩個常量運算式不能計算為同一值。 標籤**default** 只能顯示一次。 語句**default** 通常放在末尾,但它可以**switch** 出現在 語句正文的任意位置。 **case** 或**default** 標籤只能**switch** 出現在語句中。

每個**case** 標籤中的*常量運算式*將轉換為*運算式*的類型。 然後,它與相等*表達式*進行比較。 控制件傳遞給常**case***量表達式*與*運算式*的值匹配的語句。 產生的行為如下表所示。

### <a name="switch-statement-behavior"></a>切換敘述行為

| 條件 | 動作 |
|--|--|
| 轉換的值與升級之控制運算式的值相符。 | 控制權會轉移至標籤後面的陳述式。 |
| 沒有任何常量與標籤中的**case** 常量匹配;存在**default** 標籤。 | 控件將轉移到標籤。 **default** |
| 沒有任何常量與標籤中的**case** 常量匹配;不存在**default** 標籤。 | 控件在**switch** 語句后傳輸到語句。 |

如果找到匹配的表達式,則執行可以繼續執行到以後**case****default** 或標籤。 語句[`break`](../cpp/break-statement-cpp.md)用於停止執行**switch** 並在 語句之後將控制權轉移到語句。 如果沒有語句**break**,則執行從**case** 匹配**switch** 標籤到 的末尾的每個語句**default**,包括 。 例如：

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

在上述範例中，如果 `uppercase_A` 是大寫 `c`，則遞增 `'A'`。 語句**break** 取消`uppercase_A++`**switch** 後 敘述的文句標章與控制器的**while** 執行會傳遞到迴圈 。 如果沒有語句**break**,執行將"通過"到下一個標記的語句,`lowercase_a`以便`other`並且 也將遞增。 宣告也提供**break** 類似的目的`case 'a'`。 如果`c`是小`'a'`寫`lowercase_a`, 則**break** 遞增,**switch** 語句終止 語句正文。 如果`c``'a'`不是`'A'`或**default**,則執行語句。

**Visual Studio 2017 及更高版本:(** 可用於[/std:c_17)](../build/reference/std-specify-language-standard-version.md)屬性`[[fallthrough]]`在 C++17 標準中指定。 您可以在語句中**switch** 使用它。 這是向編譯器或讀取代碼的任何人的提示,即通過行為是有意的。 Microsoft C++編譯器當前不警告失敗行為,因此此屬性對編譯器行為沒有影響。 在此示例中,該屬性將應用於未終止標記語句中的空語句。 換句話說,分號是必要的。

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

**Visual Studio 2017 版本 15.3 及更高版本**(隨[/std:c++17 提供](../build/reference/std-specify-language-standard-version.md))。 語句switch可能具有*初始化*子句。 它引入並初始化了一個變數,其範圍僅限於switch語句塊:

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

**switch** 語句的內部塊可以包含具有初始化的定義,只要它們*可到達*,也就是說,不會繞過所有可能的執行路徑。 使用這些宣告引入的名稱有區域範圍。 例如：

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

可以**switch** 嵌套語句。 巢狀時,**case****default** 或標籤與包含它們的最**switch** 接近 的語句相關聯。

### <a name="microsoft-specific-behavior"></a>特定於微軟的行為

Microsoft C**case****switch** 不限制 語句中的值數。 此數目會受到可用記憶體的限制。 ANSI C 要求在語句**case** 中至少 允許**switch** 257 個標籤。

default對於 Microsoft C,微軟擴展已啟用。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項禁用這些擴展。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
