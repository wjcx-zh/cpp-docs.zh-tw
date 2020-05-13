---
title: 建構函式 (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 4640bcf5f21bbe018a8744a6c5206bdd09509c98
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749653"
---
# <a name="constructors-c"></a>建構函式 (C++)

要自訂類別的初始化方式,或在建立類別物件時呼叫函數,請定義*建構函數*。 建構函式的名稱與類別的名稱相同，但沒有傳回值。 您可以根據需要定義盡可能多的重載構造函數,以便以各種方式自定義初始化。 通常,建構函數具有公共可存取性,以便類定義或繼承層次結構以外的代碼可以創建類的物件。 但是,您也可以聲明建構函數為**受保護**或**私有**。

建構函數可以選擇採用成員在 itit 清單中。 與構造函數正文中分配值相比,這是初始化類成員的更有效方法。 下面的示例顯示了具有三個`Box`重載構造函數的類。 最後兩個使用成員 initit 清單:

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

宣告類別的實體時,編譯器根據重載解析規則選擇要呼叫的建構函數:

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

- 建構函式可以宣告為**內聯**、[顯式](#explicit_constructors)、**友或**[共](#constexpr_constructors)。
- 建構函數可以初始化已聲明為**const、****易失性**或**共變性**的物件。 構造函數完成後,該物件將變為**同一**物件。
- 要在實現檔案中定義建構函數,請指定名稱,就像使用任何其他成員函數一樣: `Box::Box(){...}`.

## <a name="member-initializer-lists"></a><a name="member_init_list"></a>成員初始化程式清單

建構函數可以選擇具有成員初始化器列表,該列表在建構函數正文執行之前初始化類成員。 (請注意,成員初始化程式列表與類型[std::initializer_list\<T>](../standard-library/initializer-list-class.md)的*初始化程式清單*不是同一回事。

使用成員初始化程式清單比在建構函數正文中分配值更可取,因為它直接初始化了成員。 在下面的範例中顯示成員初始化器清單由冒號後的所有**識別符(參數)** 表示式組成:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

標識符必須引用類成員;但是,標識符必須引用一個類成員。它用參數的值初始化。 參數可以是建構函數參數之一、函數呼叫或[\<std::initializer_list T>](../standard-library/initializer-list-class.md)。

必須在成員初始化器清單中初始化引用類型的**const**成員和成員。

應在初始化器清單中調用參數化的基類構造函數,以確保在執行派生構造函數之前完全初始化基類。

## <a name="default-constructors"></a><a name="default_constructors"></a>預設建構函式

*預設建構函數*通常沒有參數,但它們可以具有具有預設值的參數。

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

默認構造函數是[特殊成員函數](special-member-functions.md)之一。 如果在類中沒有聲明構造函數,編譯器提供隱式**內聯**預設構造函數。

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

如果依賴於隱式預設構造函數,請確保初始化類定義中的成員,如上例所示。 如果沒有這些初始化程序,成員將取消初始化,並且Volume() 呼叫將生成垃圾值。 通常,即使不依賴於隱式預設構造函數,也可以以這種方式初始化成員是一種好的做法。

以將編譯器定義為[已刪除](#explicitly_defaulted_and_deleted_constructors)的 ,可以防止編譯器產生隱式預設建構函數:

```cpp
    // Default constructor
    Box() = delete;
```

如果任何類成員不是預設可建構的,編譯器生成的預設構造函數將定義為已刪除。 例如,類類型的所有成員及其類類型成員必須具有可訪問的預設構造函數和析構函數。 引用類型的所有資料成員以及**const**成員必須具有預設成員初始化程式。

當您呼叫編譯器產生的預設建構函數並嘗試使用括弧時,將發出警告:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

這是「最令人惱怒的語法解析」(Most Vexing Parse) 問題範例。 由於範例運算式可解譯為函式的宣告或做為預設建構函式的引動過程，而且由於 C++ 剖析器偏好宣告更勝於其他項目，因此運算式被視為函式宣告。 有關詳細資訊,請參閱[大多數維興分析](https://en.wikipedia.org/wiki/Most_vexing_parse)。

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

但是,您可以使用一組初始化器列表來初始化 Box 物件陣列:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

有關詳細資訊,請參閱[初始化器](initializers.md)。

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a>複製建構函式

*複製建構函數*通過從相同類型的物件複製成員值來初始化物件。 如果類成員都是簡單的類型(如標量值),編譯器生成的複製構造函數就足夠了,並且不需要定義自己的。 如果類需要更複雜的初始化,則需要實現自定義複製構造函數。 例如,如果類成員是指針,則需要定義一個複製構造函數來分配新記憶體並從另一個指向物件複製值。 編譯器生成的複製構造函數只需複製指標,以便新指標仍指向另一個指標的記憶體位置。

複製建構函數可能具有以下簽名之一:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

定義複製構造函數時,還應定義複製賦值運算符 (*)。 有關詳細資訊,請參閱[分配](assignment.md)和[複製建構函數和複製賦值運算符號](copy-constructors-and-copy-assignment-operators-cpp.md)。

以複製建構函數定義為已刪除,可以防止物件被複製:

```cpp
    Box (const Box& other) = delete;
```

試著複製物件會產生錯誤*C2280:嘗試參考已刪除的函數*。

## <a name="move-constructors"></a><a name="move_constructors"></a>移動建構函式

*移動建構函數*是一種特殊的成員函數,用於在不複製原始資料的情況下將現有物件數據的擁有權移動到新變數。 它採用 rvalue 引用作為其第一個參數,並且任何其他參數都必須具有預設值。 移動構造函數可以顯著提高程式在大型物件周圍傳遞時的效率。

```cpp
Box(Box&& other);
```

在某些情況下,編譯器會選擇移動構造函數,該物件正被即將銷毀且不再需要其資源的同一類型的另一個物件初始化。 下面的示例顯示一個案例,當移動構造函數選擇重載解析度時。 在調用`get_Box()`的構造函數中,返回的值是*x 值*(eXpiring 值)。 它不分配給任何變數,因此即將超出範圍。 為了提供此示例的動機,讓我們為 Box 提供表示其內容的大型字串向量。 移動構造函數不是複製向量及其字串,而是從過期值"box"中"竊取"它,以便向量現在屬於新物件。 調用`std::move`是所有所需的全部,因為兩個類`vector``string`和 類都實現自己的移動構造函數。

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

如果類未定義移動構造函數,則如果沒有使用者聲明的複製構造函數、複製賦值運算符、移動賦值運算符或析構函數,編譯器將生成隱式構造函數。 如果未定義顯式或隱式移動構造函數,則以其他方式使用行動構造函數的操作將改為使用複製構造函數。 如果類聲明移動構造函數或移動賦值運算符,則隱式聲明的複製構造函數定義為已刪除。

如果類類型的任何成員缺少析構函數,或者編譯器無法確定要用於移動操作的構造函數,則隱式聲明的移動構造函數定義為已刪除。

有關如何編寫非普通移動構造函數的詳細資訊,請參閱[移動構造函數和移動賦值運算符 (C++)。](../cpp/move-constructors-and-move-assignment-operators-cpp.md)

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a>明確預設與移除建構函式

您可以顯式*預設*複製建構函數、預設構造函數、移動構造函數、複製賦值運算符、移動賦值運算符和析構函數。 您可以顯示式*刪除*所有特殊成員函數。

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

有關詳細資訊,請參閱[顯式預設和刪除函數](../cpp/explicitly-defaulted-and-deleted-functions.md)。

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a>康特克斯普魯構造函數

如果[constexpr](constexpr-cpp.md)

- 它被聲明為預設,或者滿足[一般缺點函數](constexpr-cpp.md#constexpr_functions)的所有條件;
- 類沒有虛擬基類;
- 每個參數都是[一個文字類型](trivial-standard-layout-and-pod-types.md#literal_types);
- 身體不是功能嘗試塊;
- 所有非靜態數據成員和基類子物件都初始化;
- 如果類是 (a) 具有變體成員的工會,或者 (b) 具有匿名聯合,則只有一個工會成員被初始化;
- 類別類型的每個非靜態資料成員,並且所有基類子物件都有一個 constexpr 構造函數

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a>初始化器清單建構函式

如果構造函數以[\<std::initializer_list\>T](../standard-library/initializer-list-class.md)作為其參數,並且任何其他參數具有預設參數,則當通過直接初始化實例化類時,將以重載解析度選擇該構造函數。 您可以使用initializer_list初始化任何可以接受它的成員。 例如,假設 Box 類別(前面顯示`std::vector<string>`)`m_contents`有成員 。 您可以提供以下的構構函數:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

然後建立以下的 Box 物件:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a>明確建構函數

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

在某些情況下，這類轉換十分有用，但它們可能更常導致您程式碼中的細微但嚴重的錯誤。 通常,應在建構函數(和使用者定義的運算子)上使用**顯式**關鍵字來防止此類隱式類型轉換:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

建構函式是明確建構函式時，此行會造成編譯器錯誤：`ShippingOrder so(42, 10.8);`。  有關詳細資訊,請參閱[使用者定義的類型轉換](../cpp/user-defined-type-conversions-cpp.md)。

## <a name="order-of-construction"></a><a name="order_of_construction"></a>施工順序

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

衍生類別建構函式一定會呼叫基底類別建構函式，因此，它可以依賴完全建構的基底類別，才進行任何額外的工作。 根據派生的順序調用`ClassA`基類構造函數, 例如,如果派生自`ClassB`派生`ClassC`於 ,則先調用`ClassC`構造 函`ClassB`數,`ClassA`然後是構造 函數,然後是構造函數。

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

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a>衍生函數和擴充聚合初始化

如果基類的構造函數是非公共的,但派生類可以訪問,那麼在 Visual Studio 2017 和更高版本中的 **/std:c++17**模式下,不能使用空大括弧初始化派生類型的物件。

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

以下範例顯示了 visual Studio 2017 中C++17的行為,以及**隨後在 /std:c++17**模式下的行為:

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>具有多個繼承的類別建構函數

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

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a>委派建構函數

*委派構造函數*調用同一類中的不同構造函數來執行一些初始化工作。 當您有多個構造函數必須執行類似的工作時,這非常有用。 您可以在一個構造函數中編寫主邏輯,並從其他構造函數中調用它。 在下面的瑣碎示例中,Box(int) 將其工作委託給 Box(int、int、int):

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

在任何建構函式完成時，建構函式建立的物件會立即完全初始化。 有關詳細資訊,請參閱[委派構造函數](../cpp/delegating-constructors.md)。

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a>繼承建構函數 (C++11)

派生類可以使用**using**聲明從直接基類繼承構造函數,如以下範例所示:

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

**Visual Studio 2017 及更高版本**:**在 /std:c++17**模式下**使用**語句將基類中的所有構造函數(與派生類中的建構函數具有相同簽名的構造函數除外)引入範圍。 一般而言，衍生類別未宣告新的資料成員或建構函式時，最好使用繼承建構函式。 另請參閱[Visual Studio 2017 版本 15.7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157)中的改進。

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

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a>建構函數和複合類

包含類別型態成員的類別稱為*複合類*。 在建立複合類別的類別類型成員時，會先呼叫建構函式，然後呼叫類別自己的建構函式。 當包含的類別缺少預設建構函式時，您必須在複合類別的建構函式中使用初始設定清單。 在先前的 `StorageBox` 範例中，如果將 `m_label` 成員變數的類型變更為新的 `Label` 類別，您必須呼叫基底類別建構函式和初始化 `m_label` 建構函式中的 `StorageBox` 變數：

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

- [複製建構函式和複製分配運算子](copy-constructors-and-copy-assignment-operators-cpp.md)
- [移動建構函數和行動賦值運算子](move-constructors-and-move-assignment-operators-cpp.md)
- [委派建構函式](delegating-constructors.md)

## <a name="see-also"></a>另請參閱

[類別和結構](classes-and-structs-cpp.md)
