---
title: "函式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e5794cd9ec0eb5afc879507bcf8942d6481ebca4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="functions-c"></a>函式 (C++)
函式是執行某項作業的程式碼區塊。 函式可以選擇性地定義輸入參數，以讓呼叫端將引數傳遞給函式。 函式可以選擇性地傳回值做為輸出。 函式適用於將一般作業封裝在單一可重複使用的區塊中，而且其名稱最好可清楚描述該函式的作用。 下列函式接受呼叫端的兩個整數並傳回其總和;`a`和`b`是*參數*型別的`int`。  
  
```  
int sum(int a, int b)  
{  
    return a + b;  
}  
```  
  
 此函式可以是 ' 叫用，或*呼叫*，從任意數目的程式中的位置。 傳遞至函數的值是*引數*，其類型必須與函數定義中的參數類型相容。  
  
```  
int main()  
{  
    int i = sum(10, 32);  
    int j = sum(i, 66);  
    cout << "The value of j is" << j << endl; // 108  
}  
```  
  
 函式長度沒有實際限制，但良好的設計目標在於函式可以執行單一完整定義的工作。 如果可能，應該將複雜演算法分解成容易了解的較簡單函式。  
  
 在類別範圍定義的函式稱為成員函式。 與其他語言不同，在 C++ 中，函式也可以定義於命名空間範圍 (包括隱含全域命名空間)。 這類函式的呼叫*免費函式*或*非成員函式*; 它們廣泛用於標準程式庫。  
  
## <a name="parts-of-a-function-declaration"></a>函式宣告的組件  
 最小的函式*宣告*包含傳回型別、 函式名稱和參數清單 （這可能是空的），以及提供編譯器其他指示的選擇性關鍵字。 下列範例是函式宣告：

 ```cpp
 int sum(int a, int b);
 ```

 函式定義包含宣告，再加上*主體*，即大括號之間的所有程式碼：
 
 ```cpp
int sum(int a, int b)  
{  
    return a + b;  
}  
```
 後面接著一個分號的函式宣告可能會出現在程式的多個位置。 它必須出現在每個轉譯單位中該函式的任何呼叫之前。 根據「一個定義規則 (ODR)」，函式定義只能出現在程式中一次。  
  
 函式宣告的必要組件如下：  
  
1.  傳回類型，指定函式所傳回值的類型，或者，如果未傳回任何值，則為 `void`。 在 C + + 11 中，`auto`是有效的傳回型別，它會指示編譯器透過 return 陳述式推斷類型。 在 C++14 中，也允許 decltype(auto)。 如需詳細資訊，請參閱下面的＜傳回類型中的類型推斷＞。  
  
2.  函式名稱，開頭必須為字母或底線，而且不能包含空格。 一般而言，標準程式庫函式名稱中的前置底線表示私用成員函式或不是要供您的程式碼使用的非成員函式。 
  
3.  參數清單，是以大括號分隔並以逗號隔開的零或多個參數集合，指定類型以及選擇性指定可用來存取函式主體內值的本機名稱。 
  
 函式宣告的選擇性組件如下：  
  
1.  `constexpr`，表示函式的傳回值是常數值，可在編譯時期計算。  
  
    ```  
    constexpr float exp(float x, int n)  
    {  
        return n == 0 ? 1 :  
            n % 2 == 0 ? exp(x * x, n / 2) :  
            exp(x * x, (n - 1) / 2) * x;  
    };  
    ```  
  
2.  其 `linkage` 規格：`extern` 或 `static`。  
  
    ```  
    Declare printf with C linkage.  
    extern "C" int printf( const char *fmt, ... );  
  
    ```  
  
     如需詳細資訊，請參閱[程式和連結](../cpp/program-and-linkage-cpp.md)。  
  
3.  `inline`，指示編譯器將函式的每個呼叫都取代為函式程式碼本身。 如果函式執行速度快速並在效能關鍵的程式碼區段中重複予以叫用，則內嵌有助於提高效能。  
  
    ```  
    inline double Account::GetBalance()  
    {  
        return balance;  
    }  
    ```  
  
     如需詳細資訊，請參閱[內嵌函式](../cpp/inline-functions-cpp.md)。  
  
4.  A`noexcept`運算式，指定函式是否可能擲回例外狀況。 在下列範例中，如果 `is_pod` 運算式評估為 `true`，則函式不會擲回例外狀況。  
  
    ```  
    #include <type_traits>  
  
    template <typename T>  
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}  
    ```  
  
     如需詳細資訊，請參閱[noexcept](../cpp/noexcept-cpp.md)。  
  
5.  (僅限成員函式) cv 限定詞，指定函式是 `const` 還是 `volatile`  
  
6.  (僅限成員函式) `virtual`、`override` 或 `final`。 `virtual` 指定可以覆寫衍生類別中的函式。 `override` 表示衍生類別中的函式會覆寫虛擬函式。 `final` 表示無法覆寫任何進一步衍生類別中的函式。 如需詳細資訊，請參閱[虛擬函式](../cpp/virtual-functions.md)。  
  
