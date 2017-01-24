---
title: "decltype (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "decltype"
  - "decltype_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decltype 運算子"
  - "運算子 [C++], decltype"
  - "運算子 [C++], 推算運算式類型"
  - "運算子 [C++], 運算式類型"
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# decltype (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`decltype` 類型規範會產生指定之運算式的類型。  `decltype` 類型規範搭配 [auto 關鍵字](../cpp/auto-cpp.md) 對於主要是撰寫樣板程式庫的開發人員很有用。  使用 `auto` 和 `decltype` 來宣告其傳回類型視樣板引數而定的樣板函式。  或是使用 `auto` 和 `decltype` 來宣告包裝對其他函式的呼叫，再傳回所包裝函式之類型的樣板函式。  
  
## 語法  
  
```  
decltype( expression )  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`expression`|一個運算式。  如需詳細資訊，請參閱[運算式](../cpp/expressions-cpp.md)。|  
  
## 傳回值  
 `expression` 參數的類型。  
  
## 備註  
 `decltype` 類型規範在 Visual C\+\+ 2010 \(含\) 以後版本支援，可以搭配原生或 Managed 程式碼使用。  Visual Studio 2015 和更新版本支援 `decltype(auto)` \(C\+\+14\)。  
  
 編譯器會使用下列規則來判斷 `expression` 參數的類型。  
  
-   如果 `expression` 參數是識別項或 [類別成員存取](../cpp/member-access-operators-dot-and.md)，`decltype(``expression``)` 是由 `expression` 命名的實體類型。  如果沒有這種實體或 `expression` 參數命名了一組多載函式，編譯器會產生錯誤訊息。  
  
-   如果 `expression` 參數是對函式或多載運算子函式的呼叫，`decltype(``expression``)` 會是函式的傳回類型。  在多載運算子周圍的括號會被忽略。  
  
-   如果 `expression` 參數是一個 [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)，則 `decltype(``expression``)` 會是 `expression` 的類型。  如果 `expression` 參數是[左值](../cpp/lvalues-and-rvalues-visual-cpp.md)，`decltype`\(`expression`\) 會是一個 [左值參考](../cpp/lvalue-reference-declarator-amp.md) 類型的`expression`。  
  
 下列程式碼範例示範 `decltype` 類型規範的一些用法。  首先，假設您撰寫了下列陳述式。  
  
```  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 接著，檢查由下表中四個 `decltype` 陳述式所傳回的類型。  
  
|陳述式|類型|附註|  
|---------|--------|--------|  
|`decltype(fx());`|`const int&&`|對 [右值參考](../cpp/rvalue-reference-declarator-amp-amp.md) 的`const int`。|  
|`decltype(var);`|`int`|變數 `var` 的類型。|  
|`decltype(a->x);`|`double`|成員存取的類型。|  
|`decltype((a->x));`|`const double&`|括號內的陳述式會評估為運算式而不是成員存取。  而且，因為 `a` 已宣告為 `const` 指標，所以其類型會是 `const double` 的參考。|  
  
## Decltype 和 Auto  
 在 C\+\+14 中，您可以使用沒有尾端傳回類型的  `decltype(auto)` 來宣告其傳回類型取決於樣板引數的樣板函式。  
  
 在 C\+\+11 中，您可以搭配使用尾端傳回類型上的 `decltype` 類型規範與 `auto` 關鍵字，來宣告其傳回類型視樣板引數而定的樣板函式。  例如，請考慮下列程式碼範例，其中樣板函式的傳回類型取決於樣板引數的類型。  在程式碼範例中，*未知*預留位置表示不能指定傳回類型。  
  
