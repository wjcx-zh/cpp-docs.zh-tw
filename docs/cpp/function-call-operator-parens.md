---
title: "函式呼叫運算子：() | Microsoft Docs"
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
  - "( ) 函式呼叫運算子"
  - "() 函式呼叫運算子"
  - "函式呼叫運算子 ()"
  - "函式呼叫, C++ 函式"
  - "函式呼叫, operator"
  - "函式 [C++], 函式呼叫運算子"
  - "後置運算子"
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式呼叫運算子：()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函式呼叫運算子後面的後置運算式 **\( \)** 用於指定函式呼叫。  
  
## 語法  
  
```  
  
postfix-expression   
( [argument-expression-list ] )  
```  
  
## 備註  
 函式呼叫運算子的引數是以逗號分隔的零或多個運算式，即函式的實際引數。  
  
 *postfix\-expression* 必須評估為函式位址 \(例如，函式識別項或函式指標的值\)，而 *argument\-expression\-list* 是運算式的清單 \(以逗號分隔\)，其值 \(「引數」\) 會傳遞至函式。  *argument\-expression\-list* 引數可以是空的。  
  
 *postfix\-expression* 必須是下列其中一種類型：  
  
-   傳回類型 `T` 的函式。  如以下範例宣告所示  
  
    ```  
    T func( int i )  
    ```  
  
-   傳回類型 `T` 之函式的指標。  如以下範例宣告所示  
  
    ```  
    T (*func)( int i )  
    ```  
  
-   傳回類型 `T` 之函式的參考。  如以下範例宣告所示  
  
    ```  
    T (&func)(int i)  
    ```  
  
-   傳回類型 `T` 的成員指標函式取值 \(Dereference\)。  函式呼叫的範例如下  
  
    ```  
    (pObject->*pmf)();  
    (Object.*pmf)();  
    ```  
  
## 範例  
 下列範例呼叫具有三個引數的標準程式庫函式 `strcat_s`：  
  
```  
// expre_Function_Call_Operator.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
  
// STL name space  
using namespace std;  
  
int main()  
{  
    enum  
    {  
        sizeOfBuffer = 20  
    };  
  
    char s1[ sizeOfBuffer ] = "Welcome to ";  
    char s2[ ] = "C++";  
  
    strcat_s( s1, sizeOfBuffer, s2 );  
  
    cout << s1 << endl;  
}  
```  
  
  **Welcome to C\+\+**   
## 函式呼叫結果  
 除非函式宣告為參考類型，否則函式呼叫會判斷值為右值。  具有參考傳回類型的函式會評估為左值，而且可以在指派陳述式的左邊使用，如下所示：  
  
```  
// expre_Function_Call_Results.cpp  
// compile with: /EHsc  
#include <iostream>  
class Point  
{  
public:  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
using namespace std;  
int main()  
{  
    Point ThePoint;  
  
    ThePoint.x() = 7;           // Use x() as an l-value.  
    unsigned y = ThePoint.y();  // Use y() as an r-value.  
  
    // Use x() and y() as r-values.  
    cout << "x = " << ThePoint.x() << "\n"  
         << "y = " << ThePoint.y() << "\n";  
}  
```  
  
 上述程式碼會定義稱為 `Point` 的類別，其中包含表示 *x* 和 *y* 座標的私用資料物件。  這些資料物件必須經過修改，而且必須擷取其值。  這個程式只是這種類別的數項設計之一，使用 `GetX` 和 `SetX` 或 `GetY` 和 `SetY` 則是另一種可能的設計方式。  
  
 傳回類別類型、類別類型的指標或類別類型的參考之函式可以做為成員選擇運算子的左運算元使用。  因此，下列程式碼是合法的：  
  
```  
// expre_Function_Results2.cpp  
class A {  
public:  
   A() {}  
   A(int i) {}  
   int SetA( int i ) {  
      return (I = i);  
   }  
  
   int GetA() {  
      return I;  
   }  
  
private:  
   int I;  
};  
  
A func1() {  
   A a = 0;  
   return a;  
}  
  
A* func2() {  
   A *a = new A();  
   return a;  
}  
  
A& func3() {  
   A *a = new A();  
   A &b = *a;  
   return b;  
}  
  
int main() {  
   int iResult = func1().GetA();  
   func2()->SetA( 3 );  
   func3().SetA( 7 );  
}  
```  
  
 函式可以透過遞迴方式呼叫。  如需函式宣告的詳細資訊，請參閱[函式規範](../misc/function-specifiers.md)和[成員函式](../misc/member-functions-cpp.md)。  相關資料位於[程式和連結](../cpp/program-and-linkage-cpp.md)中。  
  
## 請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [函式呼叫](../c-language/function-call-c.md)   
 [\(NOTINBUILD\) Function Declarations](http://msdn.microsoft.com/zh-tw/3f9b4e14-60d2-47c1-acd8-4fa8fc988be7)