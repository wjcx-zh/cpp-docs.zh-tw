---
title: "樣板 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6ce40029e40906441ebd7c64ff9011a61f26045b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="templates-c"></a>樣板 (C++)
範本是 c + + 中的一般程式設計基礎。 為強型別語言，c + + 會需要有特定的類型，明確宣告的程式設計人員，或由編譯器所推斷的所有變數。 不過，許多資料結構與演算法一樣無論何種類型操作。 範本讓您定義類別或函式的作業，並讓使用者指定何種實體類型的作業應處理。  
  
## <a name="defining-and-using-templates"></a>定義和使用範本  
 範本是在編譯時期，根據使用者提供範本參數的引數所產生的一般型別或函式的建構。 例如，您可以定義函式樣板，像這樣：  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 上述程式碼說明具有單一類型參數的泛型函式範本`T`，其傳回值，並且呼叫參數 （lhs 與 rhs） 都此型別。 您可以類似，但由慣例單一大寫字母您最常使用的任何項目名稱的型別參數。 `T`是範本參數，`typename`關鍵字指出此參數類型的預留位置。 呼叫此函式時，編譯器將會取代每個執行個體`T`與使用者所指定，或由編譯器所推斷的具象型別引數。 處理序編譯器產生的類別或函式，從範本指*樣板具現化*;  `minimum<int>`範本的具現化`minimum<T>`。  
  
 使用者可以在其他地方，宣告針對 int 特製化的範本執行個體假設 get_a() 和 get_b() 是函式會傳回 int:  
  
```  
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 不過，因為這是函式樣板，而編譯器可以推算的類型`T`引數從`a`和`b`，您可以呼叫它，就像一般函式：  
  
```cpp  
int i = minimum(a, b);  
```  
  
 當編譯器遇到的最後一個陳述式時，它會產生新的函式中的每個出現的*T*範本中取代`int`:  
  
```  
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 編譯器在函式樣板中所執行的類型推算的規則根據一般函式的規則。 如需詳細資訊，請參閱[多載解析的函式樣板呼叫](../cpp/overload-resolution-of-function-template-calls.md)。  
  
## <a id="type_parameters"></a>型別參數  
 在`minimum`範本以上版本，請注意，型別參數`T`未限定以任何方式直到它使用於函式呼叫參數中，加入 const 和參考限定詞的位置。  
  
 類型參數的數目沒有實際限制。 請以逗號分隔多個參數：  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 關鍵字`class`相當於`typename`在此內容中。 你可以做為前一個範例：  
  
```  
template <class T, class U, class V> class Foo{};   
```  
  
 您可以使用省略符號運算子 （...），以定義採用任意數目的零或多個型別參數的範本：  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 任何內建或使用者定義型別可用來當做型別引數。 例如，使用 std:: vector 標準程式庫來儲存 int、 雙精度浮點數、 字串、 MyClass、 const MyClass *、 MyClass （& s)。 在使用樣板的主要限制是型別引數必須支援的型別參數所套用的任何作業。 例如，如果我們呼叫最少使用 MyClass，如此範例所示：  
  
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
  
 因為 MyClass 不提供的多載，將會產生編譯器錯誤 < 運算子。  
  
 雖然您可以定義會強制執行這類限制的範本，則所有的任何特定範本的類型引數屬於相同的物件階層架構中，沒有固有要求。 您可以結合範本; 中的物件導向技術例如，您可以儲存衍生 * 向量中\<基底\*>。    請注意，引數必須是指標  
  
```  
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 向量和其他標準程式庫容器加諸的項目的基本需求`T`在於`T`複製指派和複製建構這個類別。  
  
## <a name="non-type-parameters"></a>非類型參數  
 不同於 C# 和 Java 等其他語言中的泛型類型，c + + 範本可支援非型別參數，也稱為值參數。 例如，您可以提供常數的整數值，以指定陣列的長度，如同此範例，類似於標準的程式庫中的 std:: array 類別：  
  
```  
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 請注意樣板宣告中的語法。 Size_t 值作為範本引數傳入在編譯時期，且必須是常數或 constexpr 運算式。 您使用像這樣：  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 其他類型的值包括指標和參考可以當做非類型參數中傳遞。 比方說，您可以傳遞指標的函式或函式物件，以自訂的範本程式碼內的某些作業。  
  
## <a id="template_parameters"></a>做為範本參數的範本  
 範本可以是範本參數。 在此範例中，MyClass2 有兩個範本參數： typename 參數`T`和樣板參數`Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 因為`Arr`參數本身沒有內文，不需要用到它的參數名稱。 事實上，它是指將錯誤`Arr`的類型名稱或類別參數名稱從主體內`MyClass2`。 基於這個理由，`Arr`的型別參數名稱可以省略，在此範例所示：  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>預設範本引數  
 類別和函式樣板可以有預設引數。 當範本具有預設引數，您可以將它未指定當您使用。 例如，std:: vector 範本具有配置器的預設引數：  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 在大部分情況下預設 std::allocator 類別可接受的因此，您使用的向量，像這樣：  
  
```cpp  
vector<int> myInts;  
```  
  
 如果需要您可以指定自訂配置器，但以這種方式：  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 若有多個樣板引數，則第一個預設引數之後的所有引數都必須有預設引數。  
  
 當使用其參數的所有預設的範本，使用空的角括號：  
  
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
 在某些情況下，它並不可行或適合定義完全相同的程式碼的任何類型的範本。 例如，您可能想要定義型別引數為指標或 std:: wstring，或從特定的基底類別衍生的類型時，才要執行的程式碼路徑。  在這種情況下，您可以定義*特製化*該特定類型的範本。 當使用者與該類型產生的範本時，供編譯器用來產生類別的特製化，對於所有其他類型，編譯器會選擇更一般的範本。 所有的參數進行特製化的特製化會*完成特製化*。 如果只有某些參數特製化時，它會呼叫*部分特製化*。  
  
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
  
 範本可以有任意數目的特製化，只要每個特製化的類型參數是唯一的。   只有類別樣板可以部分特製化。 範本的所有的完整和部分特製化必須是原始範本相同的命名空間中宣告。  
  
 如需詳細資訊，請參閱[樣板特製化](../cpp/template-specialization-cpp.md)。
