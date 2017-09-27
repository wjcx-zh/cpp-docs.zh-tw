---
title: "break 陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- break_cpp
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2e016ccc90ef53ca5f269a73d3f5b7ed3185f550
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="break-statement-c"></a>break 陳述式 (C++)
`break` 陳述式會在最接近的封閉式迴圈或條件陳述式出現的位置結束執行。 控制會傳遞至陳述式結尾之後的陳述式 (如果有的話)。  
  
## <a name="syntax"></a>語法  
  
```  
break;  
```  
  
## <a name="remarks"></a>備註  
 `break`陳述式搭配條件式[切換](../cpp/switch-statement-cpp.md)陳述式與[不要](../cpp/do-while-statement-cpp.md)，[如](../cpp/for-statement-cpp.md)，和[時](../cpp/while-statement-cpp.md)迴圈陳述式。  
  
 在 `switch` 陳述式中，`break` 陳述式會使程式執行 `switch` 陳述式以外的下一個陳述式。 若沒有 `break` 陳述式，則會執行相符之 `case` 標籤到 `switch` 陳述式結尾之間的每一個陳述式，包含 `default` 子句。  
  
 在迴圈中，`break` 陳述式會結束最接近的封閉式 `do`、`for` 或 `while` 陳述式的執行。 控制會傳遞到已結束之陳述式的下一個陳述式 (如果有的話)。  
  
 在巢狀陳述式中，`break` 陳述式只會結束 `do`、`for`、`switch` 或立即將它封閉的 `while` 陳述式。 您可以使用 `return` 或 `goto` 陳述式從結構更複雜的巢狀結構轉移控制權。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何在 `break` 迴圈中使用 `for` 陳述式。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // An example of a standard for loop  
    for (int i = 1; i < 10; i++)  
    {  
        cout << i << '\n';  
        if (i == 4)  
            break;  
    }  
  
    // An example of a range-based for loop  
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};  
  
    for (int i : nums) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
    }  
}  
```  
  
```Output  
In each case:   
1  
2  
3  
```  
  
 下列程式碼示範如何在 `break` 迴圈和 `while` 迴圈中使用 `do`。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    int i = 0;  
  
    while (i < 10) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    }  
  
    i = 0;  
    do {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    } while (i < 10);  
}  
```  
  
```Output  
In each case:  
0123  
```  
  
 下列程式碼示範如何在 switch 陳述式中使用 `break`。 如果您想要個別處理每一個案例，每次都必須使用 `break`；如果不使用 `break`，程式碼執行繼續進行下一個案例。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
enum Suit{ Diamonds, Hearts, Clubs, Spades };  
  
int main() {  
  
    Suit hand;  
    . . .  
    // Assume that some enum value is set for hand  
    // In this example, each case is handled separately  
    switch (hand)  
    {  
    case Diamonds:  
        cout << "got Diamonds \n";  
        break;  
    case Hearts:  
        cout << "got Hearts \n";  
        break;  
    case Clubs:  
        cout << "got Clubs \n";  
        break;  
    case Spades:  
        cout << "got Spades \n";  
        break;  
    default:   
          cout << "didn't get card \n";  
    }  
    // In this example, Diamonds and Hearts are handled one way, and  
    // Clubs, Spades, and the default value are handled another way  
    switch (hand)  
    {  
    case Diamonds:  
    case Hearts:  
        cout << "got a red card \n";  
        break;  
    case Clubs:  
    case Spades:   
    default:  
        cout << "didn't get a red card \n";  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [continue 陳述式](../cpp/continue-statement-cpp.md)
