---
title: "C++ 中的 Lambda 運算式 | Microsoft Docs"
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
  - "Lambda 運算式 [C++]"
  - "Lambda 運算式 [C++], 概觀"
  - "Lambda 運算式 [C++], 和函式物件比較"
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 中的 Lambda 運算式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+11 中，Lambda 運算式 \(通常稱為 *Lambda*\) 是一種方便的方式，可在叫用它或將它傳遞為函式引數的位置定義匿名函式物件。  Lambda 通常用來封裝要傳遞給演算法或非同步方法的數行程式碼。  本文定義什麼是 Lambda、Lambda 與其他程式設計技術的比較、描述 Lamdba 的優點並提供基本範例。  
  
## Lambda 運算式的組件  
 ISO C\+\+ 標準顯示將傳遞為 `std::sort()` 函式第三個引數的簡單 Lambda：  
  
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
  
1.  *「擷取子句」*\(Capture Clause\) \(在 C\+\+ 規格中，也稱為 *lambda\-introducer*\)。  
  
2.  \(選擇性\)*「參數清單」*\(Parameter List\)。  \(也稱為*「Lambda 宣告子」*\(Lambda Declarator\)\)  
  
3.  \(選擇性\) *可變動規格*。  
  
4.  \(選擇性\) *exception\-specification*。  
  
5.  \(選擇性\) *trailing\-return\-type*。  
  
6.  *「Lambda 主體」*\(Lambda Body\)  
  
### 擷取子句  
 Lambda 可以在其主體中引進新的變數 \(在 **C\+\+14** 中\)，也可以從周圍範圍存取 \(或*「擷取」*\(Capture\)\) 變數。  Lambda 的開頭為擷取子句 \(Standard 語法中的 *lambda\-introducer*\)，指定要擷取的變數，以及是以傳值方式還是傳址方式進行擷取。  含有 `&` 前置詞的變數會以傳址方式來存取，而不含 & 前置詞的變數會以傳值方式來存取。  
  
 空白的擷取子句 `[ ]` 表示 Lambda 運算式主體不存取封閉範圍中的任何變數。  
  
 您可以使用預設擷取模式 \(Standard 語法中的 `capture-default`\) 指出如何擷取 Lambda 中參考的任何外部變數： \[&\] 表示您參照的所有變數都是以傳址方式進行擷取，而 \[\=\] 表示是以傳值方式進行擷取。  您可以使用預設擷取模式，然後明確指定特定變數的相反模式。  例如，如果 Lambda 主體以傳址方式存取外部變數 `total`，並以傳值方式存取外部變數 `factor`，則下列擷取子句相等：  
  
```cpp  
  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 使用 `capture-default` 時只會擷取 Lambda 中提到的變數。  
  
 如果擷取子句包含 `capture-default` `&`，該擷取子句的 `identifier` 中，沒有任何 `capture` 會具有 `& identifier` 格式。  同樣地，如果擷取子句包含 `capture-default` `=`，則該擷取子句沒有任何 `capture` 會具有 `= identifier` 格式。  識別項或 `this` 不能在擷取子句中重複出現。  下列程式碼片段說明部分範例。  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};    // OK  
    [&, &i]{};   // ERROR: i preceded by & when & is the default  
    [=, this]{}; // ERROR: this when = is the default  
    [i, i]{};    // ERROR: i repeated  
}  
```  
  
 省略符號前面的 `capture` 是套件擴充，如下列 [variadic 樣板](../cpp/ellipses-and-variadic-templates.md)範例所示：  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 若要在類別方法主體中使用 Lambda 運算式，請將 `this` 指標傳遞給擷取子句，以提供對封入類別之方法和資料成員的存取。  如需示範如何搭配使用 Lambda 運算式與類別方法的範例，請參閱 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md) 中的＜範例：在方法中使用 Lambda 運算式＞。  
  
 使用擷取子句時，建議您記住這幾個重點，特別是同時使用 Lambda 與多執行緒時：  
  
