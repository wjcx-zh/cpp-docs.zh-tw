---
title: 歡迎回到C++ - 現代C++
description: 描述了現代C++的新程式設計習語及其原理。
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369497"
---
# <a name="welcome-back-to-c---modern-c"></a>歡迎回到C++ - 現代C++

自創建以來,C++已成為世界上使用最廣泛的程式設計語言之一。 編寫完善的 C++ 程式不但執行快速，而且有效率。 該語言比其他語言更靈活:它可以在最高抽象級別工作,在矽級別下。 C++提供高度優化的標準庫。 它允許訪問低級硬體功能,以最大限度地提高速度和最小化記憶體需求。 使用C++,您可以創建各種應用。 遊戲、設備驅動程式和高性能科學軟體。 嵌入式程式。 Windows 用戶端應用。 甚至其他程式設計語言的庫和編譯器也以C++編寫。

C++ 的其中一個原始需求是與 C 語言的回溯相容性。 因此,C++始終允許使用 C 樣式編程,包括原始指標、陣列、null 端接字串和其他功能。 它們可能實現出色的性能,但也會產生錯誤和複雜性。 C++的演變強調了使用C型習語的需求。 舊的 C 程式設計設施在您需要時就在那裡,但使用現代 C++代碼,您應該越來越需要它們。 現代C++代碼更簡單、更安全、更優雅,而且仍然和以往一樣快。

以下各節概述了現代C++的主要特點。 除非另有說明,此處列出的功能可在 C++11 及更高版本中提供。 在 Microsoft C++編譯器中,可以設置[/std](../build/reference/std-specify-language-standard-version.md)編譯器選項以指定要用於專案的標準版本。

## <a name="resources-and-smart-pointers"></a>資源和智慧指標

C 類程式設計中的主要錯誤類別之一是*記憶體洩漏*。 漏漏通常是由於無法呼叫使用**new**分配的記憶體的**刪除**。 現代C++強調*資源獲取的原則是初始化*(RAII)。 這個想法很簡單。 資源(堆記憶體、檔案句柄、套接字等)應由物件*擁有*。 該物件在其構造函數中創建或接收新分配的資源,並在其析構函數中刪除它。 RAII 原則可確保當擁有的物件超出範圍時,所有資源都正確返回到操作系統。

為了支援輕鬆採用 RAII 原則,C++標準庫提供了三種智慧指標類型[:std:unique_ptr、std::shared_ptr](../standard-library/unique-ptr-class.md)和[std::weak_ptr](../standard-library/weak-ptr-class.md)。 [std::shared_ptr](../standard-library/shared-ptr-class.md) 智慧指標處理其擁有的記憶體的分配和刪除。 下面的示例顯示一個類,該類具有在調用`make_unique()`的堆上分配的數位成員。 對**新**調用和**刪除**的調用由`unique_ptr`類封裝。 當`widget`物件超出範圍時,將調用unique_ptr析構函數,並將釋放為陣列分配的記憶體。  

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

只要有可能,在分配堆記憶體時使用智慧指標。 如果必須顯式使用新的運算元和刪除運算符,請遵循 RAII 原則。 有關詳細資訊,請參閱[物件存留期和資源管理 (RAII)。](object-lifetime-and-resource-management-modern-cpp.md)

## <a name="stdstring-and-stdstring_view"></a>std::字串和 std::string_view

C 樣式字串是 Bug 的另一個主要來源。 通過使用[std::string 和 std::wstring,](../standard-library/basic-string-class.md)您可以消除幾乎所有與 C 樣式字串相關的錯誤。 您還可以從成員函數中獲益,用於搜索、追加、預處理等。 兩者都高度優化速度。 將字串傳遞到僅需要唯讀存取的函數時,在 C++17 中,可以使用[std::string_view,](../standard-library/basic-string-view-class.md)以取得更大的性能優勢。

## <a name="stdvector-and-other-standard-library-containers"></a>標準::向量和其他標準庫容器

標準庫容器都遵循 RAII 的原則。 它們為元素的安全遍歷提供了反覆運算器。 而且,它們針對性能進行了高度優化,並經過過正確的徹底測試。 通過使用這些容器,您可以消除在自定義數據結構中可能出現的錯誤或效率低下的可能性。 在C++中使用[向量](../standard-library/vector-class.md)作為順序容器,而不是原始陣列。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[映射](../standard-library/map-class.md)`unordered_map`(而不是 )作為預設關聯容器。 使用[集](../standard-library/set-class.md)、[多映射](../standard-library/multimap-class.md)和[多集](../standard-library/multiset-class.md)進行退化和多案例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

當需要優化性能時,請考慮使用:

- 嵌入時的[數位](../standard-library/array-class-stl.md)類型很重要,例如,作為類成員。

- 沒有序的關聯容器,如[unordered_map](../standard-library/unordered-map-class.md)。 這些具有較低的每個元素開銷和恆定時間查找,但它們可能更難正確和高效地使用。

