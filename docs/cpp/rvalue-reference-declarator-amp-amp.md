---
title: 右值參考宣告子：&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 65eec84447043b89ff94b77b7aed22b1b06f58e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227097"
---
# <a name="rvalue-reference-declarator-ampamp"></a>右值參考宣告子：&amp;&amp;

保留右值運算式的參考。

## <a name="syntax"></a>語法

```
type-id && cast-expression
```

## <a name="remarks"></a>備註

右值參考可讓您區分左值與右值。 左值參考和右值參考的語法和語意很相似，但是兩者遵循的規則稍有不同。 如需左值和右值的詳細資訊，請參閱[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。 如需左值參考的詳細資訊，請參閱左值參考宣告子[： &](../cpp/lvalue-reference-declarator-amp.md)。

下列各節描述右值參考如何支援*移動語義*和*完美轉送*的執行。

## <a name="move-semantics"></a>移動語意

右值參考支援*移動語義*的執行，這可能會大幅增加應用程式的效能。 移動語意可讓您撰寫將資源從一個物件轉移到另一個物件 (例如動態配置記憶體) 的程式碼。 移動語意可用於轉移暫存物件中無法供程式其他位置參考的資源，因此可以發揮功效。

若要執行移動語義，您通常會在您的類別中提供移動的函式 *，* 以及選擇性的移動指派運算子（**operator =**）。 然後，來源為右值的複製和指派作業會自動利用移動語意。 不同於預設複製建構函式，編譯器不提供預設移動建構函式。 如需如何撰寫移動函式，以及如何在應用程式中使用它的詳細資訊，請參閱[移動函數和移動指派運算子（c + +）](../cpp/move-constructors-and-move-assignment-operators-cpp.md)。

您也可以多載一般函式和運算子，以使用移動語意。 Visual Studio 2010 引進了將「移動」的語義加入 c + + 標準程式庫中。 例如，`string` 類別會實作執行移動語意的作業。 請考慮下列串連數個字串並列印結果的範例：

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

在 Visual Studio 2010 之前，每次呼叫**operator +** 會配置並傳回新的暫存 `string` 物件（右值）。 **運算子 +** 無法將一個字串附加至另一個，因為它不知道來源字串是左值或右值。 如果原始字串都是左值，程式中其他位置可能會參考它們，因此不得加以修改。 藉由使用右值參考，可以修改**operator +** 以接受右值，這在程式的其他位置無法參考。 因此， **operator +** 現在可以將一個字串附加至另一個。 這可以大幅減少 `string` 類別必須執行的動態記憶體配置數目。 如需類別的詳細資訊 `string` ，請參閱[basic_string 類別](../standard-library/basic-string-class.md)。

當編譯器無法使用傳回值最佳化 (RVO) 或具名傳回值最佳化 (NRVO) 時，移動語意也能有所幫助。 在這些情況下，如果類型定義了移動建構函式，則編譯器會加以呼叫。

若要進一步了解移動語意，請參考將項目插入至 `vector` 物件的範例。 如果超出 `vector` 物件的容量，`vector` 物件必須重新配置其項目的記憶體，然後將每個項目複製到另一個記憶體位置，以便為插入的項目騰出空間。 當插入作業複製項目時，會建立新的項目，呼叫複製建構函式複製上一個項目的資料到新項目，然後終結上一個項目。 移動語意可讓您直接移動物件，而不必執行耗費大量資源的記憶體配置和複製作業。

若要利用 `vector` 範例中的移動語意，您可以寫入移動建構函式，將資料從某個物件移動至另一個。

如需在 Visual Studio 2010 的 c + + 標準程式庫中引進 move 語義的詳細資訊，請參閱[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。

## <a name="perfect-forwarding"></a>完美轉送

完美轉送可減少對多載函式的需求，有助於避免轉送問題。 當您撰寫採用參考做為其參數的泛型函式，並將這些參數傳遞（或*轉送*）至另一個函式時，就會發生*轉送問題*。 例如，如果泛型函式採用 `const T&` 類型的參數，則呼叫的函式無法修改該參數的值。 如果泛型函式接受 `T&` 類型的參數，則無法使用右值 (例如暫存物件或整數常值) 呼叫函式。

若要解決這個問題，您通常必須提供每個參數採用 `T&` 和 `const T&` 的泛型函式多載版本。 因此，多載函式數目會隨著參數數目以指數方式增加。 右值參考可讓您撰寫接受任意引數並轉送至另一個函式的函式版本，就如同直接呼叫另一個函式。

請考慮宣告 `W`、`X`、`Y` 和 `Z` 這四種類型的下列範例。 每種類型的函式會採用 **`const`** 與非左值參考的不同組合 **`const`** 做為其參數。

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

假設您要撰寫產生物件的泛型函式。 下列範例示範撰寫此函式的其中一種方法：

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

下列範例示範對 `factory` 函式的有效呼叫：

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

不過，下列範例未包含對 `factory` 函式的有效呼叫，因為 `factory` 會接受可修改的左值參考做為其參數，但它是使用右值呼叫：

```cpp
Z* pz = factory<Z>(2, 2);
```

若要解決這個問題，您通常必須為每個 `factory` 與 `A&` 參數的組合建立 `const A&` 函式的多載版本。 右值參考可讓您撰寫 `factory` 函式的一個版本，如下列範例所示：

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

這個範例使用右值參考做為 `factory` 函式的參數。 [Std：： forward](../standard-library/utility-functions.md#forward)函式的目的是將 factory 函式的參數轉送至樣板類別的「處理」（function）。

下列範例示範 `main` 函式，這個函式會使用修改的 `factory` 函式來建立 `W`、`X`、`Y` 和 `Z` 類別的執行個體。 修改的 `factory` 函式會將其參數 (左值或右值) 轉送至適當的類別建構函式。

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>右值參考的其他屬性

**您可以多載函式以接受左值參考和右值參考。**

藉由多載函式來接受 **`const`** 左值參考或右值參考，您可以撰寫程式碼來區別不可修改的物件（左值）和可修改的暫存值（右值）。 除非物件標記為，否則您可以將物件傳遞至接受右值參考的函式 **`const`** 。 下列範例說明多載之後可接受左值參考和右值參考的 `f` 函式。 `main` 函式會使用左值和右值呼叫 `f`。

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

這個範例會產生下列輸出：

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

在此範例中，第一個對 `f` 的呼叫會傳遞區域變數 (左值) 做為其引數。 對 `f` 的第二個呼叫會傳遞暫存物件做為其引數。 由於程式中的其他位置無法參考暫存物件，呼叫會繫結至接受右值參考的 `f` 多載版本，此版本可以自由修改物件。

**編譯器會將具名右值參考視為左值，而將未具名右值參考當做右值。**

當您撰寫接受右值參考做為其參數的函式時，該參數會被視為函式主體中的左值。 由於程式的多個部分都可以參考具名物件，編譯器會將具名右值參考視為左值；因此，允許程式的多個部分從該物件修改或移除資源是相當危險的。 例如，如果程式中有多個部分嘗試從相同物件傳輸資源，則只有第一個部分會成功傳輸資源。

下列範例說明多載之後可接受左值參考和右值參考的 `g` 函式。 `f` 函式接受右值參考做為其參數 (具名右值參考)，並傳回右值參考 (未具名右值參考)。 從 `g` 對 `f` 的呼叫中，多載解析會選取採用左值參考的 `g` 版本，因為 `f` 主體會將其參數視為左值。 從 `g` 對 `main` 的呼叫中，多載解析會選取採用右值參考的 `g` 版本，因為 `f` 會傳回右值參考。

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

這個範例會產生下列輸出：

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

在這個範例中，`main` 函式將右值傳遞給 `f`。 `f` 主體會將其具名參數視為左值。 從 `f` 對 `g` 的呼叫會將參數繫結至左值參考 (`g` 的第一個多載版本)。

- **您可以將左值轉換成右值參考。**

C + + 標準程式庫[std：： move](../standard-library/utility-functions.md#move)函式可讓您將物件轉換成該物件的右值參考。 或者，您可以使用 **`static_cast`** 關鍵字將左值轉換為右值參考，如下列範例所示：

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

這個範例會產生下列輸出：

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**函式樣板會推算其樣板引數類型，然後使用參考摺疊規則。**

通常會撰寫函式範本，將其參數傳遞（或*轉寄*）至另一個函式。 請務必了解樣板類型推算對於接受右值參考之函式樣板的作用。

如果函式引數為右值，編譯器會推算引數為右值參考。 例如，如果您將 `X` 類型物件的右值參考傳遞至採用 `T&&` 類型做為其參數的樣板函式，則樣板引數推算會將 `T` 推算為 `X`。 因此，該參數會具有 `X&&` 類型。 如果函式引數為左值或 **`const`** 左值，則編譯器會將其類型會推算為該類型的左值參考或 **`const`** 左值參考。

下列範例宣告某個結構樣板，然後針對各種參考類型特製化此樣板。 `print_type_and_value` 函式接受右值參考做為其參數，並將其轉送給 `S::print` 方法的適當特製化版本。 `main` 函式示範各種呼叫 `S::print` 方法的方式。

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

這個範例會產生下列輸出：

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

為了解析對 `print_type_and_value` 函式的每個呼叫，編譯器會先執行樣板引數推算。 編譯器以推算出的樣板引數取代參數類型時，會接著套用參考摺疊規則。 例如，將區域變數 `s1` 傳遞至 `print_type_and_value` 函式會造成編譯器產生下列函式簽章：

```cpp
print_type_and_value<string&>(string& && t)
```

編譯器會使用參考摺疊規則，將簽章縮減如下：

```cpp
print_type_and_value<string&>(string& t)
```

`print_type_and_value` 函式的這個版本接著會將其參數轉送給 `S::print` 方法的正確特製化版本。

下表摘要說明樣板引數類型推算的參考摺疊規則：

|||
|-|-|
|展開的類型|摺疊的類型|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

樣板引數推算是實作完美轉送的要素。 本主題先前的＜完美轉送＞一節更詳細說明完美轉送。

## <a name="summary"></a>總結

右值參考會區分左值與右值。 它們可以消除不必要的記憶體配置和複製作業，因此能協助您改善應用程式效能。 此外，也可以讓您撰寫接受任意引數並轉送至另一個函式的函式版本，就如同直接呼叫另一個函式。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[移動建構函式和移動指派運算子 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
