---
title: "建構函式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建構函式 [C++]"
  - "執行個體建構函式"
  - "物件 [C++], 建立"
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建構函式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構函式是一種初始化其類別執行個體的成員函式。  建構函式的名稱與類別的名稱相同，但沒有傳回值。  建構函式可以有任意數目的參數，而類別可以有任意數目的多載建構函式。  建構函式可能有任何協助工具、公用、受保護或私用。  如果您未定義任何建構函式，則編譯器會產生不接受任何參數的預設建構函式；將預設建構函式宣告為已刪除，即可覆寫這個行為。  
  
## 本主題內容  
  
-   [建構順序](#order_of_construction)  
  
-   [成員清單](../cpp/constructors-cpp.md#member_lists)  
  
-   [明確建構函式](../cpp/constructors-cpp.md#explicit_constructors)  
  
-   [預設建構函式](../cpp/constructors-cpp.md#default_constructors)  
  
-   [複製和移動建構函式](../cpp/constructors-cpp.md#copy_and_move_constructors)  
  
-   [明確預設和刪除的建構函式](../cpp/constructors-cpp.md#explicitly_defaulted_and_deleted_constructors)  
  
-   [在衍生類別中的建構函式](../cpp/constructors-cpp.md#constructors_in_derived_classes)  
  
-   [具有多重繼承之類別的建構函式](../cpp/constructors-cpp.md#constructors_for_classes_that_have_multiple_inheritance)  
  
-   [在建構函式中的虛擬函式](../cpp/constructors-cpp.md#virtual_functions_in_constructors)  
  
-   [建構函式和複合類別](../cpp/constructors-cpp.md#constructors_in_composite_classes)  
  
-   [委派建構函式](../cpp/constructors-cpp.md#delegating_constructors)  
  
-   [繼承建構函式 (C++11)](../cpp/constructors-cpp.md#inheriting_constructors)  
  
-   [宣告建構函式的規則](../cpp/constructors-cpp.md#rules_for_declaring_constructors)  
  
-   預設和複製建構函式  
  
-   [明確叫用的建構函式](../cpp/constructors-cpp.md#explicitly_invoking_constructors)  
  
##  <a name="order_of_construction"></a> 建構順序  
 建構函式會依此順序執行其工作：  
  
1.  它會依宣告順序呼叫基底類別和成員建構函式。  
  
2.  如果類別是從虛擬基底類別衍生，它會初始化物件的虛擬基底指標。  
  
3.  如果類別具有或繼承虛擬函式，它會初始化物件的虛擬函式指標。  虛擬函式指標指向類別的虛擬函式表，以便讓虛擬函式呼叫正確繫結至程式碼。  
  
4.  它會執行其函式主體內的任何程式碼。  
  
 下列範例顯示在衍生類別的建構函式中呼叫基底類別和成員建構函式的順序。  首先會呼叫基底建構函式，然後依其出現在類別宣告中的順序初始化基底類別成員，最後會呼叫衍生的建構函式。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class Contained1 {  
public:  
    Contained1() {  
        cout << "Contained1 constructor." << endl;  
    }  
};  
  
class Contained2 {  
public:  
    Contained2() {  
        cout << "Contained2 constructor." << endl;  
    }  
};  
  
class Contained3 {  
public:  
    Contained3() {  
        cout << "Contained3 constructor." << endl;  
    }  
};  
  
class BaseContainer {  
public:  
    BaseContainer() {  
        cout << "BaseContainer constructor." << endl;  
    }  
private:  
    Contained1 c1;  
    Contained2 c2;  
};  
  
class DerivedContainer : public BaseContainer {  
public:  
    DerivedContainer() : BaseContainer() {  
        cout << "DerivedContainer constructor." << endl;  
    }  
private:  
    Contained3 c3;  
};  
  
int main() {  
    DerivedContainer dc;  
    int x = 3;  
}  
  
```  
  
 輸出如下：  
  
```  
Contained1 constructor.  
Contained2 constructor.  
BaseContainer constructor.  
Contained3 constructor.  
DerivedContainer constructor.  
```  
  
 如果建構函式擲回例外狀況，解構順序是建構順序的相反：  
  
1.  在建構函式主體中的程式碼會回溯。  
  
2.  基底類別和成員物件會依宣告的反向順序終結。  
  
3.  如果建構函式為非委派，所有完全建構的基底類別物件和成員都會終結。  不過，因為物件本身未完全建構，所以不會執行解構函式。  
  
##  <a name="member_lists"></a> 成員清單  
 使用成員初始設定式清單，以從建構函式引數初始化類別成員。  此方法使用*「直接初始化」*\(Direct Initialization\)，這比在建構函式主體內使用指派運算子更具效率。  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height) // member init list  
    {}  
    int Volume() {return m_width * m_length * m_height; }  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
```  
  
 建立 Box 物件：  
  
```  
Box b(42, 21, 12);  
cout << "The volume is " << b.Volume();  
```  
  
##  <a name="explicit_constructors"></a> 明確建構函式  
 如果類別的建構函式具有單一參數，或者，所有參數 \(但其中一個除外\) 都有預設值，則參數類型可以隱含地轉換為類別類型。  例如，如果 `Box` 類別具有建構函式，如下：  
  
```  
Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Box 可能初始化如下：  
  
```  
Box b = 42;  
```  
  
 或將 int 傳遞給採用 Box 的函式：  
  
```  
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
  
 在某些情況下，這類轉換十分有用，但它們可能更常導致您程式碼中的細微但嚴重的錯誤。  一般規則是您應該在建構函式 \(和使用者定義運算子\) 上使用 `explicit`，以防止這種隱含類型轉換：  
  
```  
  
explicit Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 建構函式是明確建構函式時，此行會造成編譯器錯誤：`ShippingOrder so(42, 10.8);`。  如需詳細資訊，請參閱[轉換](../cpp/user-defined-type-conversions-cpp.md)。  
  
##  <a name="default_constructors"></a> 預設建構函式  
 *「預設建構函式」*\(Default Constructor\) 沒有參數；它們遵循稍微不同的規則：  
  
 預設建構函式是其中一個*「特殊成員函式」*\(Special Member Function\)；如果在類別中未宣告建構函式，編譯器會提供預設建構函式：  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
  
int main(){  
  
    Box box1{}; // call compiler-generated default ctor  
    Box box2;   // call compiler-generated default ctor  
}  
```  
  
 當您呼叫預設建構函式和嘗試使用括號時，會發出警告：  
  
```cpp  
class myclass{};  
int main(){  
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)  
}  
```  
  
 這是「最令人惱怒的語法解析」\(Most Vexing Parse\) 問題範例。  由於範例運算式可解譯為函式的宣告或做為預設建構函式的引動過程，而且由於 C\+\+ 剖析器偏好宣告更勝於其他項目，因此運算式被視為函式宣告。  如需詳細資訊，請參閱[最繁瑣的語法解析](http://en.wikipedia.org/wiki/Most_vexing_parse) \(英文\)。  
  
 如果已宣告任何非預設建構函式，編譯器不會提供預設建構函式：  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
int main(){  
  
    Box box1(1, 2, 3);  
    Box box2{ 2, 3, 4 };  
    Box box4;     // compiler error C2512: no appropriate default constructor available  
}  
  
```  
  
 如果類別沒有預設建構函式，該類別的物件陣列無法透過單獨使用方括號語法來建構。  例如，根據上述程式碼區塊，Boxes 陣列無法宣告如下：  
  
```cpp  
Box boxes[3];    // compiler error C2512: no appropriate default constructor available  
  
```  
  
 不過，您可以使用初始設定式清單集合來初始化 Boxes 陣列：  
  
```cpp  
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };  
```  
  
##  <a name="copy_and_move_constructors"></a> 複製和移動建構函式  
 *「複製建構函式」*\(Copy Constructor\) 是一種特殊成員函式，採用相同類型之物件的參考做為輸入，並建立其複本。  如需詳細資訊，請參閱[複製建構函式和複製指派運算子 \(C\+\+\)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)。  移動也是特殊成員函式建構函式，會將現有物件的擁有權移至新的變數，而不複製原始資料。  如需詳細資訊，請參閱[移動建構函式和移動指派運算子 \(C\+\+\)](http://msdn.microsoft.com/zh-tw/1442de5f-37a5-42a1-83a6-ec9cfe0414db) 和[移動建構函式和移動指派運算子 \(C\+\+\)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)。  
  
##  <a name="explicitly_defaulted_and_deleted_constructors"></a> 明確預設和刪除的建構函式  
 您可以明確預設複製建構函式、預設建構函式、移動建構函式、複製指派運算子、移動指派運算子和解構函式。  您可以明確地刪除所有特殊成員函式。  如需詳細資訊，請參閱[明確的預設和被刪除的函式](../cpp/explicitly-defaulted-and-deleted-functions.md)。  
  
##  <a name="constructors_in_derived_classes"></a> 在衍生類別中的建構函式  
 衍生類別建構函式一定會呼叫基底類別建構函式，因此，它可以依賴完全建構的基底類別，才進行任何額外的工作。  基底類別建構函式是按照衍生的順序進行呼叫，例如，如果 ClassA 衍生自 ClassB，後者衍生自 ClassC，會先呼叫 ClassC 建構函式，然後呼叫 ClassB 建構函式，最後呼叫 ClassA 建構函式。  
  
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
  
### 具有多重繼承之類別的建構函式  
 如果類別從多個基底類別衍生，基底類別建構函式是依照其列在衍生類別宣告中的順序進行叫用：  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass1 {  
public:  
    BaseClass1() {  
        cout << "BaseClass1 constructor." << endl;  
    }  
};  
class BaseClass2 {  
public:  
    BaseClass2() {  
        cout << "BaseClass2 constructor." << endl;  
    }  
};  
class BaseClass3{  
public:  
    BaseClass3() {  
        cout << "BaseClass3 constructor." << endl;  
    }  
};  
class DerivedClass : public BaseClass1, public BaseClass2, public BaseClass3  {  
public:  
    DerivedClass() {  
        cout << "DerivedClass constructor." << endl;  
    }  
};  
  
int main() {  
    DerivedClass dc;  
}  
  
```  
  
 可預期下列輸出：  
  
```  
BaseClass1 constructor.  
BaseClass2 constructor.  
BaseClass3 constructor.  
DerivedClass constructor.  
```  
  
##  <a name="virtual_functions_in_constructors"></a> 在建構函式中的虛擬函式  
 建議您呼叫建構函式中的虛擬函式時要小心。  因為基底類別建構函式一定是在衍生類別建構函式之前叫用，所以在基底建構函式中所呼叫的函式是基底類別版本，而非衍生類別版本。  在下列範例中，建構 `DerivedClass` 會導致 `BaseClass` 的 `print_it()` 實作先執行，然後 `DerivedClass` 建構函式才會導致 `DerivedClass` 的 `print_it()` 實作執行：  
  
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
  
```  
BaseClass print_it  
Derived Class print_it  
```  
  
##  <a name="constructors_in_composite_classes"></a> 建構函式和複合類別  
 包含類別類型成員的類別稱為「*複合類別*」\(Composite Class\)。  在建立複合類別的類別類型成員時，會先呼叫建構函式，然後呼叫類別自己的建構函式。  當包含的類別缺少預設建構函式時，您必須在複合類別的建構函式中使用初始設定清單。  在先前的 `StorageBox` 範例中，如果將 `m_label` 成員變數的類型變更為新的 `Label` 類別，您必須呼叫基底類別建構函式和初始化 `m_label` 建構函式中的 `StorageBox` 變數：  
  
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
  
##  <a name="delegating_constructors"></a> 委派建構函式  
 「*委派建構函式*」\(Delegating Constructor\) 呼叫相同類別中的其他建構函式，以執行某些初始化工作。  在下列範例中，衍生類別有三個建構函式—第二個建構函式委派至第一個，而第三個建構函式委派至第二個：  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
    ConstructorDestructor dc(1, 2, 3);  
}  
  
```  
  
 輸出如下：  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor constructor with 3 ints.  
```  
  
 在任何建構函式完成時，建構函式建立的物件會立即完全初始化。  `DerivedContainer(int int1)` 成功，不過，`DerivedContainer(int int1, int int2)` 會失敗，並呼叫解構函式。  
  
```cpp  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
  
    try {  
        ConstructorDestructor cd{ 1, 2, 3 };  
    }  
    catch (const exception& ex){  
    }  
}  
  
```  
  
 輸出：  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor destructor.  
```  
  
 如需詳細資訊，請參閱[統一初始設定和委派建構函式](../cpp/uniform-initialization-and-delegating-constructors.md)。  
  
##  <a name="inheriting_constructors"></a> 繼承建構函式 \(C\+\+11\)  
 衍生類別可以使用 using 宣告以從直接基底類別繼承建構函式 \(如下列範例所示\)：  
  
```  
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
  
int main(int argc, char argv[])  
{  
    cout << "Derived d1(5) calls: ";   
    Derived d1(5);  
    cout << "Derived d1('c') calls: ";  
    Derived d2('c');  
    cout << "Derived d3 = d2 calls: " ;  
    Derived d3 = d2;  
    cout << "Derived d4 calls: ";  
    Derived d4;   
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    char in[1];  
    cin.getline(in, 1);  
    return 0;  
}  
  
/* Output:  
Derived d1(5) calls: Base(int)  
Derived d1('c') calls: Base(char)  
Derived d3 = d2 calls: Base(Base&)  
Derived d4 calls: Base()  
  
Press Enter to exit.  
  
```  
  
 using 陳述式會將基底類別的所有建構函式帶入範圍中，但衍生類別中具有建構函式之相同的簽章的建構函式除外。  一般而言，衍生類別未宣告新的資料成員或建構函式時，最好使用繼承建構函式。  
  
 如果類型引數指定基底類別，則類別樣板可以繼承該類型的所有建構函式：  
  
```  
template< typename T >  
class Derived : T {  
    using T::T;   // declare the constructors from T  
    // ...  
};  
  
```  
  
 如果多個基底類別的建構函式具有相同簽章，則衍生類別無法繼承自這些基底類別。  
  
##  <a name="rules_for_declaring_constructors"></a> 宣告建構函式的規則  
 建構函式的名稱與其類別的名稱相同。  您可以宣告任何數目的建構函式，但受限於多載函式的規則   \(如需詳細資訊，請參閱[多載](../misc/overloading-cpp.md)\)。  
  
 `argument-declaration-list` 可以是空的。  
  
 C\+\+ 定義了兩種特殊的建構函式，也就是預設和複製建構函式，如下表所述。  
  
### 預設和複製建構函式  
  
|建構的種類|引數|用途|  
|-----------|--------|--------|  
|預設建構函式|可以在不使用引數的情況下呼叫|建構類別類型的預設物件|  
|複製建構函式|可以接受相同類別類型之參考的單一引數|複製類別類型的物件|  
  
 預設建構函式可以在不使用引數的情況下呼叫。  不過，假設所有引數都有預設值，那麼您可以宣告具有引數清單的預設建構函式。  同樣地，複製建構函式必須接受相同類別類型之參考的單一引數。  假設所有後續引數都有預設值，則可以提供更多引數。  
  
 如果您未提供任何建構函式，則編譯器會嘗試產生預設建構函式。  如果您未提供複製建構函式，則編譯器會嘗試產生複製建構函式。  這些編譯器產生的建構函式會視為 public 成員函式。  如果您指定的複製建構函式中，第一個引數是物件而不是參考，則會產生錯誤。  
  
 編譯器產生的預設建構函式會設定物件 \(初始化 vftables 和 vbtables，如先前所述\)，而且它會呼叫基底類別和成員的預設建構函式，不過它不會採取其他動作。  基底類別和成員建構函式只有在存在、可存取且明確時才會呼叫。  
  
 編譯器產生的複製建構函式會設定新物件，並且執行所要複製之物件內容的成員複本。  如果基底類別或成員建構函式存在，則會呼叫它們，否則會執行位元複製。  
  
 如果 `type` 類別的所有基底和成員類別擁有的複製建構函式可接受 **const** 引數，則編譯器產生的複製建構函式會接受 **const** `type`**&** 類型的單一引數。  否則，編譯器產生的複製建構函式會接受 `type`**&** 類型的單一引數。  
  
 您可以使用建構函式初始化 **const** 或 `volatile` 物件，不過建構函式本身不能宣告為 **const** 或 `volatile`。  建構函式唯一的合法儲存類別是 **inline**，使用任何其他儲存類別修飾詞 \(包括 `__declspec` 關鍵字\) 搭配建構函式都會造成編譯器錯誤。  
  
 stdcall 呼叫慣例是在使用 **\_\_stdcall** 關鍵字宣告且不使用變數引數清單的靜態成員函式和全域函式上使用。  當您在非靜態成員函式 \(例如建構函式\) 上使用 **\_\_stdcall** 關鍵字時，編譯器將會使用 thiscall 呼叫慣例。  
  
 衍生類別不會繼承基底類別的建構函式。  建立衍生類別類型的物件時，會從基底類別元件開始建構，然後才是衍生類別元件。  編譯器會使用每個基底類別的建構函式 \(在完整物件的該部分初始化時，但虛擬衍生的情況除外，如[初始化基底類別](../misc/initializing-base-classes.md)中所述\)。  
  
##  <a name="explicitly_invoking_constructors"></a> 明確叫用的建構函式  
 建構函式可以在程式中明確呼叫，以建立指定類型的物件。  例如，若要建立兩個描述線條結尾的 `Point` 物件，可以撰寫以下程式碼：  
  
```  
DrawLine( Point( 13, 22 ), Point( 87, 91 ) );  
```  
  
 建立兩個 `Point` 類型的物件，傳遞至函式 `DrawLine`，然後在運算式 \(函式呼叫\) 結尾加以終結。  
  
 另一個明確呼叫建構函式的情況是在初始化期間：  
  
```  
Point pt = Point( 7, 11 );  
```  
  
 建立 `Point` 類型的物件，並使用接受 `int` 類型的兩個引數建構函式進行初始化。  
  
 透過明確呼叫建構函式建立的物件 \(如同在上述兩個範例中\) 皆未命名，且具有其所建立之運算式的存留期。  這部分會在[暫存物件](../cpp/temporary-objects.md)中詳細討論。  
  
 由於在執行使用者程式碼的第一行之前已經完全設定物件 \(已初始化虛擬資料表等等\)，因此通常可以放心在建構函式中呼叫任何成員函式。  不過，成員函式若在建構或解構期間呼叫抽象基底類別的虛擬成員函式，則可能不安全。  
  
 建構函式可以呼叫虛擬函式。  呼叫虛擬函式時，所叫用的函式是定義為該建構函式所屬類別 \(或繼承自其基底\) 的函式。  下列範例說明在建構函式中呼叫虛擬函式時所產生的影響：  
  
```  
// specl_calling_virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Base  
{  
public:  
    Base();             // Default constructor.  
    virtual void f();   // Virtual member function.  
};  
  
Base::Base()  
{  
    cout << "Constructing Base sub-object\n";  
    f();                // Call virtual member function  
}                       //  from inside constructor.  
  
void Base::f()  
{  
    cout << "Called Base::f()\n";  
}  
  
class Derived : public Base  
{  
public:  
    Derived();          // Default constructor.  
    void f();           // Implementation of virtual  
};                      //  function f for this class.  
  
Derived::Derived()  
{  
    cout << "Constructing Derived object\n";  
}  
  
void Derived::f()  
{  
    cout << "Called Derived::f()\n";  
}  
  
int main()  
{  
    Derived d;  
}  
```  
  
 執行上述程式時，`Derived d` 宣告會引發下列連續事件：  
  
1.  呼叫 `Derived` \(`Derived::Derived`\) 類別的建構函式。  
  
2.  輸入 `Derived` 類別建構函式的主體前，會呼叫 `Base` \(`Base::Base`\) 類別的建構函式。  
  
 `Base::Base` 會呼叫屬於虛擬函式的 `f` 函式。  通常會呼叫 `Derived::f` 是因為物件 `d` 的類型是 `Derived`。  因為 `Base::Base` 函式是建構函式，因此物件的類型還不是 `Derived`，而且會呼叫 `Base::f`。  
  
## 請參閱  
 [特殊成員函式](../misc/special-member-functions-cpp.md)