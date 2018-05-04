---
title: 自動 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14ad8e7cb81df62156d35809853e1060107d7c90
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="auto-c"></a>自動 （c + +）
從所宣告變數的初始化運算式，來推斷其類型。  
  
## <a name="syntax"></a>語法  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>備註  
 `auto` 關鍵字會指示編譯器使用所宣告變數或 Lambda 運算式參數的初始化運算式來推算其類型。  
  
 除非您確實要進行轉換，否則建議您在大多數情況下使用 `auto` 關鍵字，因為它提供下列優點：  
  
-   **穩固性：**如果運算式的類型變更 — 這包括函式傳回類型變更時，它就會運作。  
  
-   **效能：**保證會有任何轉換。  
  
-   **可用性：**您不必擔心類型名稱拼字困難和錯字。  
  
-   **效率：**您撰寫程式碼可能會更有效率。  
  
 可能不想使用 `auto` 的轉換案例：  
  
-   想要特定類型但不執行任何動作時。  
  
-   運算式樣板 helper 類型 — 例如， `(valarray+valarray)`。  
  
 若要使用 `auto` 關鍵字，請使用它 (非類型) 來宣告一個變數，並指定初始化運算式。 此外，您還可以修改 `auto` 關鍵字，方式是使用規範和宣告子，例如 `const`、`volatile`、指標 (`*`)、參考 (`&`) 和右值參考 `(&&`)。 編譯器會評估初始化運算式，然後使用該資訊來推斷變數類型。  
  
 初始化運算式可以是指派 （等號語法），直接初始化 （函式樣式語法）[運算子 new](new-operator-cpp.md)運算式或初始化運算式可以是*針對範圍宣告*中的參數[範圍架構 for 陳述式 （c + +）](../cpp/range-based-for-statement-cpp.md)陳述式。 如需詳細資訊，請參閱[初始設定式](../cpp/initializers.md)和在本文件後面的程式碼範例。  
  
 `auto` 關鍵字是類型的預留位置，但它本身不是類型。 因此，`auto`關鍵字不能在轉換或運算子例如[sizeof](../cpp/sizeof-operator.md)和[typeid](../windows/typeid-cpp-component-extensions.md)。  
  
## <a name="usefulness"></a>實用性  
 `auto` 關鍵字是宣告包含複雜類型之變數的簡單方式。 例如，您可以使用 `auto` 宣告變數，其中初始化運算式包括樣板、函式指標或成員指標。  
  
 您也可以使用 `auto` 宣告並初始化 Lambda 運算式的變數。 您無法自行宣告變數類型，因為只有編譯器才知道 Lambda 運算式的類型。 如需詳細資訊，請參閱[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。  
  
## <a name="trailing-return-types"></a>尾端傳回型別  
 您可以搭配使用 `auto` 與 `decltype` 類型規範，以協助撰寫樣板庫。 使用 `auto` 和 `decltype` 來宣告其傳回類型視樣板引數而定的樣板函式。 或是使用 `auto` 和 `decltype` 宣告樣板函式，以包裝對其他函式的呼叫，然後傳回該其他函式的傳回類型。 如需詳細資訊，請參閱[decltype](../cpp/decltype-cpp.md)。  
  
## <a name="references-and-cv-qualifiers"></a>參考和 cv 限定詞  
 請注意，使用 `auto` 會捨棄參考、const 限定詞和 volatile 限定詞。 參考下列範例：  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 在上述範例中，myAuto 是 int，不需為 int 參考，因此輸出是`11 11`，而非`11 12`時便會發生，如果尚未捨棄參考辨識符號`auto`。  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>有括號初始設定式 (C + + 14) 的類型推斷  
 下列程式碼 exmample 示範如何初始化使用括號的自動變數。 請注意 A 之間以及 B 和 C 之間的差異和 e。  
  
```cpp  
#include <initializer_list>  
  
int main()  
{  
    // std::initializer_list<int>  
    auto A = { 1, 2 };  
  
    // std::initializer_list<int>  
    auto B = { 3 };  
  
    // int  
    auto C{ 4 };  
  
    // C3535: cannot deduce type for 'auto' from initializer list'  
    auto D = { 5, 6.7 };  
  
    // C3518 in a direct-list-initialization context the type for 'auto'  
    // can only be deduced from a single initializer expression  
    auto E{ 8, 9 };  
  
    return 0;  
}  
```  
  
## <a name="restrictions-and-error-messages"></a>限制和錯誤訊息  
 下表列出 `auto` 關鍵字使用限制，以及編譯器所發出的對應診斷錯誤訊息。  
  
|錯誤代碼|描述|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|`auto` 關鍵字無法與任何其他類型規範結合。|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|使用 `auto` 關鍵字所宣告的符號必須有初始設定式。|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|您不正確地使用 `auto` 關鍵字來宣告類型。 例如，您已宣告方法傳回型別或陣列。|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md)， [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|參數或樣板引數不可以使用 `auto` 關鍵字進行宣告。|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|方法或樣板參數不可以使用 `auto` 關鍵字進行宣告。|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符號無法在初始化之前使用。 實際上，這表示不能使用變數來初始化它自己。|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|您無法轉換成使用 `auto` 關鍵字所宣告的類型。|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|宣告子清單中使用 `auto` 關鍵字所宣告的所有符號必須解析成相同的類型。 如需詳細資訊，請參閱[宣告和定義](declarations-and-definitions-cpp.md)。|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)和[typeid](../windows/typeid-cpp-component-extensions.md)運算子不能套用至使用宣告的符號`auto`關鍵字。|  
  
## <a name="examples"></a>範例  
 這些程式碼片段說明可以使用 `auto` 關鍵字的數種方式。  
  
 下列宣告相同。 在第一個陳述式中，變數 `j` 宣告成類型 `int`。 在第二個陳述式中，變數 `k` 宣告成類型 `int`，因為初始化運算式 (0) 是整數。  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 下列宣告相同，但第二個宣告比第一個宣告簡單。 其中一個使用 `auto` 關鍵字的最令人信服原因是簡單。  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 下列程式碼片段會在 `for` 和範圍 `for` 迴圈開始時宣告變數 `iter` 和 `elem` 的類型。  
  
```cpp  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
```  
  
 下列程式碼片段使用 `new` 運算子和指標宣告來宣告指標。  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 下一個程式碼片段會宣告每個宣告陳述式中的多個符號。 請注意，每個陳述式中的所有符號都會解析成相同類型。  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 此程式碼片段使用條件運算子 (`?:`) 將變數 `x` 宣告為值為 200 的整數：  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 下列程式碼片段會初始化變數`x`輸入`int`、 變數`y`類型的參考至`const int`，和變數`fp`函式的傳回類型的指標`int`。  
  
```cpp  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../cpp/auto-keyword.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [/Zc: auto （推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 運算子](../cpp/sizeof-operator.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)   
 [new 運算子](new-operator-cpp.md)   
 [宣告和定義](declarations-and-definitions-cpp.md)   
 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)   
 [初始設定式](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)