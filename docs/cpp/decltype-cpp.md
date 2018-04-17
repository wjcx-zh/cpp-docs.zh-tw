---
title: decltype （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- decltype_cpp
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee3c83512929e4592a5ee75b954bc6c19f52f448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="decltype--c"></a>decltype （C++）
`decltype` 類型規範會產生指定之運算式的類型。 `decltype`搭配類型規範， [auto 關鍵字](../cpp/auto-cpp.md)，適合主要用於開發人員撰寫樣板程式庫。 使用 `auto` 和 `decltype` 來宣告其傳回類型視樣板引數而定的樣板函式。 或是使用 `auto` 和 `decltype` 來宣告包裝對其他函式的呼叫，再傳回所包裝函式之類型的樣板函式。  
  
## <a name="syntax"></a>語法  
  
```  
decltype( expression )  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`expression`|一個運算式。 如需詳細資訊，請參閱[運算式](../cpp/expressions-cpp.md)。|  
  
## <a name="return-value"></a>傳回值  
 `expression` 參數的類型。  
  
## <a name="remarks"></a>備註  
 `decltype` 類型規範在 Visual C++ 2010 (含) 以後版本支援，可以搭配原生或 Managed 程式碼使用。 Visual Studio 2015 和更新版本支援 `decltype(auto)` (C++14)。  
  
 編譯器會使用下列規則來判斷 `expression` 參數的類型。  
  
-   如果`expression`參數是識別項或[類別成員存取](../cpp/member-access-operators-dot-and.md)，`decltype(expression)`是所指名的實體的型別`expression`。 如果沒有這種實體或 `expression` 參數命名了一組多載函式，編譯器會產生錯誤訊息。  
  
-   如果`expression`參數是對函式或多載的運算子函式的呼叫`decltype(expression)`函式的傳回型別。 在多載運算子周圍的括號會被忽略。  
  
-   如果`expression`參數是[右值](../cpp/lvalues-and-rvalues-visual-cpp.md)，`decltype(expression)`是種`expression`。 如果`expression`參數是[左值](../cpp/lvalues-and-rvalues-visual-cpp.md)，`decltype(expression)`是[左值參考](../cpp/lvalue-reference-declarator-amp.md)的型別`expression`。  
  
 下列程式碼範例示範 `decltype` 類型規範的一些用法。 首先，假設您撰寫了下列陳述式。  
  
```cpp  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 接著，檢查由下表中四個 `decltype` 陳述式所傳回的類型。  
  
|陳述式|類型|注意|  
|---------------|----------|-----------|  
|`decltype(fx());`|`const int&&`|[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md)至`const int`。|  
|`decltype(var);`|`int`|變數 `var` 的類型。|  
|`decltype(a->x);`|`double`|成員存取的類型。|  
|`decltype((a->x));`|`const double&`|括號內的陳述式會評估為運算式而不是成員存取。 而且，因為 `a` 已宣告為 `const` 指標，所以其類型會是 `const double` 的參考。|  
  
## <a name="decltype-and-auto"></a>Decltype 和 Auto  
 在 C++ 14 中，你可以使用`decltype(auto)`不带尾随返回类型来声明其返回类型的模板函数取决于其模板自变量的类型。   
  
 在 C++11 中，您可以搭配使用尾端傳回類型上的 `decltype` 類型規範與 `auto` 關鍵字，來宣告其傳回類型視樣板引數而定的樣板函式。 例如，請考慮下列程式碼範例，其中樣板函式的傳回型別取決於樣板引數的類型。 在程式碼範例中，*未知*預留位置表示不能指定傳回型別。  
  
```cpp  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 `decltype` 類型規範的引入可讓開發人員取得樣板函式傳回的運算式類型。 使用*替代函式宣告語法*更新版本中，顯示`auto`關鍵字，而`decltype`類型規範來宣告*晚期指定*傳回型別。 晚期指定的傳回型別是在編譯宣告時決定，而不是在撰寫程式時決定。  
  
 下列原型說明替代函式宣告的語法。 請注意，`const`和`volatile`限定詞和`throw`[例外狀況規格](../cpp/exception-specifications-throw-cpp.md)是選擇性的。 *Function_body*預留位置代表指定函式的作用的複合陳述式。 以程式設計方式，是最佳*運算式*中的預留位置`decltype`陳述式應該符合所指定的運算式`return`陳述式，如果有的話，在*function_body*。  
  
 **自動** *function_name* **(** *參數*<sub>選擇</sub> **)** **const**<sub>選擇</sub> **volatile**<sub>選擇</sub> **->** **decltype (***運算式* **)** **擲回**<sub>選擇</sub> **{** *function_body***};**  
  
 下列程式碼範例中，`myFunc` 樣板函式的晚期指定傳回類型由 `t` 和 `u` 樣板引數的類型決定。 基於最佳編碼作法，程式碼範例也使用右值參考和`forward`函式樣板，其支援*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
```cpp  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## <a name="decltype-and-forwarding-functions-c11"></a>decltype 和轉送函式 (C++11)  
 轉送函式會包裝對其他函式的呼叫。 試想一個轉送其引數，或者包含這些引數的運算式結果到其他函式的函式樣板。 此外，轉送函式會傳回呼叫其他函式的結果。 在這個案例中，轉送函式的傳回型別應該會與包裝函式的傳回型別相同。  
  
 在這個案例中，您必須使用 `decltype` 類型規範才能撰寫適當的類型運算式。 `decltype` 類型規範可進行泛型轉送函式，因為它不會遺失函式是否傳回參考類型的必要資訊。 如需轉送函式的程式碼範例，請參閱先前的 `myFunc` 樣板函式範例。  
  
## <a name="example"></a>範例  
 下列程式碼範例會宣告樣板函式 `Plus()` 的晚期指定傳回類型。 `Plus` 函式處理其使用 `operator+` 多載的兩個運算元。 因此，加號運算子 (+) 的解譯和 `Plus` 函式的傳回類型取決於函式引數的類型。  
  
```cpp  
// decltype_1.cpp  
// compile with: cl /EHsc decltype_1.cpp  
  
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
  
```Output  
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```
  
## <a name="example"></a>範例
**2017 和更新版本的 visual Studio:**編譯器就會剖析 decltype 引數的範本會宣告，而具現化。 因此，如果在 decltype 引數中找到非相依特製化，則不會延遲到具現化期間，並且會立即處理，而且會在當下診斷出任何產生的錯誤。

下列範例顯示在宣告時引發的這類編譯器錯誤︰

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>需求  
 Visual C++ 2010 (含) 以後版本。  
  
 `decltype(auto)`需要 Visual Studio 2015 或更新版本。  
  
