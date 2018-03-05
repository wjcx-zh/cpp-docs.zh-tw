---
title: "C + + 中的 lambda 運算式 |Microsoft 文件"
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 035fe5c222f6de5b3f0d71c0ce9133c1101f2993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lambda-expressions-in-c"></a>C++ 中的 Lambda 運算式
在 C + + 11 和更新版本中，lambda 運算式，通常稱為*lambda*— 是方便的方式定義匿名函式物件的 ( *closure*) 叫用，或是做為引數的位置函式。 Lambda 通常用來封裝要傳遞給演算法或非同步方法的數行程式碼。 本文定義什麼是 Lambda、Lambda 與其他程式設計技術的比較、描述 Lamdba 的優點並提供基本範例。  

## <a name="related-topics"></a>相關主題
- [Lambda 運算式和函式物件比較](lambda-expression-syntax.md)
- [使用 lambda 運算式](examples-of-lambda-expressions.md)
- [constexpr lambda 運算式](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Lambda 運算式的組件  
 ISO C++ 標準顯示將傳遞為 `std::sort()` 函式第三個引數的簡單 Lambda：  
  
```cpp  
#include <algorithm>  
#include <cmath>  
  
void abssort(float* x, unsigned n) {  
    std::sort(x, x + n,  
        // Lambda expression begins  
        [](float a, float b) {  
            return (std::abs(a) < std::abs(b));  
        } // end of lambda expression  
    );  
}  
  
```  
  
 下圖顯示 Lambda 的組件：  
  
 ![Lambda 運算式的結構化項目](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *擷取子句*(也稱為*lambda introducer* c + + 規格中。)  
  
2.  *參數清單*選擇性。 (也稱為*ambda*)  
  
3.  *可變動規格*選擇性。  
  
4.  *例外狀況規格*選擇性。  
  
5.  *尾端傳回型別*選擇性。  
  
6.  *lambda 主體*)  
  
### <a name="capture-clause"></a>擷取子句  
 Lambda 可以引進新的變數，其主體中 (在**C + + 14**)，而且也可以存取，或*擷取*，從周圍範圍的變數。 Lambda 的開頭擷取子句 (*lambda introducer* Standard 語法中)，以指定要擷取的變數，以及擷取是透過值或參考。 含有 `&` 前置詞的變數會以傳址方式來存取，而不含 & 前置詞的變數會以傳值方式來存取。  
  
 空白的擷取子句 `[ ]` 表示 Lambda 運算式主體不存取封閉範圍中的任何變數。  
  
 您可以使用預設擷取模式 (*擷取預設*Standard 語法中) 來指出如何擷取任何外部的 lambda 中參考的變數：`[&]`方法，即可擷取所有您參考的變數參考，以及`[=]`表示值會擷取它們。 您可以使用預設擷取模式，然後明確指定特定變數的相反模式。 例如，如果 Lambda 主體以傳址方式存取外部變數 `total`，並以傳值方式存取外部變數 `factor`，則下列擷取子句相等：  
  
```cpp  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 當擷取預設值時，會擷取在 lambda 中提及的變數。  
  
 如果擷取子句包含擷取預設`&`，沒有任何`identifier`中`capture`該擷取子句可以有表單`& identifier`。 同樣地，如果擷取子句包含擷取預設`=`，沒有任何`capture`該擷取子句可以有表單`= identifier`。 識別項或 `this` 不能在擷取子句中重複出現。 下列程式碼片段說明部分範例。  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};      // OK  
    [&, &i]{};     // ERROR: i preceded by & when & is the default  
    [=, this]{};   // ERROR: this when = is the default  
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated  
}  
```  
  
 在此所示，擷取，後面接著省略符號是封裝展開[variadic 樣板](../cpp/ellipses-and-variadic-templates.md)範例：  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 若要在類別方法主體中使用 Lambda 運算式，請將 `this` 指標傳遞給擷取子句，以提供對封入類別之方法和資料成員的存取。 
 
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):`this`指標可能傳值方式擷取，藉由指定`*this`capture 子句中。 表示整個值，藉以擷取*closure*，這是匿名函式物件，該 encapulates lambda 運算式，會複製到其中 lambda 叫用每個呼叫站台。 值，藉以擷取時，lambda 會在平行或非同步作業，特別是在特定的硬體架構，例如 NUMA 上執行。 

如需示範如何使用 lambda 運算式與類別方法的範例，請參閱 「 範例:: Lambda 運算式在方法中使用 「 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。  
  
 使用擷取子句時，建議您記住這幾個重點，特別是同時使用 Lambda 與多執行緒時：  
  
