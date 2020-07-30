---
title: C + + 中的屬性
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: efdc62e2343135aee483520f633bac99519455b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229203"
---
# <a name="attributes-in-c"></a>C + + 中的屬性

C + + 標準會定義一組屬性，也可讓編譯器廠商定義自己的屬性（在廠商專屬的命名空間內），但編譯器只需要辨識標準中定義的屬性。

在某些情況下，標準屬性會與編譯器特定的 declspec 參數重迭。 在 Visual C++ 中，您可以使用 `[[deprecated]]` 屬性，而不是使用 `declspec(deprecated)` ，而且任何符合的編譯器都會辨識屬性。 對於所有其他的 declspec 參數（例如 dllimport 和 dllexport），除了屬性對等，您還必須繼續使用 declspec 語法。 屬性不會影響類型系統，而且不會變更程式的意義。 編譯器會忽略無法辨識的屬性值。

**Visual Studio 2017 15.3 版和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：在屬性清單的範圍內，您可以使用單一 introducer 來指定所有名稱的命名空間 **`using`** ：

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C + + 標準屬性

在 c + + 11 中，屬性提供了一種標準化的方式，可將 c + + 結構（包括但不限於類別、函式、變數和區塊）標注為其他不一定是廠商特有的資訊。 編譯器可以使用此資訊來產生參考用訊息，或在編譯屬性化程式碼時套用特殊邏輯。 編譯器會忽略無法辨識的任何屬性，這表示您無法使用此語法來定義您自己的自訂屬性。 屬性會以雙方括弧括住：

```cpp
[[deprecated]]
void Foo(int);
```

屬性代表特定廠商擴充功能的標準化替代方式，例如 #pragma 指示詞、__declspec （）（Visual C++），或 &#95;&#95;屬性&#95;&#95;  （GNU）。 不過，您仍然需要使用廠商專屬的結構來進行大部分的工作。 標準目前指定了下列屬性，這些是符合的編譯器應該辨識的屬性：

- `[[noreturn]]`指定函數永遠不會傳回;換句話說，它一律會擲回例外狀況。 編譯器可以調整其實體的編譯規則 `[[noreturn]]` 。

- `[[carries_dependency]]`指定函式會傳播與執行緒同步處理有關的資料相依性排序。 屬性可以套用至一或多個參數，以指定傳入的引數會在函式主體中攜帶相依性。 屬性可以套用至函式本身，以指定傳回值會從函式中承擔相依性。 編譯器可以使用此資訊來產生更有效率的程式碼。

- `[[deprecated]]`**Visual Studio 2015 和更新版本：** 指定函式不打算使用，而且可能不存在於程式庫介面的未來版本中。 當用戶端程式代碼嘗試呼叫函式時，編譯器可以使用此函數來產生參考用訊息。 可以套用至類別、typedef 名稱、變數、非靜態資料成員、函式、命名空間、列舉、枚舉器或範本特製化的宣告。

- `[[fallthrough]]`**Visual Studio 2017 和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）， `[[fallthrough]]` 屬性可以在[switch](switch-statement-cpp.md)語句的內容中用來當做 fallthrough 行為所預期的編譯器（或讀取程式碼的任何人）的提示。 Microsoft c + + 編譯器目前不會警告 fallthrough 行為，因此這個屬性不會影響編譯器行為。

- `[[nodiscard]]`**Visual Studio 2017 15.3 版和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）指定函式的傳回值不會被捨棄。 引發警告 C4834，如下列範例所示：

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Visual Studio 2017 15.3 版和更新版本：** （可與[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)搭配使用）指定不使用變數、函式、類別、typedef、非靜態資料成員、列舉或樣板特製化。 未使用標示的實體時，編譯器不會發出警告 `[[maybe_unused]]` 。 不含屬性宣告的實體之後可以使用屬性重新宣告，反之亦然。 實體會在其第一個標記為已分析的宣告之後，以及目前轉譯單位的其餘部分，被視為標示。

## <a name="microsoft-specific-attributes"></a>Microsoft 特有的屬性

- `[[gsl::suppress(rules)]]`這個 Microsoft 特有的屬性是用來隱藏在程式碼中強制執行[方針支援程式庫（GSL）](https://github.com/Microsoft/GSL)規則之檢查的警告。 例如，請考慮下列程式碼片段：

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  此範例會引發下列警告：

  - 26494（類型規則5：一律初始化物件）。

  - 26485（界限規則3：沒有陣列到指標衰減）。

  - 26481（界限規則1：不要使用指標算術。 請改用 span）。

  當您使用已安裝並啟用的 CppCoreCheck 程式碼分析工具來編譯此程式碼時，就會引發前兩個警告。 但是第三個警告並不會因為屬性而引發。 您可以藉由撰寫 [[gsl：：抑制（界限）]] 來隱藏整個界限設定檔，而不包含特定的規則編號。 C++ Core Guidelines 的設計可協助您撰寫更好且更安全的程式碼。 [隱藏] 屬性可讓您在不想要的時候，輕鬆關閉警告。
  