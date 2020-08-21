---
title: union
description: 標準 c + + union class 類型和關鍵字的描述、其使用和限制。
ms.date: 08/18/2020
f1_keywords:
- union_cpp
helpviewer_keywords:
- class type [C++], union as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
no-loc:
- union
- struct
- enum
- class
- static
ms.openlocfilehash: a4dc07df5e7858dffe62478509ee1d8dc759ce96
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88722176"
---
# `union`

> [!NOTE]
> 在 c + + 17 和更新版本中， `std::variant` class 是的型別安全替代方法 union 。

**`union`** 是使用者定義型別，其中所有成員都共用相同的記憶體位置。 這項定義表示，在任何指定的時間，都 union 只能在其成員清單中包含一個以上的物件。 這也表示無論有多少成員 union ，一律會使用足夠的記憶體來儲存最大的成員。

union當您有許多物件和有限的記憶體時，可能會很適合用來節省記憶體。 不過， union 需要額外小心才能正確使用。 您必須負責確保一律存取您所指派的相同成員。 如果任何成員類型具有非一般的 con struct 或，則您必須撰寫額外的程式碼，以明確地 con struct 並終結該成員。 在使用之前 union ，請考慮您嘗試解決的問題，是否可以使用基底和衍生型別來更妥善地表示 class class 。

## <a name="syntax"></a>語法

> **`union`***`tag`* <sub>opt</sub> **`{`** opt *`member-list`***`};`**

### <a name="parameters"></a>參數

*`tag`*<br/>
提供給的型別名稱 union 。

*`member-list`*<br/>
union可以包含的成員。

## <a name="declare-a-no-locunion"></a>宣告 union

union使用關鍵字來開始的宣告 **`union`** ，並將成員清單括在大括弧中：

```cpp
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};

int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```

## <a name="use-a-no-locunion"></a>使用 union

在上述範例中，任何存取的程式碼都 union 需要知道哪些成員會保存資料。 此問題最*常見的解決方案 union *稱為「差異」。 它會將 union 放在中 struct ，並包含 enum 成員來指出目前儲存在中的成員類型 union 。 下列範例示範基本模式：

```cpp
#include <queue>

using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    int StationId;
    time_t time;
    double current;
    double max;
    double min;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    WeatherDataType type;
    union
    {
        TempData temp;
        WindData wind;
    };
};

// Functions that are specific to data types
void Process_Temp(TempData t) {}
void Process_Wind(WindData w) {}

void Initialize(std::queue<Input>& inputs)
{
    Input first;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    Input second;
    second.type = WeatherDataType::Wind;
    second.wind = { 204, 1418859354, 14, 27 };
    inputs.push(second);
}

int main(int argc, char* argv[])
{
    // Container for all the data records
    queue<Input> inputs;
    Initialize(inputs);
    while (!inputs.empty())
    {
        Input const i = inputs.front();
        switch (i.type)
        {
        case WeatherDataType::Temperature:
            Process_Temp(i.temp);
            break;
        case WeatherDataType::Wind:
            Process_Wind(i.wind);
            break;
        default:
            break;
        }
        inputs.pop();

    }
    return 0;
}
```