7.  (僅限成員函式) 套用至成員函式的 `static` 表示函式未與類別的任何物件執行個體相關聯。  
  
8.  （只有非靜態成員函式）Ref-qualifier，指定給編譯器選擇何時將函式多載的隱含物件參數 (* 這) 是左值參考和右值參考。  
  
 下圖顯示函式定義的組件。 陰影區域是函式主體。  
  
 ![函式定義的組件](../cpp/media/vc38ru1.gif "vc38RU1")  
函式定義的組件  
  
## <a name="function-definitions"></a>函式定義  
 主體內宣告的變數稱為區域變數。 它們會在函式結束時消失；因此，函式永遠不應該傳回區域變數的參考！  
  
## <a name="function-templates"></a>函式樣板  
 函式樣板與類別樣板類似；它會根據樣板引數產生具象函式。 在許多情況下，樣板可以推斷型別引數，因此不需要明確指定它們。  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs;  
}  
  
auto a = Add2(3.13, 2.895); // a is a double  
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string  
```  
  
 如需詳細資訊，請參閱[函式樣板](../cpp/function-templates.md)  
  
## <a name="function-parameters-and-arguments"></a>函式參數和引數  
 函式具有零或多個類型的參數清單 (以逗號分隔)，且各有用來在函式主體內進行存取的名稱。 函式樣板可以指定其他類型或值參數。 呼叫端會傳遞引數，而引數是類型與參數清單相容的具象值。  
  
 根據預設，會以傳值方式將引數傳遞給函式，這表示函式會收到所傳遞物件的複本。 針對大型物件，建立複本可能十分耗費資源，而且不一定是必要的。 若要透過傳址方式 (特別是左值參考) 傳遞引數，請將參考 quaitifer 加入參數：  
  
```  
void DoSomething(std::string& input){...}  
```  
  
 函式修改透過傳址方式所傳遞的引數時，會修改原始物件，而不是本機複本。 若要防止函式修改這類引數，請將參數限定為 const&：  
  
```  
void DoSomething(const std::string& input){...}  
```  
  
 **C + + 11:**若要明確處理透過右值參考或左值參考所傳遞的引數，雙連字號參數上使用以表示通用參考：  
  
```  
void DoSomething(const std::string&& input){...}  
```  
  
 只要關鍵字 `void` 是引數宣告清單中的第一個且是唯一的成員，使用參數宣告清單中單一關鍵字 `void` 所宣告的函式就不會採用引數。 清單中其他位置的 `void` 類型引數都會產生錯誤。 例如:  
  
```  
  
