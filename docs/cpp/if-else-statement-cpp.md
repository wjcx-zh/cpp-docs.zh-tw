---
title: if-else 陳述式 (C++)
ms.date: 07/17/2017
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 16aa65ab64d9fd855ae3306da88f8eb14eec759c
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330823"
---
# <a name="if-else-statement-c"></a>if-else 陳述式 (C++)

控制條件分支。 中的陳述式*if 區塊*才會執行*if 運算式*評估為非零值 （或 TRUE）。 如果值*運算式*為非零值， *statement1*和區塊中的任何其他陳述式會執行 else 區塊，如果有的話，會略過。 如果值*運算式*為零，則會略過 if 區塊和 else 區塊，如果存在，則會執行。 評估為非零的運算式

- true
- 非 null 指標，
- 任何非零的算術值，或
- 類別型別定義的模稜兩可的轉換到算術、 布林值或指標類型。 (如需轉換的詳細資訊，請參閱 <<c0> [ 標準轉換](../cpp/standard-conversions.md)。)

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

## <a name="if_with_init"></a> 如果初始設定式的陳述式

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**如果**陳述式也可能包含宣告和初始化具名的變數的運算式。 變數只需要在 if 區塊的範圍內時，請使用這種形式的 if 陳述式。

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

在所有表單中的**如果**陳述式*運算式*，且可以包含結構以外的任何值會評估，包括所有副作用。 控制權會傳遞從**如果**陳述式中程式的下一個陳述式，除非其中一個*陳述式*s 包含[中斷](../cpp/break-statement-cpp.md)，[繼續](../cpp/continue-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)。

**Else**子句`if...else`陳述式是相關聯的最接近上一個**如果**陳述式中相同範圍中沒有任何對應**其他**陳述式。

## <a name="a-nameifconstexpr-if-constexpr-statements"></a><a name="if_constexpr"> 如果 constexpr 陳述式

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 在函式樣板，您可以使用**如果 constexpr**編譯時間分支的決策，而不需要的陳述式不必訴諸於多個函式多載。 例如，您可以撰寫單一函式的控制代碼參數，解壓縮 （沒有任何零參數多載，就需要）：

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