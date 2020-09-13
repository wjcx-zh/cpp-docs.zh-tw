---
title: 建構函式 (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 3694dc72860892d778533de2e40898faf9cc287d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042156"
---
# <a name="constructors-c"></a>建構函式 (C++)

若要自訂類別成員的初始化方式，或在建立類別的物件時叫 *用函數，請定義一個函*式。 建構函式的名稱與類別的名稱相同，但沒有傳回值。 您可以視需要定義任意數量的多載的函式，以各種方式自訂初始化。 一般而言，這些函式具有公用存取範圍，因此類別定義或繼承階層之外的程式碼可以建立類別的物件。 但是，您也可以將函式宣告為 **`protected`** 或 **`private`** 。

您可以選擇性地採用成員 init 清單。 這是比起在函式主體中指派值更有效率的方式，來初始化類別成員。 下列範例顯示具有三個多載的函式的類別 `Box` 。 最後兩個使用成員 init 清單：

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

當您宣告類別的實例時，編譯器會根據多載解析的規則，選擇要叫用的函式：

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- 函式可以宣告為 **`inline`** 、 [explicit](#explicit_constructors) **`friend`** 或 [constexpr](#constexpr_constructors)。
- 函式可以初始化已宣告為、或的物件 **`const`** **`volatile`** **`const volatile`** 。 在完成函式之後，物件就會變成 **`const`** 。
- 若要在實檔案中定義一個函式，請提供它一個限定名稱，如同其他任何成員函式： `Box::Box(){...}` 。

## <a name="member-initializer-lists"></a><a name="member_init_list"></a> 成員初始化運算式清單

函式可以選擇性地擁有成員初始化運算式清單，其會在執行函式主體之前初始化類別成員。  (請注意，成員初始化運算式清單與[std：： initializer_list \<T> ](../standard-library/initializer-list-class.md)類型的*初始化運算式清單*不同。 ) 

使用成員初始化運算式清單時，最好不要在函式主體中指派值，因為它會直接初始化成員。 在下列範例中，會顯示成員初始化運算式清單是由所有 **識別碼 (引數) ** 在冒號之後的運算式所組成：

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

識別碼必須參考類別成員;它會使用引數的值進行初始化。 引數可以是其中一個函式參數、函式呼叫或[std：： initializer_list \<T> ](../standard-library/initializer-list-class.md)。

**`const`** 參考型別的成員和成員必須在成員初始化運算式清單中初始化。

在初始化運算式清單中，應該在初始化運算式清單中建立參數化基類的函式的呼叫，以確保在執行衍生的函式之前，會完整初始化基類。

## <a name="default-constructors"></a><a name="default_constructors"></a> 預設的函式

*預設* 的函式通常沒有任何參數，但它們可以有具有預設值的參數。

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

預設的函式是其中一個 [特殊成員](special-member-functions.md)函式。 如果在類別中未宣告任何的函式，編譯器會提供隱含的預設函式 **`inline`** 。

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

如果您依賴隱含預設的函式，請務必在類別定義中初始化成員，如先前的範例所示。 如果沒有這些初始化運算式，成員就會被初始化，而磁片區 ( # A1 呼叫會產生垃圾值。 一般來說，即使不依賴隱含預設的函式，也能以這種方式初始化成員是不錯的作法。

您可以藉由將它定義為 [已刪除](#explicitly_defaulted_and_deleted_constructors)來防止編譯器產生隱含預設的函式：

```cpp
    // Default constructor
    Box() = delete;
```

如果任何類別成員不是預設的可建構，則編譯器產生的預設函式將會定義為 deleted。 例如，類別型別的所有成員及其類別型別成員都必須有可存取的預設函式和析構函數。 所有參考型別的資料成員以及 **`const`** 成員都必須有預設成員初始化運算式。

當您呼叫編譯器產生的預設的函式，並嘗試使用括弧時，會發出警告：

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

這是「最令人惱怒的語法解析」(Most Vexing Parse) 問題範例。 由於範例運算式可解譯為函式的宣告或做為預設建構函式的引動過程，而且由於 C++ 剖析器偏好宣告更勝於其他項目，因此運算式被視為函式宣告。 如需詳細資訊，請參閱 [大部分的繁瑣語法剖析](https://en.wikipedia.org/wiki/Most_vexing_parse)。

如果已宣告任何非預設建構函式，編譯器不會提供預設建構函式：

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

如果類別沒有預設建構函式，該類別的物件陣列無法透過單獨使用方括號語法來建構。 例如，根據上述程式碼區塊，Boxes 陣列無法宣告如下：

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

不過，您可以使用一組初始化運算式清單來初始化 Box 物件的陣列：

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

如需詳細資訊，請參閱 [初始化運算式](initializers.md)。

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a> 複製函式

*複製*函式會藉由複製相同類型之物件的成員值來初始化物件。 如果您的類別成員都是簡單類型（例如純量值），則編譯器產生的複製函式就已足夠，您也不需要自行定義。 如果您的類別需要更複雜的初始化，則您需要執行自訂複製的函式。 例如，如果類別成員是指標，則您需要定義複製的函式來配置新的記憶體，並複製另一個指向物件的值。 編譯器產生的複製函式只會複製指標，讓新的指標仍然指向其他的記憶體位置。

複製的函式可能會有下列其中一種簽章：

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

當您定義複製的函式時，您也應該定義複製指派運算子 (=) 。 如需詳細資訊，請參閱 [指派](assignment.md) 和複製函式 [和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)。

您可以藉由將複製的方法定義為已刪除，來防止複製您的物件：

```cpp
    Box (const Box& other) = delete;
```

嘗試複製物件時，會產生錯誤 *C2280：嘗試參考已刪除的*函式。

## <a name="move-constructors"></a><a name="move_constructors"></a> 移動函數

*移動*函式是特殊成員函式，可將現有物件資料的擁有權移至新的變數，而不會複製原始資料。 它會採用右值參考做為第一個參數，而任何其他參數都必須有預設值。 移動函式在傳遞大型物件時，可能會大幅增加程式的效率。

```cpp
Box(Box&& other);
```

編譯器會在某些情況下，選擇移動的函式，其中物件是由相同類型的另一個物件初始化，而該物件是即將終結且不再需要它的資源。 下列範例顯示使用多載解析選取移動函式時的一個案例。 在呼叫的函 `get_Box()` 式中，傳回的值為 *Xvalue* (到期) 的值。 它不會指派給任何變數，因此即將移出範圍。 為了提供此範例的動機，讓我們為 Box 提供代表其內容的大型字串向量。 移動函式不會複製向量和其字串，而是從過期值 "box" 中「竊取」，讓向量現在屬於新的物件。 的呼叫 `std::move` 是必要的，因為 `vector` 和 `string` 類別會執行自己的移動函式。

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Print_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

如果類別未定義移動函式，則編譯器會在沒有使用者宣告的複製函式、複製指派運算子、移動指派運算子或自訂函數時產生隱含的函式。 如果未定義明確或隱含移動的函式，則會改為使用複製函式的作業。 如果類別宣告移動函式或移動指派運算子，則會將隱含宣告的複製函式定義為已刪除。

如果任何屬於類別類型的成員缺少任何一個函式，或編譯器無法判斷要用於移動作業的哪一個函式，則會將隱含宣告的移動函式定義為已刪除。

如需如何撰寫非一般移動函式的詳細資訊，請參閱 [移動函式和移動指派運算子 (c + +) ](../cpp/move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a> 明確預設和已刪除的函式

您可以明確 *預設* 的複製函式、預設的函式、移動的函式、複製指派運算子、移動指派運算子和析構函數。 您可以明確地 *刪除* 所有特殊成員函式。

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

如需詳細資訊，請參閱 [明確預設和已刪除的函](../cpp/explicitly-defaulted-and-deleted-functions.md)式。

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a> constexpr 函式

若為，則可將函式宣告為[constexpr](constexpr-cpp.md)

- 它會宣告為預設值，否則會滿足所有 [constexpr](constexpr-cpp.md#constexpr_functions) 函式的條件（一般）;
- 類別沒有任何虛擬基類;
- 每個參數都是 [常數值型別](trivial-standard-layout-and-pod-types.md#literal_types);
- 主體不是函數 try 區塊;
- 所有非靜態資料成員和基類子物件都會初始化;
- 如果類別 () 具有 variant 成員的等位，或 (b) 具有匿名聯集，則只會初始化其中一個等位成員;
- 類別類型的每個非靜態資料成員，以及所有基類子物件都有 constexpr 的函式

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a> 初始化運算式清單的函式

如果函式接受[std：： initializer_list \<T\> ](../standard-library/initializer-list-class.md)做為其參數，而且任何其他參數都有預設引數，則會在透過直接初始化來具現化類別時，于多載解析中選取該函式。 您可以使用 initializer_list 來初始化任何可以接受它的成員。 例如，假設先前) 的 Box 類別 (有 `std::vector<string>` 成員 `m_contents` 。 您可以提供如下的函數：

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

然後建立如下的 Box 物件：

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a> 明確的函式

如果類別的建構函式具有單一參數，或者，所有參數 (但其中一個除外) 都有預設值，則參數類型可以隱含地轉換為類別類型。 例如，如果 `Box` 類別具有建構函式，如下：

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Box 可能初始化如下：

```cpp
Box b = 42;
```

或將 int 傳遞給採用 Box 的函式：

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

在某些情況下，這類轉換十分有用，但它們可能更常導致您程式碼中的細微但嚴重的錯誤。 一般來說，您應該 **`explicit`** 在 (的函式和使用者定義的運算子) 上使用關鍵字，以防止這種類型的隱含類型轉換：

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

建構函式是明確建構函式時，此行會造成編譯器錯誤：`ShippingOrder so(42, 10.8);`。  如需詳細資訊，請參閱 [使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)。

## <a name="order-of-construction"></a><a name="order_of_construction"></a> 結構的順序

建構函式會依此順序執行其工作：

1. 它會依宣告順序呼叫基底類別和成員建構函式。

1. 如果類別是從虛擬基底類別衍生，它會初始化物件的虛擬基底指標。

1. 如果類別具有或繼承虛擬函式，它會初始化物件的虛擬函式指標。 虛擬函式指標指向類別的虛擬函式表，以便讓虛擬函式呼叫正確繫結至程式碼。

1. 它會執行其函式主體內的任何程式碼。

下列範例顯示在衍生類別的建構函式中呼叫基底類別和成員建構函式的順序。 首先會呼叫基底建構函式，然後依其出現在類別宣告中的順序初始化基底類別成員，最後會呼叫衍生的建構函式。

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

輸出如下：

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

衍生類別建構函式一定會呼叫基底類別建構函式，因此，它可以依賴完全建構的基底類別，才進行任何額外的工作。 基類的函式會以衍生的順序來呼叫，例如，如果衍生自衍生自 `ClassA` `ClassB` 的，則會 `ClassC` 先呼叫此函式 `ClassC` ，然後再呼叫函式 `ClassB` ，然後再呼叫 `ClassA` 函式。

如果基底類別沒有預設建構函式，您必須在衍生類別建構函式中提供基底類別建構函式參數：

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

如果建構函式擲回例外狀況，解構順序是建構順序的相反：

1. 在建構函式主體中的程式碼會回溯。

1. 基底類別和成員物件會依宣告的反向順序終結。

1. 如果建構函式為非委派，所有完全建構的基底類別物件和成員都會終結。 不過，因為物件本身未完全建構，所以不會執行解構函式。

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a> 衍生的函式和延伸匯總初始化

如果基類的函式不是公用的，但可供衍生類別存取，則在 **/std： c + + 17** 模式的 Visual Studio 2017 和更新版本中，您無法使用空的大括弧來初始化衍生類型的物件。

下列範例顯示 C++14 一致性行為：

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

在 C++17 中，`Derived` 已視作彙總類型。 因此，透過私用預設建構函式將 `Base` 初始化會直接包含在擴充彙總初始化規則的過程。 `Base` 私用建構函式在先前會透過 `Derived` 建構函式呼叫，而成功的因素是 friend 宣告所致。

下列範例顯示在 **/std： c + + 17** 模式中 Visual Studio 2017 和更新版本中的 c + + 17 行為：

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>具有多重繼承之類別的函式

如果類別從多個基底類別衍生，基底類別建構函式是依照其列在衍生類別宣告中的順序進行叫用：

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

可預期下列輸出：

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a> 委派函式

*委派*的函式會在相同的類別中呼叫不同的函式，以執行一些初始化工作。 當您有多個必須執行類似工作的多個函式時，這非常有用。 您可以在一個函式中撰寫主要邏輯，並從其他函式叫用它。 在下列的簡單範例中，Box (int) 會將其工作委派給 Box (int，int，int) ：

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

在任何建構函式完成時，建構函式建立的物件會立即完全初始化。 如需詳細資訊，請參閱 [委派函數](../cpp/delegating-constructors.md)。

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a> (c + + 11) 繼承函數

衍生的類別可以使用宣告來繼承直接基類的函式， **`using`** 如下列範例所示：

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 和更新版本**： **`using`** **/std： c + + 17** 模式中的語句會從基類將所有的函式納入範圍中，除了對衍生類別中的函式具有相同簽章的函式。 一般而言，衍生類別未宣告新的資料成員或建構函式時，最好使用繼承建構函式。

::: moniker-end

如果類型引數指定基底類別，則類別樣板可以繼承該類型的所有建構函式：

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

如果多個基底類別的建構函式具有相同簽章，則衍生類別無法繼承自這些基底類別。

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a> 函數和複合類別

包含類別類型成員的類別稱為 *複合類別*。 在建立複合類別的類別類型成員時，會先呼叫建構函式，然後呼叫類別自己的建構函式。 當包含的類別缺少預設建構函式時，您必須在複合類別的建構函式中使用初始設定清單。 在先前的 `StorageBox` 範例中，如果將 `m_label` 成員變數的類型變更為新的 `Label` 類別，您必須呼叫基底類別建構函式和初始化 `m_label` 建構函式中的 `StorageBox` 變數：

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>本節內容

- [複製建構函式和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)
- [移動建構函式和移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)
- [委派建構函式](delegating-constructors.md)

## <a name="see-also"></a>另請參閱

[類別和結構](classes-and-structs-cpp.md)