// OK same as GetTickCount()  
long GetTickCount( void );   
```  
  
 請注意，雖然除了這裡所述之外，指定 `void` 引數仍是不合法的，但是 `void` 類型的衍生類型 (例如 `void` 的指標和 `void` 陣列) 可以出現在引數宣告清單中的任何位置。  
  
### <a name="default-arguments"></a>預設引數  
 函式簽章中的最後一個參數或參數可能獲指派預設引數，這表示除非呼叫端想要指定其他值，否則在呼叫函式時可能會省略引數。  
  
```  
int DoSomething(int num,   
    string str,   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// OK both parameters are at end  
int DoSomethingElse(int num,   
    string str = string{ "Working" },   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// C2548: 'DoMore': missing default parameter for parameter 2  
int DoMore(int num = 5, // Not a trailing parameter!  
    string str,  
    Allocator& = defaultAllocator)  
{...}  
```  
  
 如需詳細資訊，請參閱[預設引數](../cpp/default-arguments.md)。  
  
## <a name="function-return-types"></a>函式傳回型別  
 函式可能不會傳回另一個函式或內建陣列;不過它可以傳回這些類型的指標或*lambda*，這會產生函式物件。 除了這些情況之外，函式可能會傳回範圍內任何類型的值，也可能不會傳回值，在此情況下，傳回類型是 `void`。  
  
### <a name="trailing-return-types"></a>尾端傳回類型  
 "ordinary" 傳回型別位於函式簽章左邊。 A*尾端傳回型別*位於最右邊的簽章，前面加上-> 運算子。 傳回值的類型取決於樣板參數時，尾端傳回型別特別適用於函式樣板。  
  
```  
template<typename Lhs, typename Rhs>  
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)  
{  
    return lhs + rhs;   
}  
```  
  
 `auto` 與尾端傳回類型搭配使用時，只是做為 decltype 運算式所產生項目的預留位置，而且本身不會執行類型推斷。  

   
## <a name="function-local-variables"></a>函式區域變數  
 宣告函式主體內的變數稱為*區域變數*或只是*本機*。 非靜態區域變數只顯示於函式主體內，如果它們宣告於堆疊上，則會在函式結束時消失。 如果建構區域變數並以傳值方式傳回區域變數，則編譯器通常會執行傳回值最佳化，以避免不必要的複製作業。 如果您以傳址方式傳回區域變數，則編譯器會發出警告，因為呼叫端使用該參考的任何嘗試都是在終結區域變數之後。  
  
 區域靜態物件會在 `atexit` 指定的終止時被終結。 如果因為程式的控制流程略過其宣告而未建構靜態物件，就不會嘗試終結該物件。  
  
### <a name="static-local-variables"></a>靜態區域變數  
 在 C++ 中，區域變數可能宣告為靜態。 變數只會顯示在函式主體內，但函式的所有執行個體都有變數的單一複本。  
  
###  <a name="type_deduction"></a>傳回型別 (C + + 14) 中的類型推斷  
 在 C++14 中，您可以使用 `auto` 指示編譯器從函式主體推斷傳回類型，而不需要提供尾端傳回類型。 請注意，`auto` 一律會推斷為以傳值方式傳回。 使用 `auto&&` 指示編譯器推斷參考。  
  
 在此範例中，會將 `auto` 推斷為 lhs 與 rhs 之總和的非常數值複本。  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs; //returns a non-const object by value  
}  
```  
  
 請注意，`auto`不會保留的推斷的類型的 const-ness。 對於傳回值需要保留其引數之 const-ness 或 ref-ness 的轉送函式，您可以使用 `decltype(auto)` 關鍵字，而此關鍵字使用 `decltype` 類型推斷規則，並保留所有類型資訊。 `decltype(auto)` 可能用做左邊的 ordinary 傳回值或尾端傳回值。  
  
 下列範例 (根據程式碼從[N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html))，顯示`decltype(auto)`，並用來啟用完美轉送在具現化樣板之前不已知的傳回型別中的函式引數。  
  
```  
template<typename F, typename Tuple = tuple<T...>, int... I>  
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)   
{  
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);  
}  
  
template<typename F, typename Tuple = tuple<T...>,  
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>  
   decltype( auto)  
    apply(F&& f, Tuple&& args)      
{  
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());  
}  
}  
```  
## <a name="returning-multiple-values-from-a-function"></a>從函數傳回多個值
有各種方式從函式傳回一個以上的值：

1. 封裝已命名的類別或結構物件中的值。 需要顯示給呼叫者的類別或結構定義：

```cpp
#include <string>
#include <iostream>

using namespace std;

struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    S s = g();
    cout << s.name << " " << s.num << endl;
    return 0;
}
```

2. 傳回 std:: tuple 或 std:: pair 物件：

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;


tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}

int main()
{
    auto t = f();
    cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;
    
    // --or--

    int myval;
    string myname;
    double mydecimal;
    tie(myval, myname, mydecimal) = f();
    cout << myval << " " << myname << " " << mydecimal << endl;

    return 0;
}
```

3. **Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 使用結構化的繫結。 結構化的繫結的優點是，儲存傳回值的變數會初始化宣告，同時在某些情況下可能會更具效率。 在這個陳述式-`auto[x, y, z] = f();`-介紹方括號，並初始化會在整個函式區塊的範圍的名稱。  

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;

tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}
struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    auto[x, y, z] = f(); // init from tuple
    cout << x << " " << y << " " << z << endl;

    auto[a, b] = g(); // init from POD struct
    cout << a << " " << b << endl;
    return 0;
}
```

4. 除了使用本身的傳回值，您可以 「 傳回 」 值藉由定義任何數目的參數使用傳址方式傳遞，以便函式可以修改或初始化之物件的呼叫端提供的值。 如需詳細資訊，請參閱[參考類型函式引數](reference-type-function-arguments.md)。
  
## <a name="function-pointers"></a>函式指標  
 C++ 支援函式指標的方式與 C 語言相同。 不過，較具類型安全的替代方案通常是使用函式物件。  
  
 如果要宣告傳回函式指標類型的函式，建議您使用 `typedef` 宣告函式指標類型的別名。  例如  
  
```  
typedef int (*fp)(int);  
fp myFunction(char* s); // function returning function pointer  
```  
  
 如果沒有這樣做，函式宣告的適當語法可能會從函式指標的宣告子語法推算，方法是將識別項 (在上述範例中為 `fp`) 取代為函式名稱和引數清單，如下所示：  
  
```  
int (*myFunction(char* s))(int);  
```  
  
 上述宣告相當於上面使用 typedef 的宣告。  
  
## <a name="see-also"></a>另請參閱  
 [函式多載](../cpp/function-overloading.md)   
 [具有變數引數清單的函式](../cpp/functions-with-variable-argument-lists-cpp.md)   
 [明確預設和刪除函式](../cpp/explicitly-defaulted-and-deleted-functions.md)   
 [函式的引數相依名稱 (Koenig) 查閱](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)   
 [預設引數](../cpp/default-arguments.md)   
 [內嵌函式](../cpp/inline-functions-cpp.md)