-   傳址擷取可用來修改外部變數，但傳值擷取方式不能。  \(`mutable` 允許修改複本，但不允許修改原稿\)。  
  
-   傳址擷取方式會反映對外部變數的更新，但傳值擷取方式不會。  
  
-   傳址擷取方式採用存留期相依性，但傳值擷取方式沒有存留期相依性。  非同步執行 Lambda 時，這點特別重要。  如果您在非同步 Lambda 中以傳址方式擷取區域變數，該區域變數極可能會在 Lambda 執行之前消失，導致在執行階段存取違規。  
  
 **一般化擷取 \(C\+\+ 14\)**  
  
 在 C\+\+14，您可以在擷取子句中引進並初始化新的變數，而這些變數不需要存在於 Lambda 函式的封閉範圍中。  初始化可以表示為任何任意運算式；新變數的類型是透過運算式所產生的類型推斷而來。  這項功能的其中一個優點是在 C\+\+14 中，您可以從周圍範圍擷取僅移動變數 \(例如 std::unique\_ptr\) 並在 Lambda 中使用它們。  
  
```  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### 參數清單  
 除了擷取變數之外，Lambda 還可以接受輸入參數。  參數清單 \(Standard 語法中的 *ambda 宣告子*\) 為選擇性，在很多方面類似函式的參數清單。  
  
```  
int y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 在 **C\+\+ 14** 中，如果參數類型是泛型，您可以使用 auto 關鍵字做為類型規範。  這會告訴編譯器建立函式呼叫運算子做為樣板。  參數清單中的每個 auto 執行個體都相當於不同的類型參數。  
  
```  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Lambda 運算式可接受另一個 Lambda 運算式當做其引數。  如需詳細資訊，請參閱 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)主題中的＜高階 Lambda 運算式＞。  
  
 由於參數清單是選擇性的，所以如果您不傳遞引數至 Lambda 運算式，且其 `lambda-declarator:` 不包含 *exception\-specification*、*trailing\-return\-type* 或 `mutable`，則可省略空括號。  
  
### 可變動規格  
 通常 Lambda 的函式呼叫運算子是傳值常數，但使用 `mutable` 關鍵字會抵銷此功能。  它不會產生可變動的資料成員。  可變動規格可讓 Lambda 運算式主體修改以傳值方式擷取的變數。  本文稍後的一些範例會示範如何使用 `mutable`。  
  
### 例外狀況規格  
 您可以使用 `throw()` 例外狀況規格，表示 Lambda 運算式不會擲回任何例外狀況。  如同一般函式，如果 Lambda 運算式宣告 [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) 例外狀況規格，而且 Lambda 主體擲回例外狀況，Visual C\+\+ 編譯器就會產生警告 `throw()`，如下所示：  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() throw() { throw 5; }();  
}  
```  
  
 如需詳細資訊，請參閱[例外狀況規格 \(throw\)](../cpp/exception-specifications-throw-cpp.md)。  
  
### 傳回類型  
 Lambda 運算式的傳回類型會自動推算出來。  除非您指定 *trailing\-return\-type*，否則不需要使用 [auto](../cpp/auto-cpp.md) 關鍵字。  *trailing\-return\-type* 類似一般方法或函式的傳回類型部分。  不過，傳回類型必須接在參數清單後面，而且您必須在傳回類型前面包含 trailing\-return\-type 關鍵字 `->`。  
  
 如果 Lambda 主體包含單一 return 陳述式，或者運算式不會傳回值，您可以省略 Lambda 運算式的傳回類型部分。  如果 Lambda 主體包含單一 return 陳述式，編譯器會從傳回運算式的類型推算傳回類型。  否則，編譯器會將傳回類型推算為 `void`。  請考慮下列說明此原則的範例程式碼片段。  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
  
