---
title: 切換陳述式 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cea2c7e4bff895f9ccabc044ed5b7f5ae506b32
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
 *運算式*必須是整數類型或明確轉換成整數類資料類型是類別類型。 中所述，會執行整數提升[標準轉換](standard-conversions.md)。  
  
 `switch`陳述式主體包含的一系列**案例**標籤和選擇性**預設**標籤。 在任何兩個常數運算式**案例**陳述式可以評估為相同的值。 **預設**標籤只能出現一次。 有標記的陳述式不是語法需求，但是 `switch` 陳述式沒有它們就沒有意義。   default 陳述式不需要出現在結尾，可以出現在 switch 陳述式主體中的任何位置。 case 或 default 標籤只能出現在 switch 陳述式內。  
  
 *常數運算式*中每個**案例**標籤會轉換成的型別*運算式*相較於和*運算式*的相等。 控制權會傳遞給陳述式的**案例***常數運算式*符合值的*運算式*。 產生的行為如下表所示。  
  
### <a name="switch-statement-behavior"></a>switch 陳述式行為  
  
|條件|動作|  
|---------------|------------|  
|轉換的值與升級之控制運算式的值相符。|控制權會轉移至標籤後面的陳述式。|  
|沒有任何常數符合中的常數**案例**標籤;**預設**標籤已存在。|控制權會轉移到**預設**標籤。|  
|沒有任何常數符合中的常數**案例**標籤。**預設**標籤不存在。|控制權會轉移至 `switch` 陳述式之後的陳述式。|  
  
 如果找到相符的運算式，控制不會受到後續**案例**或**預設**標籤。 [中斷](../cpp/break-statement-cpp.md)陳述式用來停止執行，並將控制權轉移到之後的陳述式`switch`陳述式。 不含**中斷**陳述式中，每個陳述式從相符**案例**結尾的標籤`switch`，包括**預設**，會執行。 例如:   
  
```  
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
  
 在上述範例中，如果 `capa` 是大寫 `c`，則遞增 `A`。 在 `break` 之後的 `capa++` 陳述式會結束 `switch` 陳述式主體的執行，並將控制權傳遞給 `while` 迴圈。 不含`break`陳述式中，執行 「 落 「 下一個標記的陳述式，以便`lettera`和`nota`也會遞增。 `break` 的 `case 'a'` 陳述式也提供類似的用途。 如果 `c` 是小寫 `a`，`lettera` 會遞增，而 `break` 陳述式會結束 `switch` 陳述式主體。 如果 `c` 不是 `a` 或 `A`，就會執行 `default` 陳述式。  

 **2017 和更新版本的 visual Studio:** (適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` C + + 17 標準中所指定的屬性。 它可以用於`switch`陳述式做為提示編譯器 （或任何人閱讀程式碼） 是該年秋季透過行為。 Visual c + + 編譯器目前不會在警告上 fallthrough 行為，所以此屬性不有任何效果編譯器行為。 請注意，屬性會套用至空的陳述式加上標籤的陳述式; 內換句話說，分號是必要的。

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

 **Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): switch 陳述式可能會引進並初始化其範圍僅限於在 switch 陳述式區塊的變數：

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

 只要初始化是可執行到的，也就是所有可能的執行路徑都不略過，`switch` 陳述式的內部區塊可以包含有初始化的定義。 使用這些宣告引入的名稱有區域範圍。 例如:   
  
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
  
 `switch` 陳述式可以是巢狀結構。 在這種情況下，**案例**或**預設**標籤關聯的最接近`switch`含括它們的陳述式。  

 
## <a name="microsoft-specific"></a>Microsoft 特定的  
 Microsoft C 不會限制 `switch` 陳述式中 case 值的數目。 此數目會受到可用記憶體的限制。 ANSI C 要求在 `switch` 陳述式中允許至少 257 個 case 標籤。  
  
 Microsoft C 預設會啟用 Microsoft 擴充功能。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項，來停用這些擴充功能。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 