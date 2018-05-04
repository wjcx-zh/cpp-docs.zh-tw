---
title: 簡單式 」、 標準配置，POD 和常值類型 |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 7a80db109df1d9aa25f471312a9ff7103b90df7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>簡單式 」、 標準配置，POD 和常值類型

詞彙*配置*指的是類別、 結構或等位型別物件的成員如何排列在記憶體中。 在某些情況下，配置是妥善定義的語言規格。 但是，當類別或結構包含特定的 c + + 語言功能，例如虛擬基底類別虛擬函式、 成員使用不同的存取控制，則編譯器可以自由選擇版面配置。 該配置會視正在執行哪些最佳化，在許多情況下物件可能不甚至所佔用的連續記憶體區域。 例如，如果類別有虛擬函式，該類別的所有執行個體可能會共用單一的虛擬函式表格。 這種類型的程序當然非常實用，但也有限制。 是未定義的配置，因為它們無法傳遞至以其他語言，C，例如撰寫的程式，您因為它們可能出現非連續它們無法可靠地複製使用快速低階函式例如`memcopy`或透過網路序列化。

 若要啟用編譯器，以及 c + + 程式和任何指定類型的適用性取決於特定記憶體配置的作業的原因 metaprograms，C + + 14 導入了簡單的類別和結構的三種： *trivial*，*標準配置*，和*POD*或一般舊資料。 標準程式庫有函式樣板`is_trivial<T>`，`is_standard_layout<T>`和`is_pod<T>`，以決定指定的型別是否屬於指定的類別。

## <a name="trivial-types"></a>Trivial 類型

 當類別或結構，在 c + + 中的有提供編譯器或明確預設特殊成員函式，則它是 trivial 類型。 會佔用連續記憶體區域。 它可以有不同的存取規範與成員。 C + + 編譯器可以自由選擇如何排序成員，在此情況下。 因此，您可以 memcopy 這類物件，但是您無法從 C 程式中，能夠可靠地使用它們。 Trivial 類型 T 可以複製到 char 或不帶正負號的 char 陣列，並安全地複製成 T 變數。 請注意，由於對齊需求，型別成員之間可能有填補位元組。

 Trivial 類型有 trivial 預設建構函式、 trivial 複製建構函式、 trivial 複製指派運算子和 trivial 解構函式。 在每個案例中， *trivial*表示不是使用者提供，而且屬於類別具有建構函式/運算子/解構函式

- 沒有虛擬函式或虛擬基底類別，

- 沒有與對應非一般建構函式/運算子/解構函式的基底類別

- 類別型別對應非一般建構函式/運算子/解構函式沒有任何資料成員

下列範例顯示簡單式型別。 中是否存在，Trivial2`Trivial2(int a, int b)`建構函式會要求您提供的預設建構函式。 為了限定為 trivial 類型，您必須明確預設的建構函式。

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

## <a name="standard-layout-types"></a>標準配置類型

 當類別或結構不含特定 c + + 語言功能，例如，在 C 語言中，找不到虛擬函式，而且所有成員都有相同的存取控制時，它會是標準配置類型。 Memcopy 可以和版面配置充分定義，它可由 C 程式。 標準配置類型可以有使用者定義的特殊成員函式。 此外，標準配置類型具有下列特性：

- 沒有虛擬函式或虛擬基底類別

- 所有非靜態資料成員具有相同的存取控制

- 類別類型的所有非靜態成員都是標準版面配置

- 任何基底類別是標準版面配置

- 具有第一個非靜態資料成員相同型別的任何基底類別。

- 符合下列情況之一：

  - 中最具衍生性的類別和一個以上的基底類別沒有非靜態資料成員和非靜態資料成員，或

  - 具有與非靜態資料成員沒有基底類別

下列程式碼會示範一種標準配置類型的其中一個範例：

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};

```

 最後兩個需求可能是可進一步說明以程式碼。 在下一個範例中，即使基底是標準配置`Derived`不標準配置，因為這兩個 it （最常衍生的類別） 和`Base`有非靜態資料成員：

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

 在此範例中`Derived`是標準配置因為`Base`沒有任何非靜態資料成員：

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

 衍生也會顯示為標準配置如果`Base`具有資料成員和`Derived`必須只有成員函式。

## <a name="pod-types"></a>POD 類型

 當類別或結構是 trivial 和標準配置時，它是 POD （一般舊資料） 類型。 因此連續 POD 類型的記憶體配置，以及每個成員具有較高的位址超出這些類型上，則可以執行，讓個位元組複製之前，宣告的成員和二進位 I/O。  純量類型，例如 int 也是 POD 類型。 POD 類型的類別可以有只有 POD 類型為非靜態資料成員。

## <a name="example"></a>範例

下列範例顯示簡單式 」、 的標準配置，差異和 POD 類型：

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