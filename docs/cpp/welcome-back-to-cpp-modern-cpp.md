---
title: 歡迎回到 C++ (現代 C++)
description: 描述新式 c + + 中的新程式設計慣用語及其基本原理。
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 05c1fe80086e5b98d3f8a9c66c6759fddab39fa0
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353047"
---
# <a name="welcome-back-to-c---modern-c"></a>歡迎回到 C++ (現代 C++)

在建立之後，c + + 已經成為世界上最廣泛使用的程式設計語言之一。 編寫完善的 C++ 程式不但執行快速，而且有效率。 語言比其他語言更有彈性：它可以在最高層級的抽象層級運作，並在晶片的層級下運作。 C + + 提供高度優化的標準程式庫。 它可讓您存取低層級的硬體功能，以最快速度和將記憶體需求降至最低。 您可以使用 c + + 建立各式各樣的應用程式。 遊戲、設備磁碟機，以及高效能的科學軟體。 內嵌程式。 Windows 用戶端應用程式。 甚至其他程式設計語言的程式庫和編譯器都是以 c + + 撰寫。

C++ 的其中一個原始需求是與 C 語言的回溯相容性。 因此，c + + 一律允許 C 樣式的程式設計，以及原始指標、陣列、以 null 結束的字元字串，以及其他功能。 它們可能會啟用絕佳的效能，但也會產生 bug 和複雜度。 C + + 的演進具有強調的功能，可大幅減少使用 C 樣式慣用語的需求。 當您需要舊版的 C 程式設計工具時，您需要使用新式 c + + 程式碼。 新式 c + + 程式碼較簡單、更安全、更簡潔，而且仍會像以往一樣快速。

下列各節提供新式 c + + 主要功能的總覽。 除非另有說明，否則此處所列的功能可在 c + + 11 和更新版本中使用。 在 Microsoft c + + 編譯器中，您可以設定 [`/std`](../build/reference/std-specify-language-standard-version.md) 編譯器選項，以指定要用於專案的標準版本。

## <a name="resources-and-smart-pointers"></a>資源和智慧型指標

C 樣式程式設計中的其中一個主要 bug 類別是 *記憶體*流失。 遺漏的原因通常是因為無法呼叫配置 **`delete`** 給的記憶體 **`new`** 。 新式 c + + 強調資源取得的準則是 (RAII) 的 *初始化* 。 概念很簡單。 資源 (堆積記憶體、檔案控制代碼、通訊端等) 應該由物件 *擁有* 。 該物件會在其函式中建立或接收新配置的資源，並在其函式中將它刪除。 RAII 的原則可保證當擁有物件超出範圍時，所有資源都會正確地傳回作業系統。

為了支援簡單採用 RAII 準則，c + + 標準程式庫提供三種智慧型指標類型： [`std::unique_ptr`](../standard-library/unique-ptr-class.md) 、 [`std::shared_ptr`](../standard-library/shared-ptr-class.md) 和 [`std::weak_ptr`](../standard-library/weak-ptr-class.md) 。 智慧型指標可處理它所擁有之記憶體的配置和刪除。 下列範例顯示的類別具有在的呼叫中，在堆積上配置的陣列成員 `make_unique()` 。 對和的 **`new`** 呼叫 **`delete`** 會由類別封裝 `unique_ptr` 。 當 `widget` 物件超出範圍時，就會叫用 unique_ptr 的函式，並釋放為數組配置的記憶體。  

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

請盡可能在配置堆積記憶體時使用智慧型指標。 如果您必須明確地使用 new 和 delete 運算子，請遵循 RAII 的原則。 如需詳細資訊，請參閱 [物件存留期和資源管理 (RAII) ](object-lifetime-and-resource-management-modern-cpp.md)。

## <a name="stdstring-and-stdstring_view"></a>`std::string` 和 `std::string_view`

C 樣式字串是另一個主要的錯誤來源。 藉由使用[ `std::string` 和 `std::wstring` ](../standard-library/basic-string-class.md)，您可以消除幾乎所有與 C 樣式字串相關的錯誤。 您也會獲得搜尋、附加、前置等等的成員函式的優點。 兩者都經過高度優化，以加快速度。 將字串傳遞至只需要唯讀存取權的函式時，您可以使用 c + + 17， [`std::string_view`](../standard-library/basic-string-view-class.md) 以獲得更好的效能優勢。

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector` 和其他標準程式庫容器

標準程式庫容器全都遵循 RAII 的原則。 它們提供反覆運算器來進行專案的安全遍歷。 而且，它們已針對效能進行高度優化，並已針對正確性進行徹底測試。 藉由使用這些容器，您可以消除自訂資料結構可能引進的錯誤或效率不佳的可能性。 不是原始陣列，而是以 [`vector`](../standard-library/vector-class.md) c + + 中的連續容器來使用。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用 [`map`](../standard-library/map-class.md) (不 `unordered_map`) 為預設的關聯容器。 [`set`](../standard-library/set-class.md) [`multimap`](../standard-library/multimap-class.md) [`multiset`](../standard-library/multiset-class.md) 針對退化和多重案例使用、和。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

當需要效能優化時，請考慮使用：

- 內嵌 [`array`](../standard-library/array-class-stl.md) 時的型別很重要，例如，做為類別成員。

- 未排序的關聯容器（例如） [`unordered_map`](../standard-library/unordered-map-class.md) 。 這些專案具有較低的每個專案的額外負荷和長期查閱，但可能難以正確且有效率地使用。

- 排序 `vector` 。 如需詳細資訊，請參閱[演算法](../standard-library/algorithms.md)。

請勿使用 C 樣式陣列。 對於需要直接存取資料的舊版 Api，請改用存取子方法（例如） `f(vec.data(), vec.size());` 。 如需容器的詳細資訊，請參閱 [c + + 標準程式庫容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>標準程式庫演算法

在假設您需要為程式撰寫自訂演算法之前，請先參閱 c + + 標準程式庫 [演算法](../standard-library/algorithm.md)。 標準程式庫包含不斷成長的演算法，適用于許多常見的作業，例如搜尋、排序、篩選和隨機化。 數學程式庫很廣泛。 從 c + + 17 開始，提供許多演算法的平行版本。

以下是一些重要的範例：

- `for_each`，預設的「遍歷演算法」 (以及以範圍為基礎的 `for` 迴圈) 。

- `transform`，用於就地修改容器元素

- `find_if`，預設搜尋演算法。

- `sort`、 `lower_bound` 和其他預設排序和搜尋演算法。

若要撰寫比較子，請使用 strict， **`<`** 並在可以時使用 *命名的 lambda* 。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto` 而不是明確的型別名稱

