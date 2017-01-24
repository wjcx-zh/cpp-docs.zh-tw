---
title: "for 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for 關鍵字 [C++]"
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# for 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重複執行陳述式，直到條件變成 false。  如需範圍架構 for 陳述式的詳細資訊，請參閱[以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)。  
  
## 語法  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## 備註  
 使用 `for` 陳述式建構必須執行指定次數的迴圈。  
  
 如下表所示，`for` 陳述式包含三個選擇性部分。  
  
### for 迴圈項目  
  
|語法名稱|何時執行|描述|  
|----------|----------|--------|  
|`init-expression`|在 **for** 陳述式之前的任何其他項目，`init-expression` 只執行一次。  之後就會將控制項傳遞給 `cond-expression`。|通常用來初始迴圈索引。  它可能包含運算式或宣告。|  
|`cond-expression`|在執行 `statement` 的每個反覆項目之前，包括第一個反覆項目。  除非 `cond-expression` 判斷值為 true \(非零\)，否則不會執行 `statement`。|判斷值為整數類型的運算式或具有整數類型明確轉換的類別類型。  通常用來測試迴圈終止準則。|  
|`loop-expression`|每個 `statement` 反覆項目的結尾。  在 `loop-expression` 執行後會評估 `cond-expression`。|通常用來遞增迴圈索引。|  
  
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
  
 `init-expression` 和 `loop-expression` 可以包含以逗號分隔的多個陳述式。  例如：  
  
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
  
 `for` 迴圈會在執行 `statement` 中的 [break](../cpp/break-statement-cpp.md)、[return](../cpp/return-statement-cpp.md) 或 [goto](../cpp/goto-statement-cpp.md) \(至 **for** 迴圈外標記的陳述式\) 時終止。  `for` 迴圈中的 [continue](../cpp/continue-statement-cpp.md) 陳述式只有終止目前的反覆項目。  
  
 如果省略 `cond-expression`，會將其視為 true，若 `statement` 中沒有 `break`、`return` 或 `goto`，**for** 迴圈不會終止。  
  
 雖然 `for` 陳述式的三個欄位通常用於初始化、測試終止及遞增，但它們不只限於這些用途。  例如，下列程式碼會列印數字 0 到 4。  在這個範例中，`statement` 是 Null 陳述式：  
  
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
  
## for 迴圈和 C\+\+ 標準  
 C\+\+ 標準說明，在 `for` 迴圈中宣告的變數應在 `for` 迴圈結束時超出範圍。  例如：  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 根據預設，在 [\/Ze](../build/reference/za-ze-disable-language-extensions.md)下，在 `for` 迴圈中宣告的變數會保持在範圍中，直到 `for` 迴圈的封閉範圍結束。  
  
 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 允許在 for 迴圈中宣告之變數的標準行為，而不需要指定 \/Za。  
  
 您也可以使用 `for` 迴圈的範圍差異在 \/Ze 底下重新宣告變數，如下所示：  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 此範例更精確地模擬在 `for` 迴圈中所宣告之變數的標準行為，也就是要求在 `for` 迴圈中宣告的變數於迴圈結束後超出範圍。  若變數是在 `for` 迴圈中宣告的，編譯器會在內部將它升級至 `for` 迴圈封閉範圍中的區域變數，即使已經有相同名稱的區域變數。  
  
## 請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [do\-while 陳述式 \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)