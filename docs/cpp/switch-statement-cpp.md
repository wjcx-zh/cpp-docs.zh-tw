---
title: switch 陳述式 (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160810"
---
# <a name="switch-statement-c"></a>switch 陳述式 (C++)

根據整數運算式的值，允許在多個程式碼區段中選取範圍。

## <a name="syntax"></a>語法

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>備註

*運算式*必須是整數類資料類型，或屬於明確轉換成整數類資料類型的類別類型。 整數提升的執行方式如[標準轉換](standard-conversions.md)中所述。

**Switch**語句主體是由一系列的**案例**標籤和選擇性的**預設**標籤所組成。 **Case**語句中不能有兩個常數運算式評估為相同的值。 **預設**標籤只能出現一次。 標記的語句不是語法需求，但**switch**語句沒有任何意義。   default 陳述式不需要出現在結尾，可以出現在 switch 陳述式主體中的任何位置。 case 或 default 標籤只能出現在 switch 陳述式內。

每個**case**標籤中的*常數運算式*會轉換成*運算式*的類型，並與*expression*比較是否相等。 控制權會傳遞給其**case** *常數運算式*符合*expression*值的語句。 產生的行為如下表所示。

### <a name="switch-statement-behavior"></a>switch 陳述式行為

|條件|動作|
|---------------|------------|
|轉換的值與升級之控制運算式的值相符。|控制權會轉移至標籤後面的陳述式。|
|沒有任何常數符合**case**標籤中的常數;有**預設**標籤。|控制項會傳送至**預設**標籤。|
|沒有任何常數符合**case**標籤中的常數;**預設**標籤不存在。|Control 會在**switch**語句之後傳送至語句。|

如果找到相符的運算式，後續的**案例**或**預設**標籤就不會阻礙控制項。 [Break](../cpp/break-statement-cpp.md)語句是用來停止執行，並將控制權轉移到**switch**語句之後的語句。 若沒有**break**語句，則會執行符合的**case**標籤到**switch**結尾的每個語句（包括**預設值**）。 例如：

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

在上述範例中，如果 `capa` 是大寫 `c`，則遞增 `A`。 `capa++` 之後的**break**語句會終止**switch**語句主體的執行，並將控制權傳遞給**while**迴圈。 若沒有**break**語句，執行會「流經」到下一個加上標籤的語句，因此 `lettera` 和 `nota` 也會遞增。 `case 'a'`的**break**語句會提供類似的目的。 如果 `c` 是小寫 `a`，`lettera` 會遞增，而**break**語句會終止**switch**語句主體。 如果 `c` 不是 `a` 或 `A`，則會執行**default**語句。

**Visual Studio 2017 和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)） `[[fallthrough]]` 屬性是以 c + + 17 標準指定。 它可以在**switch**語句中用來做為編譯器的提示（或讀取程式碼的任何人），以供預期的行為。 Microsoft C++編譯器目前不會對 fallthrough 行為發出警告，因此這個屬性不會影響編譯器行為。 請注意，屬性會套用至加上標籤之語句內的空白語句;換句話說，這是必要的分號。

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

**Visual Studio 2017 15.3 版和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： switch 語句可能會引進並初始化範圍限制為 switch 語句區塊的變數：

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

**Switch**語句的內部區塊可以包含有初始化的定義，只要它們可連線，也就是說，所有可能的執行路徑都不會略過。 使用這些宣告引入的名稱有區域範圍。 例如：

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

**Switch**語句可以嵌套。 在這種情況下，**大小寫**或**預設**標籤會與包圍它們的最接近的**switch**語句產生關聯。

**Microsoft 專屬**

Microsoft C 不會限制**switch**語句中 case 值的數目。 此數目會受到可用記憶體的限制。 ANSI C 需要**switch**語句中至少要有257的 case 標籤。

Microsoft C 預設會啟用 Microsoft 擴充功能。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項可停用這些擴充功能。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
