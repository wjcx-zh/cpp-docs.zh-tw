---
title: 初始設定式
ms.date: 07/29/2019
description: 如何初始化中的C++類別、結構、陣列和基本類型。
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 2cc68f2384402ce1eb3ac06b414f597a6b3951f0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418430"
---
# <a name="initializers"></a>初始設定式

初始設定式指定變數的初始值。 您可以初始化下列內容中的變數：

- 變數的定義中：

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- 函式的其中一個參數：

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- 函式的傳回值：

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

初始設定式可能會有下列格式：

- 以括號刮住的運算式 (或逗號分隔的運算式清單)：

    ```cpp
    Point p1(1, 2);
    ```

- 運算式後面接著等號：

    ```cpp
    string s = "hello";
    ```

- 以大括號括住的初始設定式清單。 該清單可能是空的，也可能包含一組清單 (如下列範例所示)：

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>初始化的類型

初始化分為數種類型，可能會在程式執行的不同時期發生。 不同類型的初始化不會互斥，例如清單初始化可以觸發值初始化，而在其他情況下，則可觸發彙總初始化。

### <a name="zero-initialization"></a>零初始化

零初始化是將變數設為隱含轉換為類型的零值：

- 數值變數初始化為 0 (或 0.0、0.0000000000 等)。

- Char 變數會初始化為 `'\0'`。

- 指標會初始化為**nullptr**。

- 陣列、 [POD](../standard-library/is-pod-class.md)類別、結構和等位，其成員會初始化為零值。

零初始化在不同時期執行：

- 在程式啟動時，對象是具有靜態期間的所有具名變數。 之後可以再次初始化這些變數。

- 在初始化值期間，對象是純量類型和使用空括號初始化的 POD 類別類型。

- 只初始化其成員子集的陣列。

以下舉例說明零初始化：

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a>預設初始化

類別、結構和等位的預設初始化是使用預設建構函式的初始化。 預設的函式可以使用沒有初始化運算式或使用**new**關鍵字來呼叫：

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

如果類別、結構或等位沒有預設建構函式，則編譯器會發出錯誤。

定義純量變數時若未使用初始化運算式，則預設會初始化。 這些變數都具有不定值。

```cpp
int i1;
float f;
char c;
```

定義陣列時若未使用初始化運算式，則預設會初始化。 預設初始化陣列時，預設會初始化其成員，且其成員具有下列不定值 (如下列範例所示)：

```cpp
int int_arr[3];
```

如果陣列成員沒有預設建構函式，則編譯器會發出錯誤。

#### <a name="default-initialization-of-constant-variables"></a>常數變數的預設初始化

宣告常數變數時必須搭配使用初始設定式。 如果常數變數是純量類型，則會引發編譯器錯誤，如果是具有預設建構函式的類別類型，則會引發警告：

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>靜態變數的預設初始化

未使用初始設定式宣告的靜態變數會初始化為 0 (隱含地轉換為類型)。

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

如需全域靜態物件初始化的詳細資訊，請參閱[main 函數和命令列引數](main-function-command-line-args.md)。

### <a name="value-initialization"></a>值初始化

在下列情況下，會發生值初始化：

- 使用空大括號初始設定初始化具名的值。

- 使用空括號或大括號初始化匿名暫存物件。

- 使用**new**關鍵字加上空括弧或大括弧初始化物件

值初始化會執行下列作業：

- 對於至少有一個公用建構函式的類別，會呼叫預設建構函式。

- 對於沒有宣告建構函式的非等位類別，會將該物件初始化為零並呼叫預設建構函式。

- 對於陣列，會將每個元素初始化為值。

- 在所有其他情況下，會將變數初始化為零。

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>複製初始化

複製初始化是使用不同的物件初始化同一個物件。 在下列情況下，會發生這類初始化：

- 使用等號初始化變數

- 將引數傳遞至函式

- 從函式傳回物件

- 擲回或攔截例外狀況

- 使用等號初始化非靜態資料成員

