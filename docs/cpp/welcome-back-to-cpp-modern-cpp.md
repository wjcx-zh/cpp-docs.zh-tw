---
title: 歡迎回到C++ -現代化C++
description: 說明現代化C++的新程式設計慣用語，以及其原理。
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 9630322024e639f9e5db1888dac5a1530befc716
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869717"
---
# <a name="welcome-back-to-c---modern-c"></a>歡迎回到C++ -現代化C++

建立後， C++已成為世界上最廣泛使用的程式設計語言之一。 編寫完善的 C++ 程式不但執行快速，而且有效率。 此語言比其他語言更有彈性：它可以在最高層級的抽象層中工作，並在晶片的層級向下。 C++提供高度優化的標準程式庫。 它可讓您存取低層級的硬體功能，以最大化速度並將記憶體需求降至最低。 使用C++，您可以建立各種不同的應用程式。 遊戲、設備磁碟機和高效能科學軟體。 內嵌程式。 Windows 用戶端應用程式。 即使是其他程式設計語言的程式庫和編譯器C++也是以撰寫的。

C++ 的其中一個原始需求是與 C 語言的回溯相容性。 因此， C++一律允許 C 樣式程式設計，包括原始指標、陣列、以 null 結束的字元字串，以及其他功能。 它們可能會啟用絕佳的效能，但也會產生錯誤和複雜度。 的演進C++具有強調的功能，可大幅減少使用 C 樣式慣用語的需求。 當您需要時，會有舊版的 C 程式設計工具，但使用C++現代化程式碼時，您應該會需要較少且較少的功能。 現代化C++的程式碼更簡單、更安全、更簡潔，而且速度也跟以往一樣快。

下列各節提供現代化C++主要功能的總覽。 除非另有說明，否則此處所列的功能會在 c + + 11 和更新版本中提供。 在 Microsoft C++編譯器中，您可以設定[/std](../build/reference/std-specify-language-standard-version.md)編譯器選項，以指定要用於專案的標準版本。

## <a name="resources-and-smart-pointers"></a>資源和智慧型指標

C 樣式程式設計中的其中一個主要錯誤類別就是*記憶體*流失。 遺漏的原因通常是因為無法針對使用**new**所配置的記憶體呼叫**delete** 。 現代化C++強調資源取得的原則*是初始化*（RAII）。 概念很簡單。 資源（堆積記憶體、檔案控制代碼、通訊端等等）應由物件*所擁有*。 該物件會在其程式中建立或接收新配置的資源，並在其析構函式中將它刪除。 RAII 的原則可保證當擁有物件超出範圍時，所有資源都會正確地傳回給作業系統。

為了支援輕鬆採用 RAII 原則C++ ，標準程式庫提供三種智慧型指標類型： [std：： unique_ptr](../standard-library/unique-ptr-class.md)、 [std：： shared_ptr](../standard-library/shared-ptr-class.md)和[std：： weak_ptr](../standard-library/weak-ptr-class.md)。 智慧型指標會處理所擁有之記憶體的配置和刪除。 下列範例顯示具有陣列成員的類別，該成員會在 `make_unique()`的呼叫中，于堆積上配置。 **New**和**delete**的呼叫是由 `unique_ptr` 類別所封裝。 當 `widget` 物件超出範圍時，將會叫用 unique_ptr 的析構函式，而且它會釋放為數組配置的記憶體。  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

請盡可能在配置堆積記憶體時使用智慧型指標。 如果您必須明確使用 new 和 delete 運算子，請遵循 RAII 的原則。 如需詳細資訊，請參閱[物件存留期和資源管理（RAII）](object-lifetime-and-resource-management-modern-cpp.md)。

## <a name="stdstring-and-stdstring_view"></a>std：： string 和 std：： string_view

C 樣式字串是 bug 的另一個主要來源。 藉由使用[std：： string 和 std：： wstring](../standard-library/basic-string-class.md)，您可以消除與 C 樣式字串相關聯的幾乎所有錯誤。 您也可以取得成員函式的優點，以便搜尋、附加、預先加上等等。 這兩者都是高度優化的速度。 將字串傳遞至只需要唯讀存取的函式時，在 c + + 17 中，您可以使用[std：： string_view](../standard-library/basic-string-view-class.md)以獲得更高的效能優勢。

## <a name="stdvector-and-other-standard-library-containers"></a>std：： vector 和其他標準程式庫容器

標準程式庫容器全都遵循 RAII 的原則。 它們提供反覆運算器以進行專案的安全遍歷。 而且，它們已針對效能進行高度優化，並已徹底測試正確性。 藉由使用這些容器，您可以消除自訂資料結構中可能引進的 bug 或效率不佳的可能性。 使用[向量](../standard-library/vector-class.md)做為中C++的連續容器，而不是原始陣列。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[map](../standard-library/map-class.md) （而非 `unordered_map`）做為預設的關聯容器。 針對退化和多重案例使用[set](../standard-library/set-class.md)、 [multimap](../standard-library/multimap-class.md)和[多重](../standard-library/multiset-class.md)集。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

當需要效能優化時，請考慮使用：

- 內嵌時的[陣列](../standard-library/array-class-stl.md)類型很重要，例如，做為類別成員。

- 未排序的關聯容器，例如[unordered_map](../standard-library/unordered-map-class.md)。 這些專案具有較低的每個元素額外負荷和持續時間查詢，但可能難以正確且有效率地使用。

- 已排序 `vector`。 如需詳細資訊，請參閱[演算法](../cpp/algorithms-modern-cpp.md)。

