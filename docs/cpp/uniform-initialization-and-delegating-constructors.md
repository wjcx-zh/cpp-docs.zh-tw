---
title: 統一初始設定和委派建構函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df40eef538ec09a0189bf6c1e6b4881edb59f5c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="uniform-initialization-and-delegating-constructors"></a>統一初始設定和委派建構函式
在現代 c + + 中，您可以使用*大括號初始化*任何型別，而不等號。 此外，您可以使用委派建構函式，來簡化您的程式碼，當您有多個建構函式會執行類似的工作。  
  
## <a name="brace-initialization"></a>大括號初始化  
 您可以使用大括號初始設定的任何類別、 結構或等位。 如果類型具有預設建構函式，以隱含或明確宣告，您可以使用預設的大括號初始化 （具有空大括號）。 例如，下列類別可能初始化使用預設值和非預設的大括號初始化：  
  
```cpp  
#include <string>  
using namespace std;  
  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}  
double m_double;  
string m_string;  
};  
  
int main()  
{  
    class_a c1{};  
    class_a c1_1;  
  
    class_a c2{ "ww" };  
    class_a c2_1("xx");  
  
    // order of parameters is the same as the constructor  
    class_a c3{ "yy", 4.4 };  
    class_a c3_1("zz", 5.5);  
}  
  
```  
  
 如果類別具有非預設建構函式，在哪一個類別成員會出現在大括號初始設定式的順序是對應的參數建構函式中出現的順序，不將成員宣告的順序 (如同`class_a`中上述範例）。 否則，如果類型具有未宣告建構函式，成員的大括號初始設定式中出現的順序是依其宣告; 的順序相同在此情況下，您可以初始化最大數量的公用成員為您想，但無法略過任何成員。 下列範例會顯示所使用的順序中的大括號初始化沒有宣告建構函式時：  
  
```cpp  
class class_d {  
public:  
    float m_float;  
    string m_string;  
    wchar_t m_char;  
};  
  
int main()  
{  
    class_d d1{};  
    class_d d1{ 4.5 };  
    class_d d2{ 4.5, "string" };  
    class_d d3{ 4.5, "string", 'c' };  
  
    class_d d4{ "string", 'c' }; // compiler error  
    class_d d5("string", 'c', 2.0 }; // compiler error  
}   
```  
  
 如果預設建構函式明確宣告，但標示為已刪除，無法使用預設的大括號初始化：  
  
```cpp  
class class_f {  
public:  
    class_f() = delete;  
    class_f(string x): m_string { x } {}  
    string m_string;  
};  
int main()  
{  
    class_f cf{ "hello" };  
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function  
}  
```  
  
 您可以使用大括號初始化任何地方您通常會執行初始化 — 例如，做為函式參數或傳回值，或使用`new`關鍵字：  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## <a name="initializerlist-constructors"></a>initializer_list 建構函式  
 [Initializer_list 類別](../standard-library/initializer-list-class.md)代表一份可用在建構函式，並在其他內容中之指定型別的物件。 您可以使用大括號初始設定，以建構 initializer_list:  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  若要使用這個類別，您必須包含[< initializer_list >](../standard-library/initializer-list.md)標頭。  
  
 `initializer_list`可以複製。 在此情況下，新清單的成員會將原始清單成員的參考：  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 標準程式庫容器類別，以及`string`， `wstring`，和`regex`，有`initializer_list`建構函式。 下列範例顯示如何執行這些建構函式進行初始化大括弧括住：  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## <a name="delegating-constructors"></a>委派建構函式  
 許多具有執行類似動作的多個建構函式 — 例如，驗證的參數：  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c() {}  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) {   
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) {  
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
    }  
};  
```  
  
 您無法減少重複的程式碼將會執行所有的驗證，但的程式碼的函式`class_c`會比較容易了解和維護如果一個建構函式可以委派一些至另一個工作。 若要加入委派建構函式，請使用`constructor (. . .) : constructor (. . .)`語法：  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) : class_c(my_max) {   
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
}  
};  
int main() {  
  
    class_c c1{ 1, 3, 2 };  
}  
  
```  
  
 當您逐步執行先前的範例，請注意，建構函式`class_c(int, int, int)`建構函式會先呼叫`class_c(int, int)`，接著呼叫`class_c(int)`。 每個建構函式會執行不會執行的其他建構函式的工作。  
  
 呼叫的第一個建構函式會初始化物件，使其所有成員都會在該點初始化。 您無法執行委派給另一個建構函式的建構函式中的成員初始設定，如下所示：  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    // member initialization here, no delegate  
    class_a(string str) : m_string{ str } {}  
  
    //can’t do member initialization here  
    // error C3511: a call to a delegating constructor shall be the only member-initializer  
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}  
  
    // only member assignment  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string;  
};  
  
```  
  
 下一個範例顯示非靜態資料成員初始設定式的使用。 請注意，是否建構函式也會初始化給定的資料成員，成員初始設定式會覆寫：  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };  
};  
  
int main() {  
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"  
    int y = 4;  
}  
```  
  
 建構函式委派語法不會防止意外建立建構函式遞迴 — Constructor1 呼叫 Constructor2 呼叫 Constructor1 — 和堆疊溢位之前就會擲回任何錯誤。 您必須負責避免循環。  
  
```cpp  
class class_f{  
public:  
    int max;  
    int min;  
  
    // don't do this  
    class_f() : class_f(6, 3){ }  
    class_f(int my_max, int my_min) : class_f() { }  
};  
```