- 複製初始化會在彙總初始化期間初始化類別、結構和等位成員。 如需範例，請參閱[匯總初始化](#agginit)。

下列程式碼示範數個複製初始化範例：

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

複製初始化無法叫用明確建構函式。

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

在某些情況下，若刪除或無法存取類別的複製建構函式，複製初始化會引發編譯器錯誤。

### <a name="direct-initialization"></a>直接初始化

直接初始化是使用 (非空白) 大括號或括號的初始化。 直接初始化可以叫用明確建構函式，這點與複製初始化不同。 在下列情況下，會發生這類初始化：

- 使用非空白大括號或括號初始化變數。

- 使用**new**關鍵字加上非空白大括弧或括弧初始化變數

- 使用**static_cast**初始化變數

- 在建構函式中，會使用初始設定式清單初始化基底類別和非靜態成員。

- 在 Lambda 運算式之所擷取變數的複本中。

下列程式碼示範一些直接初始化範例：

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>清單初始化

使用以大括號括住的初始設定式清單初始化變數時，會發生清單初始化。 在下列情況下，可以使用以大括號括住的初始設定式清單：

- 初始化變數

- 使用**new**關鍵字初始化類別

- 從函式傳回物件

- 將引數傳遞至函式

- 直接初始化中的其中一個引數

- 在非靜態資料成員初始設定式中

- 在建構函式初始設定式清單中

下列程式碼示範一些清單初始化範例：

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a>匯總初始化

彙總初始化是陣列或類別類型 (通常是結構或等位) 的清單初始化表單，這些陣列或類別類型具有：

- 非 private 成員或 protected 成員

- 沒有使用者提供的建構函式 (明確預設或已刪除的建構函式除外)

- 沒有基底類別

- 沒有虛擬成員函式

> [!NOTE]
> <!--conformance note-->在 Visual Studio 2015 和更早版本中，匯總不允許非靜態成員有大括弧或相等的初始化運算式。 這項限制已在 c + + 14 標準中移除，並在 Visual Studio 2017 中執行。

彙總初始設定式包含以大括號括住的初始化清單 (包含或不含等號) (如下列範例所示)：

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

您應該會看到下列輸出：

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> 在匯總初始化期間宣告但未明確初始化的陣列成員，會以零初始化，如同上述 `myArr3`。

#### <a name="initializing-unions-and-structs"></a>初始化等位和結構

如果等位沒有建構函式，則可以使用單一值 (或使用等位的另一個執行個體) 將它初始化。 該值用於初始化第一個非靜態欄位。 此初始化與結構初始化不同，後者會使用初始化設定式中的第一個值初始化第一個欄位、第二個值初始化第二個欄位，依此類推。 比較下列範例中的等位初始化和結構初始化：

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>初始化包含彙總的彙總

彙總類型可以包含其他彙總類型 (例如陣列、結構陣列等)。 這些類型均使用巢狀大括號集進行初始化，例如：

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>參考初始化

若要初始化參考類型的變數，必須使用衍生該參考類型之類型的物件，或者其類型可轉換成衍生該參考類型之類型的物件。 例如，

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

使用暫存物件初始化參考的唯一方式是初始化常數暫存物件。 初始化之後，參考類型變數一律會指向相同物件；不能將此變數修改為指向另一個物件。

雖然語法可能相同，但初始化參考類型變數和指派參考類型變數，在語意上是不同的。 在上述範例中，變更 `iVar` 和 `lVar` 的指派就初始化而言看似相似，但兩者的作用不同。 初始化會指定參考類型變數所指向的物件；指派則會透過參考指派被參考的物件。

由於將參考類型的引數傳遞至函式以及從函式傳回參考類型的值都是初始化，因此可以正確地初始化參考所傳回的函式型式引數。

只有在下列情況下，可以不使用初始設定式宣告參考類型變數：

- 函式宣告 (原型)。 例如，

    ```cpp
    int func( int& );
    ```

- 函式傳回類型宣告。 例如，

    ```cpp
    int& func( int& );
    ```

- 宣告函式類型類別成員。 例如，

    ```cpp
    class c {public:   int& i;};
    ```

- 明確指定為**extern**的變數宣告。 例如，

    ```cpp
    extern int& iVal;
    ```

初始化參考類型變數時，編譯器會使用下圖所示的決策圖，在建立物件參考或建立參考指向之暫存物件之間做選擇。

![初始化參考型別的決策圖表](../cpp/media/vc38s71.gif "初始化參考型別的決策圖表") <br/>
初始化參考型別的決策圖表

**Volatile**類型的參考（宣告為**volatile** *typename* <strong>&</strong> *identifier*）可以使用相同類型的**volatile**物件或尚未宣告為**volatile**的物件來初始化。 不過，它們無法使用該類型的**const**物件進行初始化。 同樣地， **const**類型的參考（宣告為**const** *typename* <strong>&</strong> *identifier*）可以使用相同類型的**const**物件進行初始化（或轉換成該類型的任何專案，或是未宣告為**const**的物件）。 不過，它們無法使用該類型的**volatile**物件進行初始化。

不是以**const**或**volatile**關鍵字限定的參考只能使用宣告為**const**或**volatile**的物件進行初始化。

### <a name="initialization-of-external-variables"></a>外部變數的初始化

自動、靜態和外部變數的宣告可以包含初始化運算式。 不過，只有在變數未宣告為**extern**時，外部變數的宣告才可包含初始化運算式。