請勿使用 C 樣式陣列。 對於需要直接存取資料的舊版 Api，請改用存取子方法，例如 `f(vec.data(), vec.size());`。 如需容器的詳細資訊，請參閱[ C++標準程式庫容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>標準程式庫演算法

在假設您需要為您的程式撰寫自訂演算法之前，請先參閱C++標準程式庫[演算法](../standard-library/algorithm.md)。 標準程式庫包含許多常見作業（例如搜尋、排序、篩選和隨機化）的不斷成長演算法。 數學程式庫很廣泛。 從 c + + 17 開始，提供了許多演算法的平行版本。

以下是一些重要的範例：

- **for_each**，預設的遍歷演算法（以及以範圍為基礎的 for 迴圈）。

- **轉換**，適用于不就地修改的容器元素

- **find_if**，預設搜尋演算法。

- **排序**、 **lower_bound**和其他預設排序和搜尋演算法。

若要撰寫比較子，請使用 strict **<** ，並在可以時使用*已命名的 lambda* 。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto，而不是明確類型名稱

C + + 11 引進了[自動](auto-cpp.md)關鍵字，可用於變數、函式和樣板宣告。 [**自動**] 會告知編譯器推算物件的類型，因此您不需要明確地輸入它。 當推算的型別是嵌套範本時， **auto**特別有用：

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>以範圍為基礎的 for 迴圈

在陣列和容器上進行 C 樣式的反復專案很容易就能編制錯誤的索引，而且也很繁瑣。 若要消除這些錯誤，並讓您的程式碼更容易閱讀，請使用以範圍為基礎的 for 迴圈搭配標準程式庫容器和原始陣列。 如需詳細資訊，請參閱[以範圍為基礎的 for 語句](../cpp/range-based-for-statement-cpp.md)。

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>constexpr 運算式，而非宏

C 和C++中的宏是由預處理器在編譯之前處理的標記。 在編譯檔案之前，宏標記的每個實例都會被其定義的值或運算式取代。 宏通常用於 C 樣式的程式設計中，以定義編譯時間常數值。 不過，宏很容易出錯，而且很容易進行調試。 在現代化C++的情況下，您應該偏好使用適用于編譯時間常數的[constexpr](constexpr-cpp.md)變數：

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>統一初始化

在新式C++中，您可以針對任何類型使用括弧初始化。 初始化陣列、向量或其他容器時，這種形式的初始化特別方便。 在下列範例中，`v2` 會以 `S`的三個實例進行初始化。 `v3` 會使用使用大括弧初始化的三個 `S` 實例進行初始化。 編譯器會根據宣告的 `v3`類型，來推斷每個元素的類型。

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

如需詳細資訊，請參閱[括弧初始化](initializing-classes-and-structs-without-constructors-cpp.md)。

## <a name="move-semantics"></a>移動語義

新式C++提供*移動的語義*，讓您可以排除不必要的記憶體複本。 在舊版的語言中，在某些情況下無法避免複製。 *移動*作業會將資源的擁有權從一個物件轉移到下一個，而不需要建立複本。 在執行擁有資源的類別（例如堆積記憶體、檔案控制代碼等等）時，您可以為它定義*移動*函式和*移動指派運算子*。 在不需要複製的情況下，編譯器會在多載解析期間選擇這些特殊成員。 標準程式庫容器類型會在物件上叫用移動的函式（如果有定義的話）。 如需詳細資訊，請參閱[移動函數和移動指派C++運算子（）](move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="lambda-expressions"></a>Lambda 運算式

在 C 樣式程式設計中，函數可以使用函式*指標*傳遞至另一個函式。 函式指標不方便維護和瞭解。 它們所參考的函式可在原始程式碼中的其他位置定義，而遠離其叫用的時間點。 此外，它們不是型別安全。 新式C++提供函式*物件*、覆寫[（）](function-call-operator-parens.md)運算子的類別，讓它們可以像函式一樣呼叫。 建立函式物件最方便的方式是使用內嵌[lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。 下列範例示範如何使用 lambda 運算式來傳遞函式物件，`for_each` 函式會在向量的每個元素上叫用：

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Lambda 運算式 `[=](int i) { return i > x && i < y; }` 可以讀取為「函式，該函式會接受 `int` 類型的單一引數，並傳回布林值，指出引數是否大於 `x` 且小於 `y`。」 請注意，來自周圍內容的 `x` 和 `y` 變數可以在 lambda 中使用。 `[=]` 指定以傳值方式來*捕獲*這些變數;換句話說，lambda 運算式有自己的這些值複本。

## <a name="exceptions"></a>例外狀況

新式C++強調例外狀況，而不是錯誤碼，做為報告和處理錯誤情況的最佳方式。 如需詳細資訊，請參閱[例外狀況和錯誤處理的新式C++最佳作法](errors-and-exception-handling-modern-cpp.md)。

## <a name="stdatomic"></a>std：：不可部分完成

針對執行緒C++間的通訊機制，請使用標準程式庫[std：：](../standard-library/atomic-structure.md)不可部分完成結構和相關類型。

## <a name="stdvariant-c17"></a>std：： variant （c + + 17）

等位通常用於 C 樣式的程式設計中，藉由讓不同類型的成員佔用相同的記憶體位置來節省記憶體。 不過，等位不是型別安全，而且很容易發生程式設計錯誤。 C + + 17 引進了[std：： variant](../standard-library/variant-class.md)類別，做為等位的更強大且安全的替代方式。 [Std：：造訪](../standard-library/variant-functions.md#visit)函式可以用型別安全的方式，用來存取 `variant` 型別的成員。

## <a name="see-also"></a>請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)\
[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)\
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++語言一致性資料表](../overview/visual-cpp-language-conformance.md)