```  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 `decltype` 類型規範的引入可讓開發人員取得樣板函式傳回的運算式類型。  使用稍後顯示的「*替代函式宣告語法*」\(Alternative Function Declaration Syntax\)、`auto` 關鍵字和 `decltype` 類型規範來宣告一個「*晚期指定*」\(Late\-Specified\) 的傳回類型。  晚期指定的傳回類型是在編譯宣告時決定，而不是在撰寫程式時決定。  
  
 下列原型說明替代函式宣告的語法。  請注意，`const` 和 `volatile` 限定詞，以及 `throw` [例外狀況規格](../cpp/exception-specifications-throw-cpp.md)為選擇性。  *function\_body* 預留位置代表指定函式作用的複合陳述式。  基於撰寫程式碼的最佳作法，`decltype` 陳述式中的*運算式*預留位置應該要與 *function\_body* 中 `return` 陳述式指定的運算式相符 \(如果有的話\)。  
  
 `auto` *function\_name*`(`*參數*opt`)` `const`opt `volatile`opt `−>` `decltype(`*運算式*`)` `throw`opt `{`*function\_body*`};`  
  
 下列程式碼範例中，`myFunc` 樣板函式的晚期指定傳回類型由 `t` 和 `u` 樣板引數的類型決定。  基於撰寫程式碼的最佳作法，程式碼範例也使用右值參考和 `forward` 函式樣板，其支援「*完美轉送*」\(Perfect Forwarding\)。  如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
```  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## decltype 和轉送函式 \(C\+\+11\)  
 轉送函式會包裝對其他函式的呼叫。  試想一個轉送其引數，或者包含這些引數的運算式結果到其他函式的函式樣板。  此外，轉送函式會傳回呼叫其他函式的結果。  在這個案例中，轉送函式的傳回類型應該會與包裝函式的傳回類型相同。  
  
 在這個案例中，您必須使用 `decltype` 類型規範才能撰寫適當的類型運算式。  `decltype` 類型規範可進行泛型轉送函式，因為它不會遺失函式是否傳回參考類型的必要資訊。  如需轉送函式的程式碼範例，請參閱先前的 `myFunc` 樣板函式範例。  
  
## 範例  
 下列程式碼範例會宣告樣板函式 `Plus()` 的晚期指定傳回類型。  `Plus` 函式處理其使用 `operator+` 多載的兩個運算元。  因此，加號運算子 \(\+\) 的解譯和 `Plus` 函式的傳回類型取決於函式引數的類型。  
  
```  
// decltype_1.cpp  
// compile with: /EHsc  
//  
#include "stdafx.h"  
#include <iostream>  
#include <string>  
#include <utility>  
#include <iomanip>  
  
using namespace std;  
  
template<typename T1, typename T2>  
auto Plus(T1&& t1, T2&& t2) ->   
   decltype(forward<T1>(t1) + forward<T2>(t2))  
{  
   return forward<T1>(t1) + forward<T2>(t2);  
}  
  
class X  
{  
   friend X operator+(const X& x1, const X& x2)  
   {  
      return X(x1.m_data + x2.m_data);  
   }  
  
public:  
   X(int data) : m_data(data) {}  
   int Dump() const { return m_data;}  
private:  
   int m_data;  
};  
  
int main()  
{  
   // Integer   
   int i = 4;  
   cout <<   
      "Plus(i, 9) = " <<   
      Plus(i, 9) << endl;  
  
   // Floating point  
   float dx = 4.0;  
   float dy = 9.5;  
   cout <<     
      setprecision(3) <<   
      "Plus(dx, dy) = " <<  
      Plus(dx, dy) << endl;  
  
   // String        
   string hello = "Hello, ";  
   string world = "world!";  
   cout << Plus(hello, world) << endl;  
  
   // Custom type  
   X x1(20);  
   X x2(22);  
   X x3 = Plus(x1, x2);  
   cout <<   
      "x3.Dump() = " <<   
      x3.Dump() << endl;  
}  
```  
  
 **輸出**  
  
 這個程式碼範例會產生下列結果。  
  
 13  
  
 13.5  
  
 Hello, world\!  
  
 42  
  
## 需求  
 Visual C\+\+ 2010 \(含\) 以後版本。  
  
 decltype\(auto\) 需要 Visual Studio 2015 \(含\) 以後版本  
  
## 請參閱  
 [\(NOTINBUILD\)Simple Type Names](http://msdn.microsoft.com/zh-tw/333f45cb-2c72-4d81-8e59-e346b05f55e3)