- 排`vector`序排序 。 如需詳細資訊，請參閱[演算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 樣式陣組。 對於需要直接存取資料的舊 API,請使用存取器`f(vec.data(), vec.size());`方法,例如 。 有關容器的詳細資訊,請參閱[C++標準庫容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>標準庫演演算法

在假定需要為程式編寫自定義演演算法之前,請先查看C++標準庫[演演演算法](../standard-library/algorithm.md)。 標準庫包含越來越多的演演演算法,用於許多常見操作,如搜索、排序、篩選和隨機化。 數學庫很廣泛。 從 C++17 開始,提供了許多演演演算法的並行版本。

下面是一些重要範例:

- **for_each**,預設遍歷演演演算法(以及基於範圍的迴圈)。

- **轉換**,用於容器元素的不到位修改

- **find_if**,默認搜索演演演算法。

- **排序****、lower_bound**和其他預設排序和搜尋演演演算法。

要編寫比較器,請使用嚴格**<**,並盡可能使用名為*lambdas。*

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>自動而非顯示式型態名稱

C++11 引入了[用於](auto-cpp.md)變數、函數和範本聲明的自動關鍵字。 **自動**告訴編譯器推斷物件的類型,這樣您就不必顯式鍵入它。 當推算類型是嵌套樣本時,**自動**特別有用:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>基於範圍的循環

陣列和容器的 C 樣式反覆運算容易出現索引錯誤,而且鍵入也十分繁瑣。 為了消除這些錯誤並使代碼更具可讀性,請使用基於範圍的用於標準庫容器和原始陣列的迴圈。 有關詳細資訊,請參閱[基於範圍的語句](../cpp/range-based-for-statement-cpp.md)。

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

## <a name="constexpr-expressions-instead-of-macros"></a>缺點運算式而不是宏

C 和 C++ 中的宏是預處理器在編譯前處理的權杖。 在編譯檔之前,宏令牌的每個實例都將替換為其定義的值或表達式。 宏通常用於 C 樣式編程,用於定義編譯時常量值。 但是,宏容易出錯且難以調試。 在現代C++中,您應該更喜歡編譯時間常量的[constexpr](constexpr-cpp.md)變數:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>統一初始化

在現代C++中,可以為任何類型的大括弧初始化使用大括弧初始化。 這種初始化形式在初始化陣組、向量或其他容器時特別方便。 在下面的範例中,`v2`使用的三`S`個 實體初始化。 `v3`使用使用大括弧初始化的`S`三個實例進行初始化。 編譯器根據 宣告的類型推斷每個元素的`v3`類型 。

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

有關詳細資訊,請參閱[Brace 初始化](initializing-classes-and-structs-without-constructors-cpp.md)。

## <a name="move-semantics"></a>移動語義

現代C++提供*移動語義*,從而可以消除不必要的記憶體副本。 在語言的早期版本中,在某些情況下,副本是不可避免的。 *移動*操作將資源的擁有權從一個對象轉移到下一個物件,而不進行複製。 實現擁有資源的類別(如堆記憶體、檔案句柄等)時,可以為其定義*移動建構函數*和*移動賦值運算子*。 在不需要副本的情況下,編譯器將在重載解析期間選擇這些特殊成員。 標準庫容器類型在物件上調用移動構造函數(如果定義了。 有關詳細資訊,請參閱[移動構造函數和移動分配運算符 (C++)。](move-constructors-and-move-assignment-operators-cpp.md)

## <a name="lambda-expressions"></a>Lambda 運算式

在 C 樣式編程中,可以使用*函數指標*將函數傳遞給另一個函數。 函數指標在維護和理解方面不方便。 它們引用的函數可以在原始程式碼的其他地方定義,遠離調用它的點。 此外,它們不是類型安全的。 現代C++提供*函數物件*,類重寫[()](function-call-operator-parens.md)運算符,這使得它們可以像函數一樣調用。 建立函數物件的最方便方法是使用內聯[lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。 下面的範例展示如何使用 lambda 運算式傳遞函式`for_each`物件, 此函數會在向量中的每個元素上調用該函數:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

lambda 表示`[=](int i) { return i > x && i < y; }`式 可以讀取為函數,該函式採用單個類型`int`的 參數,並傳回布林,指示參數是否`x`大於與小`y`於 。 請注意,變數`x`和`y`來自周圍上下文的變數可以在 lambda 中使用。 指定`[=]`這些變數由值捕捉;但是,這些變數的*用值擷取*。換句話說,lambda 表達式具有這些值的自身副本。

## <a name="exceptions"></a>例外狀況

現代C++強調異常,而不是錯誤代碼,這是報告和處理錯誤條件的最佳方式。 有關詳細資訊,請參閱[有關異常和錯誤處理的現代C++最佳做法](errors-and-exception-handling-modern-cpp.md)。

## <a name="stdatomic"></a>std::原子

使用C++標準庫[(標準庫):原子](../standard-library/atomic-structure.md)結構和相關類型,用於線程間通信機制。

## <a name="stdvariant-c17"></a>分值:變數 (C++17)

聯合通常用於 C 樣式程式設計,透過不同類型的成員佔用相同的記憶體位置來節省記憶體。 但是,聯合類型不安全,並且容易出現程式設計錯誤。 C++17 引入了[std::變型](../standard-library/variant-class.md)類,作為聯合的更強大、更安全的替代。 [std::存取](../standard-library/variant-functions.md#visit)函數可用於以類型安全`variant`的方式存取 類型的成員。

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)\
[蘭姆達運算式](../cpp/lambda-expressions-in-cpp.md)\
[C++標準庫](../standard-library/cpp-standard-library-reference.md)\
[微軟C++語言一致性表](../overview/visual-cpp-language-conformance.md)
