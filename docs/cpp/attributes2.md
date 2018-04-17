---
title: C + + 標準屬性 |Microsoft 文件
ms.custom: ''
ms.date: 03/28/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: d2dcce6b0e289588c426792a334ee4ec38d1ab5f
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2018
---
# <a name="attributes-in-c"></a>C + + 中的屬性

C + + 標準定義一組屬性，也可讓編譯器廠商，以定義自己的屬性 （廠商特定命名空間內），但編譯器必須能夠辨識只有在標準中定義的屬性。

在某些情況下，標準屬性重疊使用編譯器專用 declspec 參數。 在 Visual c + + 中，您可以使用`[[deprecated]]`屬性而不是使用`declspec(deprecated)`並將任何符合編譯器所辨識的屬性。 對於所有其他 declspec 參數例如 dllimport 和 dllexport，為尚未沒有屬性對等項目，您必須繼續使用 declspec 語法。 屬性不會影響類型系統中，而且它們不會變更程式的意義。 編譯器會忽略它們無法辨識的屬性值。

**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 在屬性清單的範圍內，您可以指定所有名稱的命名空間，以單一`using`introducer:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C + + 標準屬性

在 C + + 11 中，屬性會提供標準化的方式，來加上註解 c + + 建構 （包括但不是限於類別、 函式、 變數和區塊），並可能會或可能不是廠商專屬的其他資訊。 編譯器可以使用這項資訊來產生參考用訊息，或編譯屬性化程式碼時套用特殊的邏輯。 編譯器會忽略無法辨識，任何屬性，這表示您無法定義自己的自訂屬性，使用此語法。 屬性是由兩個方括號括住：

```cpp
[[deprecated]]
void Foo(int);
```

屬性代表 #pragma 指示詞，__declspec （Visual c + +），例如特定廠商延伸模組的標準化替代方案或&#95;&#95;屬性&#95;&#95; (GNU)。 不過，您仍然必須使用廠商專屬建構大部分的用途。 標準目前指定符合的編譯器應該會辨識下列屬性：

- `[[noreturn]]` 指定函式永遠不會傳回。亦即它一律會擲回例外狀況。 編譯器可以調整其編譯規則`[[noreturn]]`實體。

- `[[carries_dependency]]` 指定函式會傳播資料相依性順序與執行緒同步處理。 屬性可以套用至一或多個參數，以指定傳入的引數傳送至函式主體的相依性。 屬性可以套用至函式本身，以指定的傳回值會移到函式的相依性。 編譯器可以使用這項資訊來產生更有效率的程式碼。

- `[[deprecated]]` **Visual Studio 2015 和更新版本：**指定，函式不為了在使用，而且可能會存在在未來的版本的程式庫介面。 編譯器可以使用此用戶端程式碼嘗試呼叫函式時，產生參考用訊息。 可以套用至類別、 typedef 名稱、 變數、 非靜態資料成員、 函式、 命名空間、 列舉型別、 列舉值，或樣板特製化的宣告。  

- `[[fallthrough]]` **2017 和更新版本的 visual Studio:** (適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md))`[[fallthrough]]`屬性可用的內容中[切換](switch-statement-cpp.md)編譯器 （或任何人讀取提示陳述式程式碼），目的是 fallthrough 行為。 Visual c + + 編譯器目前不會在警告上 fallthrough 行為，所以此屬性不有任何效果編譯器行為。

- `[[nodiscard]]` **Visual Studio 2017 15.3 和更新版本：** (適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定函式的傳回值並不適合被捨棄。 引發警告 C4834，如本範例所示：

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 15.3 和更新版本：** (適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定的變數、 函式、 類別、 typedef、 非靜態資料成員、 列舉或樣板特製化可能會刻意不會使用。 實體標記時，編譯器不會警告`[[maybe_unused]]`未使用。 屬性，反之亦然，稍後可以重新宣告沒有屬性宣告的實體。 實體會被視為標記為標示為其第一個宣告會分析之後，和目前的轉譯單位的轉譯的其餘部分。

## <a name="microsoft-specific-attributes"></a>Microsoft 特定屬性

- `[[gsl::suppress(rules)]]` 此 Microsoft 特定的屬性用來隱藏警告的強制執行的西洋棋[指導方針支援程式庫 (GSL)](https://github.com/Microsoft/GSL)程式碼中的規則。 例如，請考慮此程式碼片段：

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

   此範例會引發下列警告：

   - 26494 (型別規則 5： 一律初始化物件。)

   - 26485 (範圍規則 3： 沒有陣列至指標衰退。)

   - 26481 (範圍規則 1： 不要使用指標算術。 請改用範圍。）

   您可以編譯此程式碼搭配 CppCoreCheck 程式碼分析工具安裝並啟動時，就會引發的前兩個警告。 但是，因為屬性不會引發的第三個警告。 您可以隱藏整個 「 範圍 」 設定檔寫入 [[gsl::suppress(bounds)]]，但不包含特定的規則數目。 C + + 核心指導方針，專門設計來協助您撰寫更好且更安全的程式碼。 隱藏屬性讓您更容易時不想要關閉的警告。
