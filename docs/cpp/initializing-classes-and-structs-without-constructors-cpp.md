---
title: 為類別、結構和聯合進行初始化
description: 將大括弧初始化與任何C++類、結構或聯合
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374067"
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

請注意,當類或結構沒有構造函數時,您按在類中聲明成員的順序提供列表元素。 如果類具有構造函數,請按參數的順序提供元素。 如果類型具有預設構造函數(隱式或顯式聲明),則可以使用預設大括弧初始化(使用空大括弧)。 例如,可以使用預設和非預設大括弧初始化初始化以下類:

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

如果類具有非預設構造函數,則類成員在大括弧初始化器中顯示的順序是相應參數在構造函數中顯示的順序,而不是成員聲明的順序(如`class_a`上例所示)。 否則,如果類型沒有聲明構造函數,則成員在大括弧初始化器中出現的順序與聲明它們的順序相同;在這種情況下,您可以根據需要初始化任意數量的公共成員,但不能跳過任何成員。 下面的範例顯示了在沒有聲明建構函數時大括弧初始化中使用的順序:

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

若顯式宣告預設建構函數但標記為已刪除,則無法使用預設大括弧初始化:

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

您可以在通常執行初始化的任意位置使用大括弧初始化,例如,作為函數參數或返回值,或者使用**新**關鍵字:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

在 **/std:c++17**模式下,空大括弧初始化的規則稍微限制一些。 請參考[派生建構函數與延伸的聚合初始化](constructors-cpp.md#extended_aggregate)。

## <a name="initializer_list-constructors"></a>initializer_list建構函數

[initializer_list類](../standard-library/initializer-list-class.md)表示可在建構函數和其他上下文中使用的指定類型的物件的清單。 可以使用大括弧初始化構造initializer_list:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> 要使用此類,必須包括[\<initializer_list>](../standard-library/initializer-list.md)標頭。

可以`initializer_list`複製 。 在這種情況下,新列表的成員是原始清單成員的引用:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

標準庫容器類和`string`,`wstring``regex`和,`initializer_list`具有建構函數。 以下範例展示如何使用這些建構函數執行大括弧初始化:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
[建構函式](../cpp/constructors-cpp.md)
