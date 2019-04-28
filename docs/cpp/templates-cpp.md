---
title: 樣板 (C++)
ms.date: 11/04/2016
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: f1532b5aa4ea712feab08b49b7c035187ca0d042
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330488"
---
# <a name="templates-c"></a>樣板 (C++)

範本是中的泛用程式設計的基礎C++。 作為強型別語言，C++必須要有特定的型別，明確宣告的程式設計人員或編譯器推算出的所有變數。 不過，許多資料結構和演算法看起來相同無論何種類型操作。 應處理範本，您定義類別或函式的作業，並讓使用者指定何種實體類型的作業。

## <a name="defining-and-using-templates"></a>定義和使用範本

範本是一種建構，在根據使用者所提供的範本參數的引數的編譯時期產生的一般型別或函式。 例如，您可以定義函式範本，如下：

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上述程式碼說明具有單一類型參數的泛型函式樣板*T*，其傳回值，並呼叫參數 （lhs 與 rhs） 全都是這個型別。 您可以類似，但依慣例單一大寫的字母您最常使用的任何項目名稱的型別參數。 *T*是範本參數，而**typename**關鍵字指出此參數類型的預留位置。 呼叫此函式時，編譯器將會取代每個執行個體`T`與所指定使用者或編譯器推算出的具象型別引數。 處理程序，編譯器會產生的類別，或從範本函式指*樣板具現化*;`minimum<int>`範本的具現化`minimum<T>`。

使用者可以在其他地方，宣告 int 特製化的範本執行的個體假設 get_a() 和 get_b() 會傳回整數的函式：

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

不過，因為這是函式樣板和編譯器可以推斷的型別`T`從引數並*b*，您可以如同一般函式呼叫它：

```cpp
int i = minimum(a, b);
```

當編譯器遇到的最後一個陳述式時，它會產生新的函式中的每個出現位置*T*範本中取代**int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

編譯器在函式樣板中所執行的類型推斷規則根據一般的函式的規則。 如需詳細資訊，請參閱 <<c0> [ 多載解析的函式樣板呼叫](../cpp/overload-resolution-of-function-template-calls.md)。

## <a id="type_parameters"></a> 型別參數

在 `minimum`範本，請注意，型別參數*T*未限定以任何方式之前，它會在函式呼叫參數中，新增 const 和參考限定詞。

類型參數的數目沒有實際限制。 以逗號分隔多個參數：

```cpp
template <typename T, typename U, typename V> class Foo{};
```

關鍵字**類別**相當於**typename**在此內容中。 您可以表示為前一個範例︰

```cpp
template <class T, class U, class V> class Foo{};
```

您可以使用省略符號運算子 （...），以定義採用任意數目的零個或多個類型參數的範本：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何內建或使用者定義型別可用來當做型別引數。 例如，使用 std:: vector 標準程式庫來儲存 int、 雙精度浮點數、 字串、 MyClass、 const MyClass *、 MyClass （& s)。 使用範本時的主要限制是型別引數必須支援會套用至型別參數的任何作業。 例如，如果我們呼叫最小值使用 MyClass，如此範例所示：

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

會產生編譯器錯誤，因為 MyClass 不提供的多載 < 運算子。

雖然您可以定義的範本，會強制執行這類限制，沒有任何特殊範本中所有的型別引數屬於相同的物件階層架構，固有需求。 您可以結合範本; 中的物件導向技術例如，您可以儲存衍生 * 在向量\<基底\*>。    請注意，引數必須是指標

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

向量和其他標準程式庫容器加諸的項目的基本需求`T`在於`T`複製指派和複製可建構。

## <a name="non-type-parameters"></a>非類型參數

不同於泛型類型以其他語言如C#和 Java 中，C++範本支援非類型參數，也稱為 「 值參數。 例如，您可以提供常數的整數值，以指定陣列的長度，如同此範例中是類似於標準程式庫中的 std:: array 類別：

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

請注意樣板宣告中的語法。 Size_t 值做為範本引數傳入在編譯時期，而且必須是常數或 constexpr 的運算式。 您可以使用它像這樣：

```cpp
MyArray<MyClass*, 10> arr;
```

其他類型的值包括指標和參考可以當做非類型參數傳遞。 比方說，您可以傳入指標的函式或函式物件，若要自訂的範本程式碼內某項作業。

## <a id="template_parameters"></a> 做為範本參數的範本

範本可以是範本參數。 在此範例中，MyClass2 有兩個範本參數： typename 參數*T*和 範本參數*Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

因為*Arr*參數本身有沒有主體時，不需要其參數的名稱。 事實上，它是錯誤，請參閱*Arr*的類型名稱或類別參數名稱從主體內`MyClass2`。 基於這個理由， *Arr*的型別參數名稱可以省略，在此範例中所示：

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>預設樣板引數

類別和函式樣板可以有預設引數。 當範本具有預設引數，您可以將它未指定當您使用。 比方說，std:: vector 範本有配置器的預設引數：

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大部分情況下預設 std:: allocator 類別是可接受的因此您可以使用像這樣的向量：

```cpp
vector<int> myInts;
```

但是如果需要您可以指定自訂的配置器如下所示：

```cpp
vector<int, MyAllocator> ints;
```

若有多個樣板引數，則第一個預設引數之後的所有引數都必須有預設引數。

其參數會將預設值的範本時，使用空括弧：

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

## <a name="template-specialization"></a>樣板特製化

在某些情況下，它不是辦法或不想要定義完全相同的程式碼的任何類型的範本。 比方說，您可能想要定義型別引數是指標或 std:: wstring，或從特定的基底類別衍生的類型時，才可以執行的程式碼路徑。  在此情況下，您可以定義*特製化*該特定類型的範本。 當使用者中，具現化的範本與該型別時，編譯器會使用特製化，以產生類別，並對於所有其他類型，編譯器會選擇更一般的範本。 特製化，特製化的所有參數都*完成特製化*。 如果只有某些參數進行特製化，它會呼叫*部分特製化*。

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

範本可以有任意數目的特製化，只要每個特製化的型別參數是唯一的。 只有類別樣板可以部分特製化。 所有完整和部分的特製化的範本必須與原始範本相同的命名空間中宣告。

如需詳細資訊，請參閱 <<c0> [ 樣板特製化](../cpp/template-specialization-cpp.md)。