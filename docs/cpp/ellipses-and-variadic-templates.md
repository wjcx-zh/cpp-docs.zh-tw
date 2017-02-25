---
title: "省略符號和 Variadic 範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# 省略符號和 Variadic 範本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何使用省略符號 \(`...`\) 與 C\+\+ variadic 範本。  省略符號在 C 和 C\+\+ 中有[許多用途](../misc/ellipsis-dot-dot-dot.md)。  這些包括函式的變數引數清單。  從 C 執行階段程式庫的 `printf()` 函式是其中一個最知名的範例。  
  
 *variadic 範本* 是支援任意數目的引數傳遞的類別或函式樣板。  這個機制對於 C\+\+ 程式庫開發人員特別有用，因為您可以將它套用至類別樣板和函式樣板，進而提供各種類型安全且非一般的功能和彈性。  
  
## 語法  
 在 variadic 範本中，省略符號有兩種用法。  在參數名稱左邊，它表示*參數封裝*，在參數名稱右邊，則會展開參數封裝至不同的名稱。  
  
 以下是「*variadic 樣板類別*」\(variadic Template Class\) 定義語法的基本範例：  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 對於參數套件與延伸套件，您可以依您的喜好在 ellipsis 周圍增加空白，就像底下這些例子:  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 或是:  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 請注意這篇文章使用第一個例子裡面使用的慣例 \(ellipsis 連接至 `typename`\)。  
  
 在前述範例中，`Arguments` 是參數封裝。  類別 `classname` 可以接受可變數目的引數，如下列範例所示：  
  
```cpp  
  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 使用 variadic 樣板類別定義也可以至少要求一個參數:  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 以下是「*variadic 樣板函式*」\(variadic Template Function\) 語法的基本範例：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 `Arguments` 參數封裝接著會展開以供使用，如下一節**了解 variadic 樣板**中所示。  
  
 可能還有其他形式的 variadic 樣板函式語法，包括但不限於下列範例：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 也允許像 `const` 之類的規範：  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 就像 variadic 樣板類別定義，您可以設定至少需要一個參數的函式:  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 Variadic 範本使用 `sizeof...()` 運算子 \(與舊版 `sizeof()` 運算子無關\)：  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    const unsigned numargs = sizeof...(Arguments);  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
  
```  
  
## 進一步了解省略符號放置  
 在過去，本文說明了定義參數套件和擴充的省略符號放置，「在參數名稱左邊的它表示參數套件，在參數名稱右邊，它展開參數套件中不同的名稱」。  這在技術上是對的，但是可能會造成在轉譯程式碼的混淆。  請考量：  
  
-   在樣板參數清單 \(`template <parameter-list>`\)， `typename...` 引入樣板參數套件。  
  
-   在參數宣告子句 \(`func(parameter-list)`\)， 「最上層」省略符號引入函式參數套件，且省略定位非常重要:  
  
    ```cpp  
  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   若省略符號在參數名稱之後顯示，您有參數封裝擴充。  
  
## 範例  
 說明 variadic 範本功能機制的一個好方法是在重寫 `printf`的某些功能時使用它:  
  
```cpp  
#include <iostream>  
  
using namespace std;  
  
void print() {  
    cout << endl;  
}  
  
template <typename T> void print(const T& t) {  
    cout << t << endl;  
}  
  
template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {  
    cout << first << ", ";  
    print(rest...); // recursive call using pack expansion syntax  
}  
  
int main()  
{  
    print(); // calls first overload, outputting only a newline  
    print(1); // calls second overload  
  
    // these call the third overload, the variadic template,   
    // which uses recursion as needed.  
    print(10, 20);  
    print(100, 200, 300);  
    print("first", 2, "third", 3.14159);  
}  
  
```  
  
## Output  
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  合併 variadic 樣板函式的大部分實作會使用某種形式的遞迴，但只是與傳統遞迴稍有不同。傳統遞迴涉及使用相同簽章呼叫其自身的函式。\(它可以多載或設為範本，不過每次都會選擇相同簽章\)。Variadic 遞迴包含使用不同引數數目 \(幾乎一定會減少\) 來呼叫 variadic 函式樣板，並因此每次戳記不同的簽章。  仍然需要「基底案例」，不過，遞迴的本質是不同的。  
  
## 請參閱  
 [省略符號 \(...\)](../misc/ellipsis-dot-dot-dot.md)