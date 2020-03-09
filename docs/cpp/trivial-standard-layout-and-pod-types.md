---
title: Trivial、標準配置、POD 與常值類型
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 2745302b3ebd7927e9d839e4661e884a2bd91042
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865769"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial、標準配置、POD 與常值類型

「配置」這個字詞，指的是類別、結構或等位型別的物件成員，在記憶體中如何安排。 在某些情況下，語言規格會完善地定義配置。 但是當類別或結構包含某些 C++ 語言特徵標記時 (例如虛擬基底類別、虛擬函式、存取控制不同的成員)，編譯器就可以自由選擇配置。 配置可能取決於執行的最佳化而有不同，在許多情況下，物件甚至可能不會佔用記憶體的連續區域。 例如，如果某個類別有虛擬函式，該類別的所有執行個體就可能共用單一虛擬函式表。 這樣的類型非常實用，但也有其限制。 由於配置未經定義，因此無法傳遞到以其他語言 (例如 C) 寫成的程式，而且也因為配置可能是不連續的，而無法透過快速的低階函式 (例如 `memcopy`) 確實複製，或透過網路序列化。

為了讓編譯器及 C++ 程式和中繼程式能夠依據特定記憶體配置，對為了作業而提供的任何類型評估合適性，C++14 帶來了三種類別的簡單分類與結構：*trivial*、標準配置 和 *POD* (即 Plain Old Data)。 標準程式庫有函式範本 `is_trivial<T>`、`is_standard_layout<T>` 及 `is_pod<T>`，能判斷提供的類型是否屬於提供的分類。

## <a name="trivial-types"></a>Trivial 類型

當 C++ 中的類別或結構有編譯器提供或明確預設的特殊成員函式時，就是 Trivial 類型。 其佔有連續的記憶體區域。 其成員有不同的存取指定名稱。 在 C++ 中，編譯器可以自由選擇在此情況下如何為成員排序。 因此，您可對這類物件進行 memcopy，但無法確實從 C 程式加以取用。 Trivial 類型的 T 可以複製到 Char 或未簽署 Char 的陣列中，並可安全複製回 T 變數中。 請注意，基於對齊需求，類型成員之間可能會有填補的位元組。

Trivial 類型有 Trivial 預設建構函式、Trivial 複製建構函式、Trivial 複製指派運算子及 Trivial 解構函式。 在各個情況下，*Trivial* 分別表示建構函式/運算子/解構函式並非使用者提供的，而且所屬類別

- 沒有虛擬函式或虛擬基底類別，

- 沒有對應非 Trivial 建構函式/運算子/解構函式的基底類別

- 沒有對應非 Trivial 建構函式/運算子/解構函式的類別類型資料成員

下列範例顯示了 Trivial 類型。 在 Trivial2 中，您必須提供預設建構函式，`Trivial2(int a, int b)` 建構函式才會存在。 對於要符合 Trivial 資格的類型，您必須明確預設建構函式。

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Standard layout 類型

當某個類別或結構不包含某些 C++語言特徵標記 (例如在 C 語言中找不到的虛擬函式)，而且所有成員都有相同的存取控制時，即為標準配置類型。 這個類型可進行 memcopy，而且配置會經過充分定義，能夠供 C 程式取用。 標準配置類型可以有使用者定義的特殊成員函式。 此外，標準配置類型有以下特性：

- 沒有虛擬函式或虛擬基底類別

- 所有非靜態資料成員都有相同的存取控制

- 類別類型的所有非靜態資料成員均具有標準配置

- 任何基底類別均具有標準配置

- 第一個非靜態資料成員不會是相同類型的基底類別。

- 符合以下其中一個條件：

  - 衍生程度最高的類別中沒有非靜態資料成員，最多只有一個具非靜態資料成員的基底類別，或

  - 沒有具非靜態資料成員的基底類別

下列程式碼示範了其中一個標準配置類型的範例：

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

最後兩個需求以程式碼來說明可能較為合適。 在下一個範例中，即使 Base 具有標準配置，`Derived` 也不是標準配置，因為其 (衍生程度最高的類別) 與 `Base` 都有非靜態的資料成員：

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

在此範例中，因為 `Derived` 沒有非靜態的資料成員，所以 `Base` 具有標準配置：

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

如果 `Base` 有資料成員，而 `Derived` 只有成員函式，則 Derived 也會具有標準配置。

## <a name="pod-types"></a>POD 類型

當類別或結構同時為 Trivial 或標準配置時，即為 POD (Plain Old Data) 類型。 因此，POD 類型的記憶體配置會是連續的，而各個成員的位址高於在其之前宣告的成員，這樣一來，位元組複製的位元組和二進位 I/O 才可在這些類型執行。  純量類型 (例如 int) 也屬於 POD 類型。 若 POD 類型是類別，非靜態資料成員就只能是 POD 類型。

## <a name="example"></a>範例

下列範例示範了 Trivial、標準配置和 POD 類型的差異：

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal_types"></a> 常值類型

常值類型的配置可以在編譯時期決定。 以下是常值類型：

- void
- 純量類型
- 參考
- Void、純量類型或參考的陣列
- 具有 trivial 解構函式和一或多個非移動或複製建構函式之 constexpr 建構函式的類別。 此外，其所有的非靜態資料成員和基底類別必須是常值類型，且不會變動。

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)