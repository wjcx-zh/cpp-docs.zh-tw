---
title: 樣板 (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032339"
---
# <a name="templates-c"></a>樣板 (C++)

範本是C++通用程式設計的基礎。 作為強類型語言,C++要求所有變數具有特定類型,要麼由程式師顯式聲明或由編譯器推斷。 但是,無論它們使用哪種類型,許多數據結構和演算法看起來都相同。 範本使您能夠定義類或函數的操作,並允許使用者指定這些操作應處理的具體類型。

## <a name="defining-and-using-templates"></a>定義與使用樣本

範本是一種構造,它基於使用者為範本參數提供的論點在編譯時生成普通類型或函數。 例如,您可以定義如下所示的函數範本:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上述代碼描述了具有單類型參數*T*的泛型函數的範本,其返回值和調用參數(lhs 和 rhs)都是此類。 您可以命名任何你喜歡的類型參數,但按照慣例,最常用的是單個大寫字母。 *T*是範本參數;**類型名稱**關鍵字表示此參數是類型的占位元。 調用函數時,編譯器將用使用者指定或編譯器推導`T`的混凝土類型參數替換 其每個實例。 編譯器從範本生成類或函數的過程稱為*範本實例化*;`minimum<int>`是範本`minimum<T>`的實例化。

在其他地方,用戶可以聲明專用於 int 的樣本實例。假定 get_a()和 get_b()是返回 int 的函數:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

但是,由於這是一個函數範本,編譯器可以從參數`T`*a*和*b*推斷其類型,因此可以像普通函數一樣調用它:

```cpp
int i = minimum(a, b);
```

當編譯器遇到最後一個語句時,它產生新函數,其中樣本中*T*的每一次發生都取代為**int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

編譯器如何在函數範本中執行類型演繹的規則基於普通函數的規則。 有關詳細資訊,請參閱[函數樣本呼叫的重載解析](../cpp/overload-resolution-of-function-template-calls.md)。

## <a name="type-parameters"></a><a id="type_parameters"></a>型態參數

在上面的`minimum`範本中,請注意,在函數調用參數中添加 const 和引用限定符之前,類型參數*T*不會以任何方式限定。

類型參數的數量沒有實際限制。 按逗號分隔多個參數:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

關鍵字**類別**等效於此上下文中**的類型命名**。 您可以將前面的範例表示為:

```cpp
template <class T, class U, class V> class Foo{};
```

可以使用橢圓運算子 (...) 定義具有任何數為零個或多個類型參數的樣本:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何內置類型或使用者定義類型都可以用作類型參數。 例如,您可以在標準庫中使用[std::vector](../standard-library/vector-class.md)來儲存**int**類型、**雙**[、std::字串](../standard-library/basic-string-class.md)`MyClass`**、const** `MyClass`*`MyClass&`等的變數。 使用範本時的主要限制是類型參數必須支援應用於類型參數的任何操作。 例如,如果我們調用`minimum`using,`MyClass`如在此範例中所示:

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

將生成編譯器錯誤,因為`MyClass`不為**<** 運算符提供重載。

沒有任何固有要求,即任何特定範本的類型參數都屬於同一物件層次結構,儘管您可以定義強制實施此類限制的範本。 您可以將面向對象的技術與範本相結合;例如,可以將派生* 存儲在向\<量\*庫>。    請注意,參數必須是指針

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector`和其他標準庫容器對的元素`T`施加的基本要求`T`是 可複製和可複製構造。

## <a name="non-type-parameters"></a>非類型參數

與其他語言(如 C# 和 Java)中的泛型類型不同,C++範本支援*非類型參數*,也稱為值參數。 例如,可以提供常量整數值來指定陣列的長度,如本示例類似於標準庫中的[std::array](../standard-library/array-class-stl.md)類:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

請注意範本聲明中的語法。 該`size_t`值在編譯時作為範本參數傳入,並且必須是**const**或**constexpr**運算式。 像這樣使用它:

```cpp
MyArray<MyClass*, 10> arr;
```

其他類型的值(包括指標和引用)可以作為非類型參數傳入。 例如,可以將指標傳遞到函數或函數物件以自定義範本代碼中的一些操作。

### <a name="type-deduction-for-non-type-template-parameters"></a>非類型樣本參數的類型扣除

在 Visual Studio 2017 及更高版本中,在 **/std:c++17**模式下,編譯器推匯出使用**auto**聲明的非類型範本參數的類型:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>樣本作為樣本參數

範本可以是範本參數。 這個樣本參數:MyClass2 有兩個樣本參數:類型名稱參數*T*與樣本參數*Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

由於*Arr*參數本身沒有正文,因此不需要其參數名稱。 事實上,從正文中引用*Arr*的類型名稱或類別參數名稱是`MyClass2`錯誤的 。 因此,可以省略*Arr*的類型參數名稱,如以下範例所示:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>預設樣本參數

類和函數範本可以具有預設參數。 當範本具有預設參數時,您可以在使用它時將其保留為未指定參數。 例如,std::vector 範本具有分配器的預設參數:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大多數情況下,預設 std::分配器類是可以接受的,因此您可以使用如下所示的向量:

```cpp
vector<int> myInts;
```

但是,如有必要,您可以指定如下所示的自定義分配器:

```cpp
vector<int, MyAllocator> ints;
```

若有多個樣板引數，則第一個預設引數之後的所有引數都必須有預設引數。

使用參數全部為預設的樣本時,請使用空角度括弧:

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>範本特製化

在某些情況下,範本不可能或不希望為任何類型的定義完全相同的代碼。 例如,您可能希望定義僅在類型參數是指針或 std::wstring 或派生自特定基類的類型時才能執行的代碼路徑。  在這種情況下,您可以為該特定類型定義樣本的*專門化*。 當使用者使用該類型實例化範本時,編譯器使用專門化生成類,對於所有其他類型,編譯器選擇更通用的範本。 所有參數都專用的專業化化是*完整的專業化化*。 如果只有某些參數是專門化的,則稱為*部分專業化化*。

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

只要每個專用類型參數是唯一的,範本就可以具有任意數量的專門化。 只有類範本可以部分專用。 範本的所有完整和部分專門化都必須在與原始範本相同的命名空間中聲明。

有關詳細資訊,請參閱[樣本專業化 。](../cpp/template-specialization-cpp.md)