C + + 11 引進了在 [`auto`](auto-cpp.md) 變數、函式和範本宣告中使用的關鍵字。 **`auto`** 告訴編譯器推斷物件的型別，讓您不必明確地輸入它。 **`auto`** 當推算的型別是嵌套的範本時特別有用：

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>以範圍為基礎的 `for` 迴圈

在陣列和容器上進行 C 樣式反覆運算很容易就會產生錯誤的索引，而且鍵入的繁瑣也相當繁瑣。 若要排除這些錯誤，並讓您的程式碼更容易閱讀，請使用以範圍為基礎的 **`for`** 迴圈搭配標準程式庫容器和原始陣列。 如需詳細資訊，請參閱以 [範圍為基礎的 `for` 語句](../cpp/range-based-for-statement-cpp.md)。

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

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr` 運算式而非宏

C 和 c + + 中的宏是在編譯之前由預處理器處理的權杖。 在編譯檔案之前，會將宏標記的每個實例取代為其定義的值或運算式。 宏通常用於 C 樣式程式設計中，以定義編譯時間常數值。 不過，宏很容易出錯，而且難以進行調試。 在新式 c + + 中，您應該偏好將 [`constexpr`](constexpr-cpp.md) 變數用於編譯時期常數：

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>統一初始化

在新式 c + + 中，您可以針對任何類型使用括弧初始化。 初始化陣列、向量或其他容器時，這種形式的初始化特別方便。 在下列範例中， `v2` 會使用三個實例來初始化 `S` 。 `v3` 初始化時，會使用以 `S` 大括弧初始化的三個實例。 編譯器會根據的宣告型別推斷每個元素的型別 `v3` 。

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

如需詳細資訊，請參閱 [括弧初始化](initializing-classes-and-structs-without-constructors-cpp.md)。

## <a name="move-semantics"></a>移動語義

新式 c + + 提供 *移動語義*，讓您可以消除不必要的記憶體複製。 在舊版的語言中，在某些情況下無法避免複製。 *移動*作業會將資源的擁有權從某個物件轉移至下一個物件，而不需要進行複製。 某些類別擁有堆積記憶體、檔案控制代碼等資源。 當您執行資源擁有的類別時，您可以定義 *移動* 函式和 *移動指派運算子* 。 編譯器會在不需要複製的情況下，于多載解析期間選擇這些特殊成員。 標準程式庫容器類型會叫用物件上的移動函式（如果有定義的話）。 如需詳細資訊，請參閱 [移動函數和移動指派運算子 (c + +) ](move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="lambda-expressions"></a>Lambda 運算式

在 C 樣式程式設計中，函式可以使用函式 *指標*傳遞至另一個函式。 函式指標不太方便維護和瞭解。 它們所參考的函式可以在原始程式碼中的其他地方定義，而不是從叫用它的位置。 此外，它們不是型別安全。 新式 c + + 提供的函式 *物件*是覆寫運算子的類別 [`operator()`](function-call-operator-parens.md) ，可讓它們以函式的形式來呼叫。 建立函式物件最方便的方式，就是使用內嵌 [lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。 下列範例示範如何使用 lambda 運算式來傳遞函式物件，該函式會在 `for_each` 向量中的每個專案上叫用函式：

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Lambda 運算式可以讀取為「函式，該函式會 `[=](int i) { return i > x && i < y; }` 採用類型的單一引數 **`int`** ，並傳回布林值，指出引數是否大於 `x` 且小於」 `y` 。 請注意，您 `x` `y` 可以在 lambda 中使用來自周圍內容的變數和。 指定以傳 `[=]` 值方式 *捕捉* 這些變數; 換句話說，lambda 運算式有自己的這些值的複本。

## <a name="exceptions"></a>例外狀況

新式 c + + 強調例外狀況，而不是錯誤碼，作為報告和處理錯誤狀況的最佳方式。 如需詳細資訊，請參閱 [新式 c + + 的例外狀況和錯誤處理最佳做法](errors-and-exception-handling-modern-cpp.md)。

## `std::atomic`

針對執行緒間通訊機制，使用 c + + 標準程式庫 [`std::atomic`](../standard-library/atomic-structure.md) 結構和相關類型。

## <a name="stdvariant-c17"></a>`std::variant` (C + + 17) 

等位通常用於 C 樣式程式設計中，藉由讓不同類型的成員佔用相同的記憶體位置來節省記憶體。 不過，等位不是型別安全，而且很容易發生程式設計錯誤。 C + + 17 引進了類別，做為等位 [`std::variant`](../standard-library/variant-class.md) 的更健全且安全的替代方案。 [`std::visit`](../standard-library/variant-functions.md#visit)函數可以用型別安全的方式，用來存取型別的成員 `variant` 。

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)\
[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)\
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)\
[Microsoft c + + 語言一致性資料表](../overview/visual-cpp-language-conformance.md)
