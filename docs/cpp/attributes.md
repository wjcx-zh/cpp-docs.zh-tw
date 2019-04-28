---
title: 中的屬性C++
ms.date: 06/01/2018
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 81de2816c208d5ddc879f04d70912c3dddcd7832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284743"
---
# <a name="attributes-in-c"></a>中的屬性C++

C++標準會定義一組屬性，並也可讓編譯器廠商，以定義自己的屬性 （在廠商特定命名空間中），但編譯器才能辨識只有在標準中所定義的屬性。

在某些情況下，標準的屬性與重疊編緝器特定 declspec 而發出的參數。 在視覺效果C++，您可以使用`[[deprecated]]`屬性，而不是使用`declspec(deprecated)`並將任何符合標準編譯器所辨識的屬性。 對於所有其他 declspec 參數 dllimport 和 dllexport 等，還沒有屬性的對等項目所以您必須繼續使用 declspec 而發出的語法。 屬性不會影響類型系統，且不變更程式的意義。 編譯器會忽略它們無法辨識的屬性值。

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):在屬性清單的範圍內，您可以使用單一指定所有名稱的命名空間**使用**introducer:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++標準屬性

在 C + + 11 中，屬性會提供標準化的方式，來加上註解C++可能會或可能不到供應商特有的其他資訊的建構 （包括但不是限於類別、 函式、 變數和區塊）。 編譯器產生參考用訊息，或是編譯屬性化程式碼時套用特殊邏輯，可以使用這項資訊。 編譯器會忽略無法辨識，任何屬性，這表示您無法定義自己的自訂屬性使用此語法。 屬性會以雙精度浮點的方括號括住：

```cpp
[[deprecated]]
void Foo(int);
```

屬性代表 #pragma 指示詞，例如特定廠商擴充功能的標準化的替代 __declspec (Visual C++)，或&#95;&#95;屬性&#95;&#95; (GNU)。 不過，您仍需要廠商特定建構用於大部分的用途。 標準目前會指定符合的編譯器應該會辨識下列屬性：

- `[[noreturn]]` 指定函式永遠不會傳回;亦即它一定會擲回例外狀況。 編譯器可以調整其編譯規則`[[noreturn]]`實體。

- `[[carries_dependency]]` 指定函式會傳播相關執行緒同步處理排序的資料相依性。 屬性可以套用至一或多個參數，以指定傳入的引數會攜帶到函式主體的相依性。 屬性可以套用至函式本身，以指定的傳回值會從函式的相依性。 編譯器可以使用這項資訊來產生更有效率的程式碼。

- `[[deprecated]]` **Visual Studio 2015 和更新版本：** 指定函式不適用於使用，而且可能會存在在未來的版本的程式庫介面。 編譯器可以使用這個來產生參考用訊息，當用戶端程式碼嘗試呼叫函式。 可以套用至類別、 typedef 名稱、 變數、 非靜態資料成員、 函式、 命名空間、 列舉型別、 列舉值或樣板特製化的宣告。

- `[[fallthrough]]` **Visual Studio 2017 和更新版本：** (適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md))`[[fallthrough]]`屬性可用的內容中[切換](switch-statement-cpp.md)以做為編譯器 （或任何人讀取提示的陳述式程式碼） 的 fallthrough 行為。 視覺效果C++編譯器目前不會在警告上 fallthrough 行為，所以這個屬性沒有任何效果編譯器行為。

- `[[nodiscard]]` **Visual Studio 2017 版本 15.3 和更新版本：** (適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定函式的傳回值並不適合被捨棄。 引發警告 C4834，在此範例中所示：

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 版本 15.3 和更新版本：** (適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定的變數、 函式、 類別、 typedef、 非靜態資料成員、 列舉或樣板特製化可能會刻意不會使用。 實體標記時，編譯器不會警告`[[maybe_unused]]`未使用。 與屬性，反之亦然，稍後可以重新宣告沒有屬性宣告的實體。 實體會被視為標記標示為其第一個宣告分析之後，以及轉譯目前轉譯單位的其餘部分。

## <a name="microsoft-specific-attributes"></a>Microsoft 特定屬性

- `[[gsl::suppress(rules)]]` 此 Microsoft 特定屬性用來隱藏警告的強制執行的西洋棋[指導方針的支援程式庫 (GSL)](https://github.com/Microsoft/GSL)程式碼中的規則。 此程式碼片段為例：

    ```cpp
    void main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

  此範例中，會引發下列警告：

  - 26494 (輸入規則 5:一律初始化物件。）

  - 26485 (範圍規則 3:沒有指標衰減陣列。）

  - 26481 (規則 1，範圍：請勿使用指標算術。 請改用 span。）

  當您編譯此程式碼使用 CppCoreCheck 程式碼分析工具安裝並啟動時，就會引發的前兩個警告。 但並不會因為屬性中引發的第三個警告。 您可以藉由撰寫且不包含幾個特定規則的 [[gsl::suppress(bounds)]] 隱藏整個 「 範圍 」 設定檔。 C++ Core Guidelines 專門設計來協助您撰寫更好且更安全的程式碼。 隱藏屬性讓您更容易時不想要關閉的警告。