-   傳址擷取可用來修改外部變數，但傳值擷取方式不能。 (`mutable` 允許修改複本，但不允許修改原稿)。  
  
-   傳址擷取方式會反映對外部變數的更新，但傳值擷取方式不會。  
  
-   傳址擷取方式採用存留期相依性，但傳值擷取方式沒有存留期相依性。 非同步執行 Lambda 時，這點特別重要。 如果您在非同步 Lambda 中以傳址方式擷取區域變數，該區域變數極可能會在 Lambda 執行之前消失，導致在執行階段存取違規。  
  
### <a name="generalized-capture-c-14"></a>一般化擷取 (C++ 14)  
  
 在 C++14，您可以在擷取子句中引進並初始化新的變數，而這些變數不需要存在於 Lambda 函式的封閉範圍中。 初始化可以表示為任何任意運算式；新變數的類型是透過運算式所產生的類型推斷而來。 這項功能的其中一個優點是在 C++14 中，您可以從周圍範圍擷取僅移動變數 (例如 std::unique_ptr) 並在 Lambda 中使用它們。  
  
```cpp  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### <a name="parameter-list"></a>參數清單  
 除了擷取變數之外，Lambda 還可以接受輸入參數。 參數清單 (*ambda* Standard 語法中) 是選擇性的而且在大部分的方面類似於函式參數清單。  
  
```cpp  
auto y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 在**c + + 14**，如果參數類型為泛型，您可以使用 auto 關鍵字做為類型規範。 這會告訴編譯器建立函式呼叫運算子做為樣板。 參數清單中的每個 auto 執行個體都相當於不同的類型參數。  
  
```cpp  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Lambda 運算式可接受另一個 Lambda 運算式當做其引數。 如需詳細資訊，請參閱 < 高階 Lambda 運算式 > 主題中的 < [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。  
  
 由於參數清單是選擇性的您就可以省略空括號，如果您不傳遞引數至 lambda 運算式，而且不包含其 ambda*例外狀況規格*， *尾端傳回型別*，或`mutable`。  
  
### <a name="mutable-specification"></a>可變動規格  
 通常 Lambda 的函式呼叫運算子是傳值常數，但使用 `mutable` 關鍵字會抵銷此功能。它不會產生可變動的資料成員。 可變動規格可讓 Lambda 運算式主體修改以傳值方式擷取的變數。 本文稍後的一些範例會示範如何使用 `mutable`。  
  
### <a name="exception-specification"></a>例外狀況規格  
 您可以使用 `noexcept` 例外狀況規格，表示 Lambda 運算式不會擲回任何例外狀況。 為一般函式，Visual c + + 編譯器會產生警告[C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)如果 lambda 運算式宣告`noexcept`例外狀況規格，而且 lambda 主體擲回例外狀況，如下所示：  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() noexcept { throw 5; }();  
}  
```  
  
 如需詳細資訊，請參閱[例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)。  
  
### <a name="return-type"></a>傳回型別  
 Lambda 運算式的傳回型別會自動推算出來。 您不必使用[自動](../cpp/auto-cpp.md)關鍵字除非您指定*尾端傳回型別*。 *尾端傳回型別*類似一般方法或函式的傳回類型部分。 不過，傳回類型必須接在參數清單後面，而且您必須在傳回類型前面包含 trailing-return-type 關鍵字 `->`。  
  
 如果 Lambda 主體包含單一 return 陳述式，或者運算式不會傳回值，您可以省略 Lambda 運算式的傳回類型部分。 如果 Lambda 主體包含單一 return 陳述式，編譯器會從傳回運算式的類型推算傳回類型。 否則，編譯器會將傳回類型推算為 `void`。 請考慮下列說明此原則的範例程式碼片段。  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
```  
  
 Lambda 運算式可能會產生另一個 Lambda 運算式當做其傳回值。 如需詳細資訊，請參閱 < 高階 Lambda 運算式 > [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。  
  
### <a name="lambda-body"></a>Lambda 主體  
 Lambda 主體 (*複合陳述式*Standard 語法中) 的 lambda 運算式可以包含一般方法或函式的主體可包含任何內容。 一般函式和 Lambda 運算式的主體都可以存取下列類型的變數：  
  
-   擷取自封閉範圍的變數 (如先前所述)。  
  
-   參數  
  
-   區域宣告變數  
  
-   類別資料成員 (在類別內部宣告並擷取 `this` 時)  
  
-   有靜態儲存期的任何變數 (例如，全域變數)  
  
 下列範例包含 Lambda 運算式，這個運算式會以傳值方式明確擷取變數 `n`，並以傳址方式隱含擷取變數 `m`：  
  
```cpp  
// captures_lambda_expression.cpp  
// compile with: /W4 /EHsc   
#include <iostream>  
using namespace std;  
  
