---
title: 樣板 (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 5f8322d850084ca53e946dcff1b67dc81b493fe3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160771"
---
# <a name="templates-c"></a>樣板 (C++)

範本是中C++一般程式設計的基礎。 身為強型別語言， C++會要求所有變數都有特定的型別，不論是由程式設計人員明確宣告或由編譯器推算。 不過，許多資料結構和演算法的外觀都相同，不論它們是在哪種類型上運作。 範本可讓您定義類別或函數的作業，並讓使用者指定這些作業應使用的具體類型。

## <a name="defining-and-using-templates"></a>定義和使用範本

範本是一種結構，它會在編譯時期根據使用者為範本參數所提供的引數來產生一般類型或函式。 例如，您可以定義如下的函數樣板：

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上述程式碼描述具有單一類型參數*T*之泛型函式的範本，其傳回值和呼叫參數（lhs 和 rhs）都是此類型。 您可以將類型參數命名為任何您喜歡的名稱，但依照慣例，最常使用單一大寫字母。 *T*是範本參數;**typename**關鍵字指出此參數是類型的預留位置。 呼叫函式時，編譯器會將每個 `T` 的實例取代為使用者所指定或由編譯器推算的具象類型引數。 編譯器從範本產生類別或函式的進程稱為樣板具現*化*;`minimum<int>` 是範本 `minimum<T>`的具現化。

在其他位置，使用者可以宣告專為 int 特殊化的範本實例。假設 get_a （）和 get_b （）是傳回 int 的函式：

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

不過，因為這是函式樣板，而編譯器可以從引數*a*和*b*推算 `T` 的類型，所以您可以像一般函式一樣呼叫它：

```cpp
int i = minimum(a, b);
```

當編譯器遇到最後一個語句時，它會產生新的函式，其中範本中每個出現的*T*都會取代為**int**：

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

編譯器在函式樣板中執行類型推斷的規則是以一般函數的規則為基礎。 如需詳細資訊，請參閱[函數樣板呼叫的](../cpp/overload-resolution-of-function-template-calls.md)多載解析。

## <a name="type-parameters"></a><a id="type_parameters"></a>型別參數

在上述的 `minimum` 範本中，請注意類型參數*t*不會以任何方式限定，直到在函式呼叫參數中使用為止，其中會加入 const 和 reference 限定詞。

型別參數的數目沒有實際的限制。 以逗號分隔多個參數：

```cpp
template <typename T, typename U, typename V> class Foo{};
```

關鍵字**類別**相當於此內容中的**typename** 。 您可以用下列方式表達先前的範例：

```cpp
template <class T, class U, class V> class Foo{};
```

您可以使用省略號運算子（...）來定義接受任意數目零或多個型別參數的範本：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何內建或使用者定義的類型都可以當做類型引數使用。 例如，您可以使用標準程式庫中的[std：： vector](../standard-library/vector-class.md)來儲存類型為**int**、 **double**、 [std：： string](../standard-library/basic-string-class.md)、`MyClass`、 **const** `MyClass`*、`MyClass&`等等的變數。 使用範本時的主要限制是，類型引數必須支援任何套用至類型參數的作業。 例如，如果我們使用 `MyClass` 來呼叫 `minimum`，如下列範例所示：

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

將會產生編譯器錯誤，因為 `MyClass` 未提供 **<** 運算子的多載。

任何特定範本的類型引數都屬於相同的物件階層，並不會有任何固有的需求，雖然您可以定義可強制執行這類限制的範本。 您可以結合物件導向技術與範本;例如，您可以將衍生的 * 儲存在向量中，\<基底\*>。    請注意，引數必須是指標

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector` 和其他標準程式庫容器在 `T` 的元素上所施加的基本需求，就是 `T` 是可指派和複製可建構。

## <a name="non-type-parameters"></a>非類型參數

不同于其他語言（例如C#和 JAVA）中的C++泛型型別，範本支援*非類型參數*，也稱為值參數。 例如，您可以提供常數整數值來指定陣列的長度，如同此範例，類似于標準程式庫中的[std：： array](../standard-library/array-class-stl.md)類別：

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

請注意範本宣告中的語法。 `size_t` 值會在編譯時期當做樣板引數傳入，而且必須是**const**或**constexpr**運算式。 您可以使用它，如下所示：

```cpp
MyArray<MyClass*, 10> arr;
```

其他類型的值（包括指標和參考）可以當做非型別參數傳入。 例如，您可以將指標傳入函數或函式物件，以自訂範本程式碼內的某些作業。

### <a name="type-deduction-for-non-type-template-parameters"></a>非類型樣板參數的類型推斷

在 Visual Studio 2017 和更新版本中，在 **/std： c + + 17**模式中，編譯器會會推算以**auto**宣告之非類型樣板引數的類型：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>範本做為範本參數

範本可以是範本參數。 在此範例中，MyClass2 有兩個範本參數： typename 參數*T*和樣板參數*Arr*：

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

因為*Arr*參數本身沒有主體，所以不需要其參數名稱。 事實上，從 `MyClass2`的主體中參考*Arr*的 typename 或類別參數名稱是錯誤的。 基於這個理由，可以省略*Arr*的類型參數名稱，如下列範例所示：

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>預設範本引數

類別和函式範本可以有預設引數。 當範本具有預設引數時，您可以在使用它時將它保留為未指定。 例如，std：： vector 範本具有配置器的預設引數：

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大多數情況下，預設的 std：：配置器類別是可接受的，因此您可以使用如下的向量：

```cpp
vector<int> myInts;
```

但如有需要，您可以指定自訂配置器，如下所示：

```cpp
vector<int, MyAllocator> ints;
```

若有多個樣板引數，則第一個預設引數之後的所有引數都必須有預設引數。

使用預設為所有參數的範本時，請使用空的角括弧：

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

在某些情況下，範本無法針對任何類型定義完全相同的程式碼，這是不可能或理想的做法。 例如，您可能想要定義只有在類型引數是指標、std：： wstring 或衍生自特定基類的類型時，才要執行的程式碼路徑。  在這種情況下，您可以針對該特定類型定義範本的特製*化*。 當使用者具現化具有該類型的範本時，編譯器會使用特製化來產生類別，而對於所有其他類型，編譯器會選擇較一般的範本。 所有參數都特殊化的特製化就是*完整特殊化*。 如果只有部分參數是特製化的，則稱為「*部分特殊化*」。

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

只要每個特殊化型別參數都是唯一的，範本可以有任意數目的特製化。 只有類別樣板可以部分特製化。 範本的所有完整和部分特製化都必須在與原始範本相同的命名空間中宣告。

如需詳細資訊，請參閱[範本特製化](../cpp/template-specialization-cpp.md)。
