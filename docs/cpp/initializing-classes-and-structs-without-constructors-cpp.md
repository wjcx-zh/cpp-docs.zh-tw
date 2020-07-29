---
title: 類別、結構和等位的括弧初始化
description: 使用括弧初始化搭配任何 c + + 類別、結構或等位
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: d862ff01ef7375c9d46791f7549d8a07682c3586
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227422"
---
# <a name="brace-initialization"></a>大括弧初始化

您不一定需要定義類別的建構函式，尤其是相當簡單的類別。 使用者可以使用統一初始化來初始化類別或結構的物件 (如下列範例所示)：

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

請注意，當類別或結構沒有任何函式時，您會以類別中宣告成員的順序提供清單元素。 如果類別有一個函式，請以參數的順序提供元素。 如果類型具有隱含或明確宣告的預設的處理常式，您可以使用預設的大括弧初始化（含空的大括弧）。 例如，您可以使用預設和非預設的大括弧初始化來初始化下列類別：

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

如果類別具有非預設的處理常式，則類別成員在大括弧初始化運算式中出現的順序，就是對應參數出現在函式中的順序，而不是宣告成員的順序（如同 `class_a` 上一個範例中的）。 否則，如果類型沒有宣告的函式，成員在大括弧初始化運算式中出現的順序會與宣告的順序相同。在此情況下，您可以視需要初始化多個公用成員，但不能略過任何成員。 下列範例顯示沒有宣告的函式時，在大括弧初始化中使用的順序：

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
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

如果預設的函式已明確宣告，但標示為已刪除，則無法使用預設的大括弧初始化：

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

您可以在一般執行初始化的任何地方使用括弧初始化，例如，做為函式參數或傳回值，或使用 **`new`** 關鍵字：

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

在 **/std： c + + 17**模式中，空白大括弧初始化的規則會略有限制。 請參閱[衍生的函數和擴充的匯總初始化](constructors-cpp.md#extended_aggregate)。

## <a name="initializer_list-constructors"></a>initializer_list 的構造函式

[Initializer_list 類別](../standard-library/initializer-list-class.md)代表指定類型的物件清單，可用於函數和其他內容中。 您可以使用大括弧初始化來建立 initializer_list：

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> 若要使用這個類別，您必須包含 [\<initializer_list>](../standard-library/initializer-list.md) 標頭。

`initializer_list`可以複製。 在此情況下，新清單的成員會參考原始清單的成員：

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

標準程式庫容器類別，以及、 `string` `wstring` 和 `regex` 都有一個 `initializer_list` 函數。 下列範例示範如何使用這些函式進行括弧初始化：

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
[建構函式](../cpp/constructors-cpp.md)
