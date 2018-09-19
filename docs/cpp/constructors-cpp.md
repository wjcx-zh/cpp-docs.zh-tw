---
title: 建構函式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08200320e30816ac45e6c91a14dc41508430cfae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069114"
---
# <a name="constructors-c"></a>建構函式 (C++)

若要自訂類別成員初始化的方式，或您類別的物件建立時叫用函式，定義*建構函式*。 建構函式的名稱與類別的名稱相同，但沒有傳回值。 您可以定義多個多載建構函式視需要自訂初始設定，以各種方式。 一般而言，建構函式具有公用存取範圍，以便在類別定義或繼承階層架構之外的程式碼可建立類別的物件。 但您也可以宣告為建構函式**保護**或是**私人**。

建構函式 （選擇性） 可以採用成員初始化清單。 這是更有效率的方式，來初始化類別成員，與指派建構函式主體中的值。 下列範例示範類別`Box`具有三個多載建構函式。 這兩個使用 init 成員清單：

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
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

當您宣告類別的執行個體時，編譯器會選擇要叫用的建構函式為基礎的多載解析規則：

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

- 建構函式可以宣告為**內嵌**，[明確](#explicit_constructors)， **friend**或是[constexpr](#constexpr_constructors)。
- 建構函式可以初始化已經宣告為物件**const**， **volatile**或是**const volatile**。 物件會變成**const**建構函式完成之後。
- 若要在實作檔中定義的建構函式，提供限定的名稱就如同任何其他成員函式： `Box::Box(){...}`。

## <a name="member_init_list"></a> 成員初始設定式清單

建構函式可以選擇性地有成員初始設定式清單，用來初始化建構函式主體執行前的類別成員。 (請注意，成員初始設定式清單不一樣*初始設定式清單*型別的[std:: initializer_list\<T >](../standard-library/initializer-list-class.md)。)

使用成員初始設定式清單是偏好透過指派建構函式主體中的值，因為它會直接初始化的成員。 在下列範例中顯示的成員初始設定式清單包含所有**identifier(argument)** 冒號後面的運算式：

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

識別碼必須參考類別成員;它會使用引數的值進行初始化。 引數可以是其中一個建構函式參數，而函式呼叫或[std:: initializer_list\<T >](../standard-library/initializer-list-class.md)。

**const**成員初始設定式清單中，則必須初始化成員和成員的參考型別。

呼叫參數化的基底類別建構函式應該進行初始設定式清單中，以確保衍生的建構函式的執行前，已完全初始化基底類別。

## <a name="default_constructors"></a> 預設建構函式

*預設建構函式*通常會有任何參數，但它們可以有預設值的參數。

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

預設建構函式是其中一種[特殊成員函式](special-member-functions.md)。 如果在類別中不宣告任何建構函式，編譯器會提供隱含**內嵌**預設建構函式。

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

如果您依賴的隱含預設建構函式時，務必初始化成員在類別定義中，在上述範例所示。 這些初始設定式中，成員會是未初始化而 Volume() 呼叫會產生記憶體回收的值。 一般情況下，最好來初始化成員，如此一來，即使不依賴隱含的預設建構函式。

您可以防止編譯器產生的隱含預設建構函式定義為[刪除](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;

```

為已刪除無法預設可建構的任何類別成員時，將會定義編譯器產生的預設建構函式。 例如，類別型別的所有成員和其類別類型成員，必須有預設建構函式和解構函式，可存取。 所有資料成員的參考都類型，也一樣**const**成員必須有預設成員初始設定式。

當您呼叫的編譯器產生的預設建構函式，並嘗試使用括號時，就會發出警告：

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

這是「最令人惱怒的語法解析」(Most Vexing Parse) 問題範例。 由於範例運算式可解譯為函式的宣告或做為預設建構函式的引動過程，而且由於 C++ 剖析器偏好宣告更勝於其他項目，因此運算式被視為函式宣告。 如需詳細資訊，請參閱 <<c0> [ 最繁瑣](http://en.wikipedia.org/wiki/Most_vexing_parse)。

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

不過，您可以使用一組初始設定式清單初始化物件的陣列：

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

如需詳細資訊，請參閱 <<c0> [ 初始設定式](initializers.md)。

## <a name="copy_and_move_constructors"></a> 複製建構函式

A*複製建構函式*從相同類型的物件複製的成員值來初始化物件。 如果您類別的成員全部的簡單類型，例如純量值，編譯器產生的複製建構函式就已足夠，您不需要定義您自己。 如果您的類別需要更複雜的初始化，您就必須實作自訂的複製建構函式。 比方說，如果類別成員是指標，然後您需要定義配置新的記憶體，並將值複製其他人的指向物件中的複製建構函式。 編譯器產生的複製建構函式只會複製指標，使新的指標仍然會指向對方的記憶體位置。

複製建構函式可能具有其中一個這些簽章：

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

當您定義的複製建構函式時，您也應該定義複製指派運算子 （=）。 如需詳細資訊，請參閱 <<c0> [ 指派](assignment.md)並[複製建構函式和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)。

您可以防止您的物件複製藉由定義為已刪除的複製建構函式：

```cpp
    Box (const Box& other) = delete;
```

嘗試複製該物件會產生錯誤*C2280： 嘗試參考已刪除的函式*。

## <a name="move_constructors"></a> 移動建構函式

A*移動建構函式*是將現有的物件資料的擁有權移至新的變數，而不複製原始資料的特殊成員函式。 它接受右值參考做為其第一個參數，而且任何其他參數必須有預設值。 移動建構函式傳遞大型物件時，可能會大幅增加您的程式效率。 移動建構函式接受右值參考做為其第一個參數。 任何其他參數都必須有預設值。

```cpp
Box(Box&& other);
```

編譯器會選擇移動建構函式在某些情況下，其中物件正在初始化另一個物件被終結，而且不再需要它的相同類型的資源。 下列範例會顯示一種情況時移動建構函式多載解析會選取。 變數* 方塊*傳回 get_Box() 是*xvalue* （即將過期的值） 也就是即將超出範圍。 若要提供此範例中的動機，讓方塊大向量表示其內容的字串。 而非複製向量和它的字串，移動建構函式 「 竊取 」 它從過期的值 「 方塊 」 以便向量現在屬於新的物件。 在呼叫`std::move`就有需要因為兩者`vector`和`string`類別會實作自己的移動建構函式。

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
    void Get_Contents()
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
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

如果類別未定義的移動建構函式，編譯器會產生隱含的其中一個，如果沒有任何使用者宣告複製建構函式、 複製指派運算子、 移動指派運算子或解構函式。 如果沒有明確或隱含的移動建構函式定義，否則會使用移動建構函式的作業會改為使用複製建構函式。 如果類別宣告移動建構函式或移動指派運算子，以隱含方式宣告的複製建構函式會定義為刪除。

隱含宣告的移動建構函式定義為刪除，如果是類別類型的任何成員沒有解構函式或編譯器無法判斷要用於移動作業的建構函式。

如需如何撰寫非 trivial 移動建構函式的詳細資訊，請參閱[移動建構函式和移動指派運算子 （c + +）](../cpp/move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="explicitly_defaulted_and_deleted_constructors"></a> 明確預設和已刪除的建構函式

您可以明確地*預設*複製建構函式、 預設建構函式、 移動建構函式、 複製指派運算子、 移動指派運算子和解構函式。 您可以明確地*刪除*所有特殊成員函式。

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

如需詳細資訊，請參閱 <<c0> [ 明確預設和刪除函式](../cpp/explicitly-defaulted-and-deleted-functions.md)。

## <a name="constexpr_constructors"></a> constexpr 建構函式

建構函式可以宣告為[constexpr](constexpr-cpp.md)如果

- 它是其中一個宣告為預設值，否則它符合所有的條件[constexpr 函式](constexpr-cpp.md#constexpr_functions)一般而言;
- 此類別具有虛擬基底類別;
- 每個參數是[常值型別](trivial-standard-layout-and-pod-types.md#literal_types);
- 主體不是函式 try 區塊;
- 所有非靜態資料成員和基底類別的子物件會初始化;
- 如果類別是具有 variant 的成員，（a) 等位，或 （b） 具有匿名等位，會將其中一個等位成員初始化;
- 類別類型的每個非靜態資料成員和所有基底類別的子物件具有的 constexpr 建構函式

## <a name="init_list_constructors"></a> 初始設定式清單建構函式

如果建構函式接受[std:: initializer_list\<T\> ](../standard-library/initializer-list-class.md)多載解析會選取其參數，以及任何其他參數有預設引數，因為該建構函式，類別為透過直接初始化具現化。 您可以使用 initializer_list 來初始化可接受的任何成員。 例如，假設 （如上所示） 方塊類別具有`std::vector<string>`成員`m_contents`。 您可以提供的建構函式，就像這樣：

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

然後再建立方塊物件，就像這樣：

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> 明確建構函式

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

在某些情況下，這類轉換十分有用，但它們可能更常導致您程式碼中的細微但嚴重的錯誤。 一般而言，您應該使用**明確**關鍵字的建構函式 （和使用者定義運算子） 以避免這種隱含類型轉換：

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

建構函式是明確建構函式時，此行會造成編譯器錯誤：`ShippingOrder so(42, 10.8);`。  如需詳細資訊，請參閱 <<c0> [ 使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)。

## <a name="order_of_construction"></a> 建構順序

建構函式會依此順序執行其工作：

1. 它會依宣告順序呼叫基底類別和成員建構函式。

2. 如果類別是從虛擬基底類別衍生，它會初始化物件的虛擬基底指標。

3. 如果類別具有或繼承虛擬函式，它會初始化物件的虛擬函式指標。 虛擬函式指標指向類別的虛擬函式表，以便讓虛擬函式呼叫正確繫結至程式碼。

4. 它會執行其函式主體內的任何程式碼。

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

衍生類別建構函式一定會呼叫基底類別建構函式，因此，它可以依賴完全建構的基底類別，才進行任何額外的工作。 基底類別建構函式會呼叫衍生的順序 — 比方說，如果`ClassA`衍生自`ClassB`，其係衍生自`ClassC`，則`ClassC`首先，呼叫建構函式則`ClassB`建構函式，則`ClassA`建構函式。

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>具有多重繼承的類別建構函式

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

## <a name="virtual_functions_in_constructors"></a> 建構函式中的虛擬函式

建議您呼叫建構函式中的虛擬函式時要小心。 因為基底類別建構函式一定是在衍生類別建構函式之前叫用，所以在基底建構函式中所呼叫的函式是基底類別版本，而非衍生類別版本。 在下列範例中，建構 `DerivedClass` 會導致 `BaseClass` 的 `print_it()` 實作先執行，然後 `DerivedClass` 建構函式才會導致 `DerivedClass` 的 `print_it()` 實作執行：

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

輸出如下：

```Output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> 委派建構函式

A*委派建構函式*呼叫其他建構函式中相同的類別來執行某些初始化工作。 當您有多個全部都必須執行類似工作的建構函式時，這非常有用。 您可以撰寫一個建構函式中的主要邏輯，並從其他項目叫用它。 在下列的簡單範例中，Box(int) 會委派至 Box(int,int,int) 其工作：

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```


在任何建構函式完成時，建構函式建立的物件會立即完全初始化。 如需詳細資訊，請參閱 <<c0> [ 統一初始設定和委派建構函式](../cpp/uniform-initialization-and-delegating-constructors.md)。

## <a name="inheriting_constructors"></a> 繼承建構函式 (C + + 11)

在衍生的類別可以繼承從直接基底類別建構函式利用**使用**宣告，如下列範例所示：

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

**Visual Studio 2017 15.7 版及更新版本**:**使用**中的陳述式 **/std: c + + 17**模式帶入範圍中所有的建構函式，除了具有相同的簽章的基底類別在衍生類別中的建構函式。 一般而言，衍生類別未宣告新的資料成員或建構函式時，最好使用繼承建構函式。 另請參閱[改良 Visual Studio 2017 15.7 版中的](../cpp-conformance-improvements-2017.md#improvements_157)。

如果型別引數指定基底類別，則類別樣板可以繼承該類型的所有建構函式：

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

如果多個基底類別的建構函式具有相同簽章，則衍生類別無法繼承自這些基底類別。

## <a name="constructors_in_composite_classes"></a> 建構函式和複合類別

包含類別類型成員的類別稱為*複合類別*。 在建立複合類別的類別類型成員時，會先呼叫建構函式，然後呼叫類別自己的建構函式。 當包含的類別缺少預設建構函式時，您必須在複合類別的建構函式中使用初始設定清單。 在先前的 `StorageBox` 範例中，如果將 `m_label` 成員變數的類型變更為新的 `Label` 類別，您必須呼叫基底類別建構函式和初始化 `m_label` 建構函式中的 `StorageBox` 變數：

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
