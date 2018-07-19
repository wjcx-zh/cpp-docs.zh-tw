---
title: switch 陳述式 （c + +） |Microsoft Docs
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
ms.openlocfilehash: 1d4ab0694936fe4ad25b3c56bf286e9416e4e935
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942915"
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
 *運算式*必須是整數型別或模稜兩可的轉換成整數類資料類型是類別類型。 中所述執行整數提升[標準轉換](standard-conversions.md)。  
  
 **切換**陳述式主體所組成的一系列**案例**標籤和選擇性**預設**標籤。 在任何兩個常數運算式**案例**陳述式可以評估為相同的值。 **預設**標籤只能出現一次。 標記陳述式不是語法需求，但**切換**陳述式是無意義，而不需要它們。   default 陳述式不需要出現在結尾，可以出現在 switch 陳述式主體中的任何位置。 case 或 default 標籤只能出現在 switch 陳述式內。  
  
 *常數運算式*每個**案例**標籤會轉換成的型別*運算式*相較於和*運算式*的相等。 控制權會傳遞給陳述式的**案例***常數運算式*的值相符*運算式*。 產生的行為如下表所示。  
  
### <a name="switch-statement-behavior"></a>switch 陳述式行為  
  
|條件|動作|  
|---------------|------------|  
|轉換的值與升級之控制運算式的值相符。|控制權會轉移至標籤後面的陳述式。|  
|沒有常數符合中的常數**案例**標籤;**預設**標籤已存在。|控制權會轉移到**預設**標籤。|  
|沒有常數符合中的常數**案例**標籤;**預設**標籤不存在。|控制權會轉移到之後的陳述式**切換**陳述式。|  
  
 如果找到相符運算式，控制項不會受到後續**案例**或是**預設**標籤。 [中斷](../cpp/break-statement-cpp.md)陳述式用來停止執行，並將控制權移轉給之後的陳述式**切換**陳述式。 不含**中斷**陳述式中，每個陳述式，從相符**案例**結尾標籤**切換**，包括**預設**，是執行。 例如:   
  
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
  
 在上述範例中，如果 `capa` 是大寫 `c`，則遞增 `A`。 **中斷**之後的陳述式`capa++`結束執行**切換**陳述式主體並將控制權傳遞至**雖然**迴圈。 不含**中斷**陳述式中，執行會 「 繼續 」 下一個標記的陳述式，以便`lettera`和`nota`也會遞增。 類似的目的由**中斷**陳述式`case 'a'`。 如果`c`是小寫`a`，`lettera`就會遞增並**中斷**陳述式會終止**切換**陳述式主體。 如果`c`不是`a`或是`A`，則**預設**陳述式。  

 **Visual Studio 2017 和更新版本：** (適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md))`[[fallthrough]]`屬性會指定在 C + + 17 標準。 它可以用於**切換**陳述式做為提示給編譯器 （或任何人讀取程式碼） 是該行為。 Visual c + + 編譯器目前不會在警告上 fallthrough 行為，因此這個屬性不會影響編譯器行為。 請注意，屬性會套用至空的陳述式內加上標籤的陳述式;換句話說，分號是必要的。

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

 **Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): switch 陳述式可能會引進並初始化的變數，其範圍僅限於在 switch 陳述式區塊：

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

 內部區塊**切換**陳述式可以包含有初始化的定義，只要它們是連線到 — 也就是不可能執行的所有路徑程式略過。 使用這些宣告引入的名稱有區域範圍。 例如:   
  
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
  
 A**切換**陳述式可以巢狀。 在此情況下，**案例**或是**預設**標籤相關聯的最接近**切換**含括它們的陳述式。  

 
## <a name="microsoft-specific"></a>Microsoft 特定的  
 Microsoft C 不會限制中的 case 值的數目**切換**陳述式。 此數目會受到可用記憶體的限制。 ANSI C 要求在至少 257 個 case 標籤中允許**切換**陳述式。  
  
 Microsoft C 預設會啟用 Microsoft 擴充功能。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項來停用這些擴充功能。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [選取範圍陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 