int main()  
{  
   int m = 0;  
   int n = 0;  
   [&, n] (int a) mutable { m = ++n + a; }(4);  
   cout << m << endl << n << endl;  
}  
```  
  
```Output  
5  
0  
```  
  
 因為變數 `n` 是以傳值方式擷取，其值在 Lambda 運算式呼叫之後會保持為 `0`。 `mutable` 規格允許在 Lambda 內修改 `n`。  
  
 雖然 Lambda 運算式只能擷取有自動儲存期的變數，但是您可以在 Lambda 運算式的主體中使用有靜態儲存期的變數。 下列範例使用 `generate` 函式和 Lambda 運算式，將值指派給 `vector` 物件的每個項目。 Lambda 運算式會修改這個靜態變數以產生下一個項目的值。  
  
```cpp  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });   
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
```  
  
 如需詳細資訊，請參閱[產生](../standard-library/algorithm-functions.md#generate)。  
  
 下列程式碼範例會使用上述範例中，函式，並將 c + + 標準程式庫演算法會使用 lambda 運算式的範例`generate_n`。 此 Lambda 運算式會將 `vector` 物件的元素指派給前兩個元素的總和。 使用 `mutable` 關鍵字，因此 Lambda 運算式的主體可以修改其外部變數 `x` 和 `y` 的複本，這兩個變數是 Lambda 運算式以傳值方式擷取的。 由於 Lambda 運算式會以傳值方式擷取原始變數 `x` 和 `y`，在 Lambda 執行後，它們的值仍然保持 `1`。  
  
```cpp  
// compile with: /W4 /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });  
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
  
int main()  
{  
    // The number of elements in the vector.  
    const int elementCount = 9;  
  
    // Create a vector object with each element set to 1.  
    vector<int> v(elementCount, 1);  
  
    // These variables hold the previous two elements of the vector.  
    int x = 1;  
    int y = 1;  
  
    // Sets each element in the vector to the sum of the   
    // previous two elements.  
    generate_n(v.begin() + 2,  
        elementCount - 2,  
        [=]() mutable throw() -> int { // lambda is the 3rd parameter  
        // Generate current value.  
        int n = x + y;  
        // Update previous two values.  
        x = y;  
        y = n;  
        return n;  
    });  
    print("vector v after call to generate_n() with lambda: ", v);  
  
    // Print the local variables x and y.  
    // The values of x and y hold their initial values because   
    // they are captured by value.  
    cout << "x: " << x << " y: " << y << endl;  
  
    // Fill the vector with a sequence of numbers  
    fillVector(v);  
    print("vector v after 1st call to fillVector(): ", v);  
    // Fill the vector with the next sequence of numbers  
    fillVector(v);  
    print("vector v after 2nd call to fillVector(): ", v);  
}  
```  
  
```Output  
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34  
x: 1 y: 1  
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9  
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18  
```  
  
 如需詳細資訊，請參閱[generate_n](../standard-library/algorithm-functions.md#generate_n)。  

## <a name="constexpr-lambda-expressions"></a>constexpr lambda 運算式
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 可能會做為宣告的 lambda 運算式`constexpr`或常數運算式中使用時的每個資料成員初始設定它擷取或導入了常數運算式中允許使用。  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }

``` 
Lambda 會隱含地`constexpr`如果它的結果符合需求的`constexpr`函式：
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
如果 lambda 是隱含或明確地`constexpr`，轉換成函式指標會產生`constexpr`函式：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="microsoft-specific"></a>Microsoft 專有  
 下列通用語言執行平台 (CLR) Managed 實體不支援 Lambda：`ref class`、`ref struct`、`value class` 或 `value struct`。  
  
 如果您要使用的 Microsoft 專有修飾詞，例如[__declspec](../cpp/declspec.md)，您可以將它插入 lambda 運算式之後立即`parameter-declaration-clause`— 例如：  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 若要判定 lambda 是否支援修飾詞，請參閱本文中，有關[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)文件集。  
  
 除了 C + + 11 標準 lambda 功能，Visual Studio 支援無狀態 lambda，可完全轉換為使用任意呼叫慣例的函式指標。  
  
## <a name="see-also"></a>請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C + + 標準程式庫中的函式物件](../standard-library/function-objects-in-the-stl.md)   
 [函式呼叫](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)
