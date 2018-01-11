---
title: "省略符號和 Variadic 範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6d3d0fa1dc4e2e4d817280fa83b26c56732cb2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ellipses-and-variadic-templates"></a>省略符號和 Variadic 範本
本文示範如何使用省略符號 (`...`) 與 c + + 的 variadic 樣板。 省略符號已在 C 和 c + + 中的許多用途。 其中包括對於函式的變數引數清單。 `printf()`函式的 C 執行階段程式庫是其中一個最知名的範例。  
  
 A *variadic 樣板*是支援任意數目的引數的類別或函式範本。 這項機制是對於 c + + 程式庫開發人員特別有用，因為您可以將它套用到類別樣板和函式樣板，並藉此提供各種不同的型別安全和非簡單式的功能與彈性。  
  
## <a name="syntax"></a>語法  
 Variadic 範本是在兩種方式中使用省略符號。 參數名稱左邊，它表示*參數封裝*，參數名稱右邊，它展開參數封裝至不同的名稱。  
  
 以下是基本範例*variadic 樣板類別*定義語法：  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 對於參數封裝和展開，您可以依您的喜好在省略符號周圍加入空白，如下面這些範例所示：  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 或這個：  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 請注意，本文使用第一個範例中顯示的慣例 (省略符號附加至 `typename`)。  
  
 在前述範例中，`Arguments` 是參數封裝。 類別`classname`可以接受變動數目的引數，如下列範例所示：  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 藉由使用 variadic 樣板類別定義，您也可以要求至少一個參數：  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 以下是基本範例*variadic 樣板函式*語法：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 `Arguments`下一節中所示，供使用，然後展開參數封裝**了解 variadic 樣板**。  
  
 可能會使用其他形式的 variadic 樣板函式語法，包括但不是限於這些範例：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 規範喜歡`const`也允許：  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 做為 variadic 樣板類別定義，您可以進行需要至少一個參數的函式：  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 Variadic 範本使用`sizeof...()`運算子 (與舊版不相關`sizeof()`運算子):  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    constexpr auto numargs{ sizeof...(Arguments) };  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
  
```  
  
## <a name="more-about-ellipsis-placement"></a>進一步了解省略符號位置  
 在過去，本文說明了定義參數封裝和展開的省略符號位置，「在參數名稱左邊的它表示參數封裝，在參數名稱右邊，它展開參數封裝至不同的名稱」。 這在技術上是對的，但是在轉譯程式碼上可能會造成混淆。 請考慮：  
  
-   樣板參數清單中 (`template <parameter-list>`)，`typename...`引入樣板參數封裝。  
  
-   在參數宣告子句 (`func(parameter-list)`)、 「 最上層 」 的省略符號導入了函式參數封裝，並省略符號位置，請務必：  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   若省略符號在參數名稱之後顯示，您有參數封裝展開。  
  
## <a name="example"></a>範例  
 說明 variadic 樣板函式機制的好方法是使用中的某些功能的重新撰寫`printf`:  
  
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
  
## <a name="output"></a>輸出  
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  大部分併入 variadic 樣板函式的實作使用某種形式中，遞迴，但是稍有不同於傳統的遞迴。  傳統的遞迴牽涉到使用相同的簽章來呼叫本身的函式。 （它可能多載或樣板化，但相同的簽章會選擇每次）。Variadic 遞迴牽涉到使用不同的 （幾乎遞減） 數目的引數，並藉此戳記出不同的簽章每次呼叫 variadic 函式樣板。 「 基底大小寫 」 仍需要，但遞迴方式不同。  
  