在上述範例中， union 中的沒有 `Input` struct 名稱，因此稱為 *匿名* union 。 您可以直接存取其成員，就像是的成員一樣 struct 。 如需如何使用匿名的詳細資訊 union ，請參閱[匿名 union ](#anonymous_unions)區段。

先前的範例顯示您也可以使用 class 衍生自通用基底的型別來解決的問題 class 。 您可以根據容器中每個物件的執行時間類型，將程式碼分支。 您的程式碼可能更容易維護及瞭解，但也可能比使用更慢 union 。 此外，您也 union 可以使用來儲存不相關的類型。 union可讓您以動態方式變更預存值的型別，而不需要變更變數本身的型別 union 。 例如，您可以建立的異類陣列 `MyUnionType` ，其元素會儲存不同類型的不同值。

您可以輕鬆地誤用 `Input` struct 範例中的。 使用者可以正確地使用鑒別子來存取保存資料的成員。 您可以藉由建立和提供特殊的存取函式來防止誤用 union **`private`** ，如下一個範例所示。

## <a name="unrestricted-no-locunion-c11"></a>不受限制的 union (c + + 11) 

在 c + + 03 及更早版本中， union static 只要型別沒有 class 使用者提供 con struct or、de struct or 或指派運算子，就可以包含具有類型的非資料成員。 在 C++11 中，已移除這些限制。 如果您在中包含這類成員 union ，編譯器會自動將非使用者提供的任何特殊成員函式標示為 **`deleted`** 。 如果在 union 或中是匿名的 union class struct ，則任何不是由使用者提供的特殊成員函式 class struct 都會標示為 **`deleted`** 。 下列範例顯示如何處理此案例。 的其中一個成員 union 具有需要這項特殊處理的成員：

```cpp
// for MyVariant
#include <crtdbg.h>
#include <new>
#include <utility>

// for sample objects and output
#include <string>
#include <vector>
#include <iostream>

using namespace std;

struct A
{
    A() = default;
    A(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    //...
};

struct B
{
    B() = default;
    B(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    vector<int> vec;
    // ...
};

enum class Kind { None, A, B, Integer };

#pragma warning (push)
#pragma warning(disable:4624)
class MyVariant
{
public:
    MyVariant()
        : kind_(Kind::None)
    {
    }

    MyVariant(Kind kind)
        : kind_(kind)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A();
            break;
        case Kind::B:
            new (&b_) B();
            break;
        case Kind::Integer:
            i_ = 0;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    ~MyVariant()
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            a_.~A();
            break;
        case Kind::B:
            b_.~B();
            break;
        case Kind::Integer:
            break;
        default:
            _ASSERT(false);
            break;
        }
        kind_ = Kind::None;
    }

    MyVariant(const MyVariant& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(other.a_);
            break;
        case Kind::B:
            new (&b_) B(other.b_);
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    MyVariant(MyVariant&& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(move(other.a_));
            break;
        case Kind::B:
            new (&b_) B(move(other.b_));
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
    }

    MyVariant& operator=(const MyVariant& other)
    {
        if (&other != this)
        {
            switch (other.kind_)
            {
            case Kind::None:
                this->~MyVariant();
                break;
            case Kind::A:
                *this = other.a_;
                break;
            case Kind::B:
                *this = other.b_;
                break;
            case Kind::Integer:
                *this = other.i_;
                break;
            default:
                _ASSERT(false);
                break;
            }
        }
        return *this;
    }

    MyVariant& operator=(MyVariant&& other)
    {
        _ASSERT(this != &other);
        switch (other.kind_)
        {
        case Kind::None:
            this->~MyVariant();
            break;
        case Kind::A:
            *this = move(other.a_);
            break;
        case Kind::B:
            *this = move(other.b_);
            break;
        case Kind::Integer:
            *this = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
        return *this;
    }

    MyVariant(const A& a)
        : kind_(Kind::A), a_(a)
    {
    }

    MyVariant(A&& a)
        : kind_(Kind::A), a_(move(a))
    {
    }

    MyVariant& operator=(const A& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(a);
        }
        else
        {
            a_ = a;
        }
        return *this;
    }

    MyVariant& operator=(A&& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(move(a));
        }
        else
        {
            a_ = move(a);
        }
        return *this;
    }

    MyVariant(const B& b)
        : kind_(Kind::B), b_(b)
    {
    }

    MyVariant(B&& b)
        : kind_(Kind::B), b_(move(b))
    {
    }

    MyVariant& operator=(const B& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(b);
        }
        else
        {
            b_ = b;
        }
        return *this;
    }

    MyVariant& operator=(B&& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(move(b));
        }
        else
        {
            b_ = move(b);
        }
        return *this;
    }

    MyVariant(int i)
        : kind_(Kind::Integer), i_(i)
    {
    }

    MyVariant& operator=(int i)
    {
        if (kind_ != Kind::Integer)
        {
            this->~MyVariant();
            new (this) MyVariant(i);
        }
        else
        {
            i_ = i;
        }
        return *this;
    }

    Kind GetKind() const
    {
        return kind_;
    }

    A& GetA()
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    const A& GetA() const
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    B& GetB()
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    const B& GetB() const
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    int& GetInteger()
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

    const int& GetInteger() const
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

private:
    Kind kind_;
    union
    {
        A a_;
        B b_;
        int i_;
    };
};
#pragma warning (pop)

int main()
{
    A a(1, "Hello from A");
    B b(2, "Hello from B");

    MyVariant mv_1 = a;

    cout << "mv_1 = a: " << mv_1.GetA().name << endl;
    mv_1 = b;
    cout << "mv_1 = b: " << mv_1.GetB().name << endl;
    mv_1 = A(3, "hello again from A");
    cout << R"aaa(mv_1 = A(3, "hello again from A"): )aaa" << mv_1.GetA().name << endl;
    mv_1 = 42;
    cout << "mv_1 = 42: " << mv_1.GetInteger() << endl;

    b.vec = { 10,20,30,40,50 };

    mv_1 = move(b);
    cout << "After move, mv_1 = b: vec.size = " << mv_1.GetB().vec.size() << endl;

    cout << endl << "Press a letter" << endl;
    char c;
    cin >> c;
}
```

union無法儲存參考。 union也不支援繼承。 這表示您不能使用 union 做為基底 class ，或繼承自另一個 class ，或有虛擬函式。

## <a name="initialize-a-no-locunion"></a>初始化 union

您可以藉 union 由指派以大括弧括住的運算式，在相同的語句中宣告和初始化。 運算式會進行評估並指派給的第一個欄位 union 。

```cpp
#include <iostream>
using namespace std;

union NumericType
{
    short       iValue;
    long        lValue;
    double      dValue;
};

int main()
{
    union NumericType Values = { 10 };   // iValue = 10
    cout << Values.iValue << endl;
    Values.dValue = 3.1416;
    cout << Values.dValue << endl;
}
/* Output:
10
3.141600
*/
```

`NumericType` union (在概念上排列) ，如下圖所示。

![將資料儲存在數數值型別：：：非 loc (聯集) ：：：](../cpp/media/vc38ul1.png "將資料儲存在 NumericType：：：非 loc (聯集) ：：：") <br/>
資料儲存在 `NumericType`union

## <a name="anonymous-no-locunion"></a><a name="anonymous_unions"></a> 匿名 union

匿名 union 是指沒有或的宣告 *`class-name`* *`declarator-list`* 。

> **`union  {`**  *`member-list`*  **`}`**

匿名中宣告的名稱 union 會直接使用，例如非成員變數。 這表示在匿名中宣告的名稱在 union 周圍的範圍中必須是唯一的。

匿名 union 可能會有下列額外的限制：

- 如果在檔案或命名空間範圍中宣告，則也必須將它宣告為 **`static`** 。

- 它只能有 **`public`** 成員; **`private`** **`protected`** 在匿名中具有和成員會 union 產生錯誤。

- 它不能有成員函式。

## <a name="see-also"></a>請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[`class`](../cpp/class-cpp.md)<br/>
[`struct`](../cpp/struct-cpp.md)
