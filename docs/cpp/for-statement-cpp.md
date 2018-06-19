---
title: 陳述式 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38181a43134c35c4db1db3d78a79d3338934b7d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417180"
---
# <a name="for-statement-c"></a>for 陳述式 (C++)
重複執行陳述式，直到條件變成 false。 範圍架構 for 陳述式上的資訊，請參閱[範圍架構 for 陳述式 （c + +）](../cpp/range-based-for-statement-cpp.md)。  
  
## <a name="syntax"></a>語法  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>備註  
 使用 `for` 陳述式建構必須執行指定次數的迴圈。  
  
 如下表所示，`for` 陳述式包含三個選擇性部分。  
  
### <a name="for-loop-elements"></a>for 迴圈項目  
  
|語法名稱|何時執行|描述|  
|-----------------|-------------------|-----------------|  
|`init-expression`|之前的任何其他項目**如**陳述式，`init-expression`執行一次。 之後就會將控制項傳遞給 `cond-expression`。|通常用來初始迴圈索引。 它可能包含運算式或宣告。|  
|`cond-expression`|在執行 `statement` 的每個反覆項目之前，包括第一個反覆項目。 除非 `statement` 判斷值為 true (非零)，否則不會執行 `cond-expression`。|判斷值為整數類型的運算式或具有整數類型明確轉換的類別類型。 通常用來測試迴圈終止準則。|  
|`loop-expression`|每個 `statement` 反覆項目的結尾。 在 `loop-expression` 執行後會評估 `cond-expression`。|通常用來遞增迴圈索引。|  
  
 下列範例示範使用 `for` 陳述式的不同方式。  
  
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
  
 `init-expression` 和 `loop-expression` 可以包含以逗號分隔的多個陳述式。 例如:   
  
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
  
 A`for`時就會終止迴圈[中斷](../cpp/break-statement-cpp.md)，[傳回](../cpp/return-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md) (加上標籤的陳述式之外**如**迴圈) 內`statement`執行。 A[繼續](../cpp/continue-statement-cpp.md)陳述式中的`for`迴圈終止只有目前的反覆項目。  
  
 如果`cond-expression`已省略，就會被視為 true 和**如**迴圈將不會終止不`break`， `return`，或`goto`內`statement`。  
  
 雖然 `for` 陳述式的三個欄位通常用於初始化、測試終止及遞增，但它們不只限於這些用途。 例如，下列程式碼會列印數字 0 到 4。 在這個範例中，`statement` 是 Null 陳述式：  
  
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
 C++ 標準說明，在 `for` 迴圈中宣告的變數應在 `for` 迴圈結束時超出範圍。 例如:   
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 根據預設，在[/Ze](../build/reference/za-ze-disable-language-extensions.md)，在宣告的變數`for`迴圈會保留在範圍中，直到`for`迴圈的封閉範圍結束。  
  
 [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)啟用標準的行為，而不需要指定 /Za 宣告於 for 迴圈的變數。  
  
 您也可以使用 `for` 迴圈的範圍差異在 /Ze 底下重新宣告變數，如下所示：  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 此範例更精確地模擬在 `for` 迴圈中所宣告之變數的標準行為，也就是要求在 `for` 迴圈中宣告的變數於迴圈結束後超出範圍。 若變數是在 `for` 迴圈中宣告的，編譯器會在內部將它升級至 `for` 迴圈封閉範圍中的區域變數，即使已經有相同名稱的區域變數。  
  
## <a name="see-also"></a>另請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 (C++)](../cpp/while-statement-cpp.md)   
 [do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)