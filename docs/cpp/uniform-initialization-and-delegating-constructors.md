---
title: "統一初始設定和委派建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# 統一初始設定和委派建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在現代 C\+\+，您可以為任何型別使用 *括號初始化* ，但其中不含等號。  此外，當您使用多個可以簡化工作的建構函時候，您也可以使用委派的建構函式以簡化您的程式碼。  
  
## 括號初始化  
 您可以為所有類別、結構或等位使用括號來初始化。  如果型別有預設建構函式，無論是隱含或是明確宣告，您可以使用預設括號初始化 \(包含空括號\)。  例如，使用預設和非預設的括號初始化，下列類別可能初始化:  
  
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
  
 如果一個類別有非預設的建構函式，那類別成員出現在brace initializer 的順序會跟相關參數在建構函式中出現的順序一樣, 而不是成員被宣告的順序 \(如上述範例的 `class_a` \)。  否則，如果這個型別沒有宣告建構函式，成員會出現在括號初始設定式的命令不相同則為其宣告命令; 在這種情況下，您可以如您所願使用許多公用成員，您不能略過任何成員。  下列範例顯示用以括號初始化的命令，而未宣告的建構函式時:  
  
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
  
 如果預設建構函式明確地宣告，但是標記為刪除，預設無法使用括號初始化:  
  
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
  
 您可以使用括號來初始化任何地方初始化中通常會，比如函式參數或傳回值，或使用 `new` 關鍵字:  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## initializer\_list 建構函式  
 [initializer\_list Class](../standard-library/initializer-list-class.md) 表示可用於建構函式所指定型別的物件清單和其他內容。  您可以使用括號初始化以建構 initializer\_list:  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  若要使用這個類別，您必須包含 [\<initializer\_list\>](../standard-library/initializer-list.md) 標頭。  
  
 `initializer_list` 可以複製。  在這個案例中，新清單的成員是對原始清單成員的參考:  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 標準文件庫容器類別和 \( `string`、 `wstring`和 `regex`，具有 `initializer_list` 建構函式。  下列範例示範如何使用這些建構函式的括號初始化:  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## 委派建構函式  
 許多類別擁有相同項目中的多個建構函式，以驗證參數:  
  
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
  
 您可以透過增加一個進行驗證的函式以減少程式碼，不過，如果建構函式可以委派到其他工作，了解和維護`class_c` 的程式碼將更為容易。  若要加入委派的建構函式，請使用 `constructor (. . .) : constructor (. . .)` 語法:  
  
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
  
 您透過前導參照逐步執行，請注意建構函式 `class_c(int, int, int)` 第一次呼叫建構函式 `class_c(int, int)`，接著呼叫 `class_c(int)`。  每個建構函式會執行未由其他建構函式只執行的工作。  
  
 第一個被呼叫建構函式的稱為初始化物件，他所有的成員都將被初始化。  您無法在委派至另一個建構函式的成員初始設定，如下所示:  
  
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
  
 下一個範例顯示使用非靜態資料成員初始設定式。  請注意，如果建構函式初始化一個已有給定值的成員，則初始化的同時，此成員會被覆寫:  
  
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
  
 建構函式委派語法不會預防意外產生的遞迴建構函式—Constructor1呼叫已經呼叫Constructor1的Constructor2—而且直到堆疊溢位之前都不會擲回任何錯誤訊息。  避免循環為您的責任。  
  
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