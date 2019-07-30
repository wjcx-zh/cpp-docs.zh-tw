---
title: if-else 陳述式 (C++)
ms.date: 07/20/2019
description: 使用 if-else 語句C++來控制條件式分支。
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 0e9de2d39e09e148c7e4f3ea82c3dadb173c2d0c
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661644"
---
# <a name="if-else-statement-c"></a>if-else 陳述式 (C++)

控制條件分支。 只有在 if*運算式*評估為非零值 (或 TRUE) 時, 才會執行*if 區塊*中的語句。 如果*expression*的值為非零, 則會執行*statement1*和區塊中的任何其他語句, 並略過 else 區塊 (如果有的話)。 如果*expression*的值為零, 則會略過 if-區塊, 並執行 else-區塊 (如果有的話)。 評估為非零的運算式為

- true
- 非 null 指標,
- 任何非零的算術值, 或
- 定義算術、布林值或指標類型之明確轉換的類別類型。 (如需轉換的詳細資訊, 請參閱[標準轉換](../cpp/standard-conversions.md))。

## <a name="syntax"></a>語法

```cpp
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
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

## <a name="if_with_init"></a>if 語句與初始化運算式

**Visual Studio 2017 15.3 版和更新**版本(可用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**If**語句也可以包含宣告和初始化命名變數的運算式。 當只有在 if 區塊範圍內需要變數時, 請使用這種形式的 if 語句。

## <a name="example"></a>範例

```cpp
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

在**if**語句的所有形式中, 都會評估*運算式*(可以有任何值, 但結構除外), 包括所有的副作用。 除非其中一個*語句*包含[break](../cpp/break-statement-cpp.md)、 [continue](../cpp/continue-statement-cpp.md)或[goto](../cpp/goto-statement-cpp.md), 否則 Control 會從**if**語句傳遞至程式中的下一個語句。

`if...else`語句的**else**子句會與相同範圍中沒有對應之**else**語句的最接近 previous **if**語句相關聯。

## <a name="a-nameifconstexpr-if-constexpr-statements"></a><a name="if_constexpr">if constexpr 語句

**Visual Studio 2017 15.3 版和更新**版本(可用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):在函式樣板中, 您可以使用**if constexpr**語句來進行編譯階段分支決策, 而不需要使用多個函數多載。 例如, 您可以撰寫處理參數解壓縮的單一函式 (不需要任何零參數的多載):

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
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

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[switch 陳述式 (C++)](../cpp/switch-statement-cpp.md)