```  
  
 Lambda 運算式可能會產生另一個 Lambda 運算式當做其傳回值。  如需詳細資訊，請參閱 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)中的＜高階 Lambda 運算式＞。  
  
### Lambda 主體  
 Lambda 運算式的 Lambda 主體 \(Standard 語法中的 *compound\-statement*\) 可以包含一般方法或函式主體可包含的任何內容。  一般函式和 Lambda 運算式的主體都可以存取下列類型的變數：  
  
-   擷取自封閉範圍的變數 \(如先前所述\)。  
  
-   參數  
  
-   區域宣告變數  
  
-   類別資料成員 \(在類別內部宣告並擷取 `this` 時\)  
  
-   有靜態儲存期的任何變數 \(例如，全域變數\)  
  
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
  
 **輸出：**  
  
  **5**  
**0** 因為變數 `n` 是以傳值方式擷取，其值在 Lambda 運算式呼叫之後會保持為 `0`。  `mutable` 規格允許在 Lambda 內修改 `n`。  
  
 雖然 Lambda 運算式只能擷取有自動儲存期的變數，但是您可以在 Lambda 運算式的主體中使用有靜態儲存期的變數。  下列範例使用 `generate` 函式和 Lambda 運算式，將值指派給 `vector` 物件的每個項目。  Lambda 運算式會修改這個靜態變數以產生下一個項目的值。  
  
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
  
 如需詳細資訊，請參閱[產生](../Topic/generate.md)。  
  
 下列程式碼範例使用前一個範例的函式，並加入使用 STL 演算法 `generate_n` 的 Lambda 運算式範例。  此 Lambda 運算式會將 `vector` 物件的元素指派給前兩個元素的總和。  使用 `mutable` 關鍵字，因此 Lambda 運算式的主體可以修改其外部變數 `x` 和 `y` 的複本，這兩個變數是 Lambda 運算式以傳值方式擷取的。  由於 Lambda 運算式會以傳值方式擷取原始變數 `x` 和 `y`，在 Lambda 執行後，它們的值仍然保持 `1`。  
  
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
  
 **輸出：**  
  
  **呼叫 generate\_n\(\) 與 lambda 後的向量 v：1 1 2 3 5 8 13 21 34**  
**x：1 y：1**  
**呼叫 fillVector\(\) 後的向量 v：1 2 3 4 5 6 7 8 9**  
**第二次呼叫 fillVector\(\) 後的向量 v：10 11 12 13 14 15 16 17 18** 如需詳細資訊，請參閱 [generate\_n](../Topic/generate_n.md)。  
  
## Microsoft 專有  
 下列通用語言執行平台 \(CLR\) Managed 實體不支援 Lambda：`ref class`、`ref struct`、`value class` 或 `value struct`。  
  
 如果您使用 [\_\_declspec](../cpp/declspec.md) 之類的 Microsoft 專有修飾詞，可以將其插入 Lambda 運算式中的 `parameter-declaration-clause` 後面，例如：  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
  
```  
  
 若要判定 Lambda 是否支援修飾詞，請參閱說明文件的 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)一節中，有關 Lambda 的文章。  
  
 Visual Studio 支援 C\+\+11 標準 Lambda 運算式語法和功能，例外狀況如下：  
  
-   Lambda 和其他所有類別一樣，不會取得自動產生的移動建構函式和移動指派運算子。  如需右值參考行為的詳細資訊，請參閱 [C\+\+11\/14\/17 功能的支援](../cpp/support-for-cpp11-14-17-features-modern-cpp.md)中的＜右值參考＞一節。  
  
-   此版本不支援選擇性的 *attribute\-specifier\-seq*。  
  
 除了 C\+\+11 標準 Lambda 功能，Visual Studio 還包含下列功能：  
  
-   無狀態 Lambda，可完全轉換為使用任意呼叫慣例的函式指標。  
  
-   只要所有 return 陳述式都有相同類型，就會自動推算比 `{ return expression; }` 更複雜的 Lambda 主體傳回類型。  \(此功能包含在所提議的 C\+\+14 標準中。\)  
  
## 請參閱  
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [STL 中的函式物件](../standard-library/function-objects-in-the-stl.md)   
 [函式呼叫](../cpp/function-call-cpp.md)   
 [for\_each](../Topic/for_each.md)