---
title: if else 陳述式 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8de2511096766cc4852c1c612eccb7dc65713218
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="if-else-statement-c"></a>if-else 陳述式 (C++)
控制條件分支。 中的陳述式*if 區塊*才會執行*if 運算式*評估為非零值 (或`true`)。 如果值*運算式*非零， *statement1*區塊中的任何其他陳述式執行和 else 區塊，如果有的話，會略過。 如果值*運算式*為零，則會略過 if 區塊和執行其他的區塊，如果有的話。 評估為非零的運算式
- `true`
- 非 null 指標，
- 任何非零的算術值，或 
- 類別型別定義的模稜兩可的轉換到算術、 布林值或指標類型。 (如需轉換的資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。)   
  
## <a name="syntax"></a>語法  
  
```  
  
if ( expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
} 

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
}  

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
} 
```  
## <a name="example"></a>範例  
```  
// if_else_statement.cpp  
#include <iostream>

using namespace std;

class C
{
    public:
    void do_somthing(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

  // no else statement
    if (x == 10)
    {
        x = 0; 
    }
    
  
    C* c;
  init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```  
## <a name="if-statement-with-an-initializer"></a>如果初始設定式的陳述式
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):**如果**陳述式也可能包含宣告和初始化具名的變數的運算式。 如果區塊範圍內的變數只在需要時，請使用這種形式的 if 陳述式。 

```cpp
## Example  
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>


using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }


    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }

}
```

 在所有表單中的**如果**陳述式，*運算式*，且可以包含建立結構，以外的任何值會評估，包括所有副作用。 控制權會傳遞從**如果**陳述式中程式的下一個陳述式，除非其中一個*陳述式*s 包含[中斷](../cpp/break-statement-cpp.md)，[繼續](../cpp/continue-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)。  
  
 **Else**子句`if...else`陳述式是相關聯的最接近先前**如果**陳述式沒有相對應位於相同範圍**else**陳述式。   

## <a name="constexpr-if-statements"></a>constexpr 如果陳述式
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 在函式樣板，您可以使用**constexpr 如果**做出編譯時期分支不含陳述式不必訴諸於多個函式多載。 例如，您可以撰寫單一函式的控制代碼參數，解壓縮 （需要沒有零參數多載）： 

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
// handle t
   do_something(t);

   // handle r conditionally
   constexpr if (sizeof...(r)) 
   {
      
      f(r...); 
   }
   else
   {
       g(r...);
   }
}
```

  
 
## <a name="see-also"></a>另請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [switch 陳述式 (C++)](../cpp/switch-statement-cpp.md)