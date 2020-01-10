---
title: C++ 中的模組概觀
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: C + + 20 中的模組提供標頭檔的新式替代方式。
ms.openlocfilehash: 28e1824250ad4fb404c528aa9511745abb001f31
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301375"
---
# <a name="overview-of-modules-in-c"></a>C++ 中的模組概觀

C + + 20 引進了*模組*，這是元件化C++程式庫和程式的現代化解決方案。 模組是一組原始程式碼檔案，這些檔案會與匯入它們的[轉譯單位](https://wikipedia.org/wiki/Translation_unit_(programming))分開編譯。 模組會消除或大幅減少與使用標頭檔相關的許多問題，也可能會減少編譯時間。 不會顯示在模組中宣告的宏、預處理器指示詞和非匯出的名稱，因此不會影響匯入模組之轉譯單元的編譯。 您可以依照任何順序匯入模組，而不需要考慮宏重新定義。 匯入轉譯單位中的宣告不會參與已匯入之模組中的多載解析或名稱查詢。 在模組編譯一次之後，結果會儲存在二進位檔案中，以描述所有匯出的類型、函數和範本。 該檔案的處理速度快于標頭檔，而且編譯器可以在每次將模組匯入專案的位置重複使用。

模組可以與標頭檔並存使用。 C++原始檔可以匯入模組，也會 #include 標頭檔案。 在某些情況下，您可以將標頭檔匯入為模組，而不是預處理器 #included 的以程式方式提供。 我們建議新的專案盡可能使用模組，而不是標頭檔。 對於開發中較大的現有專案，我們建議您嘗試將舊版標頭轉換成模組，以瞭解您在編譯時間是否有意義的縮減。

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>在 Microsoft C++編譯器中啟用模組

從 Visual Studio 2019 16.2 版，模組不會在 Microsoft C++編譯器中完全執行。 您可以使用模組功能來建立單一資料分割模組，並匯入 Microsoft 所提供的標準程式庫模組。 若要啟用對模組的支援，請使用[/experimental： module](../build/reference/experimental-module.md)和[/std： c + + 最新版本](../build/reference/std-specify-language-standard-version.md)進行編譯。 在 Visual Studio 專案中，以滑鼠右鍵按一下**方案總管**中的專案節點，然後選擇 [**屬性**]。 將 設定 下拉式選在**所有**設定，然後**選擇 設定** **屬性** >  **C/C++**  > **語言** > **啟用C++模組（實驗性）** 。

模組和使用它的程式碼必須使用相同的編譯器選項進行編譯。

## <a name="consume-the-c-standard-library-as-modules"></a>使用C++標準程式庫作為模組

雖然 c + + 20 標準未指定，但 Microsoft 可將C++標準程式庫的實作為模組匯入。 藉由匯C++入標準程式庫做為模組，而不是透過標頭檔 #including 它，您可以根據專案的大小來加速編譯時間。 程式庫會元件化至下列模組：

- 標準 RegEx 提供標頭 \<RegEx 的內容 >
- std. filesystem 提供標頭的內容 \<檔案系統 >
- std 記憶體提供標頭 \<記憶體的內容 >
- 「標準執行緒」提供標頭的內容，\<不可部分完成的 >、\<condition_variable >、\<未來 >、\<mutex >、\<shared_mutex > 和 \<執行緒 >
- std 提供標準程式庫中的C++其他專案

若要使用這些模組，只要將匯入宣告新增至原始程式碼檔案的頂端即可。 例如：

```cpp
import std.core;
import std.regex;
```

若要使用 Microsoft 標準程式庫模組，請使用[/ehsc](../build/reference/eh-exception-handling-model.md)和[/md](../build/reference/md-mt-ld-use-run-time-library.md)選項來編譯您的程式。

## <a name="basic-example"></a>基本範例

下列範例顯示名為**Foo. ixx**之原始檔中的簡單模組定義。 Visual Studio 中的模組介面檔案需要**ixx**副檔名。 在此範例中，介面檔案包含函式定義和宣告。 不過，定義也可以放在一或多個不同的檔案中（如稍後的範例所示）。 **Export 模組 Foo**語句指出此檔案是稱為 `Foo`之模組的主要介面。 `f()` 上的**export**修飾詞表示當另一個程式或模組匯入 `Foo` 時，將會顯示此函式。 請注意，模組會參考 `Bar`的命名空間。

```cpp
export module Foo;

#define ANSWER 42

namespace Bar 
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

檔案**myprogram.exe**會使用匯**入**宣告來存取 `Foo`所匯出的名稱。 請注意，名稱 `Bar` 會顯示在這裡，但不是所有的成員。 也請注意，不會顯示宏 `ANSWER`。

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

匯入宣告只能出現在全域範圍中。

## <a name="implementing-modules"></a>執行模組

您可以使用單一介面檔案（. ixx）來建立模組，該檔案會匯出名稱並包含所有函式和類型的實作為。 您也可以將此部署放在一或多個不同的執行檔中，類似于使用 .h 和 .cpp 檔案的方式。 **Export**關鍵字僅適用于介面檔案。 執行檔案可以匯**入**另一個模組，但無法**匯出**任何名稱。 可以使用任何副檔名來命名執行檔。 系統會將介面檔案和其後置的一組執行檔視為一種特殊的轉譯單位，稱為*模組單位*。 在任何執行檔中宣告的名稱會自動顯示在相同模組單元中的所有其他檔案中。

對於較大的模組，您可以將模組分割為多個模組單元 *，稱為「* 分割區」。 每個分割區都是由一個或多個執行檔支援的介面檔所組成。 （從 Visual Studio 2019 版本16.2，尚未完全執行資料分割）。

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>模組、命名空間和引數相依的查閱

模組中的命名空間規則與任何其他程式碼中的相同。 如果匯出命名空間內的宣告，則也會隱含地匯出封入的命名空間（不包括非匯出的成員）。 如果明確匯出命名空間，則會匯出該命名空間定義內的所有宣告。

在匯入轉譯單位中針對多載解析執行引數相依的查閱時，編譯器會將在相同轉譯單位（包括模組介面）中宣告的函式，視為函式引數的類型。已定義。

### <a name="module-partitions"></a>模組磁碟分割

> [!NOTE]
> 這一節是針對完整性而提供的。 分割區尚未在 Microsoft C++編譯器中執行。

模組可以元件*化成分割*區，每個都包含一個介面檔案和零或多個執行檔。 模組磁碟分割類似于模組，不同之處在于它會共用整個模組中所有宣告的擁有權。 分割區介面檔案所匯出的所有名稱都是由主要介面檔案匯入和重新匯出。 資料分割的名稱必須以模組名稱開頭，後面接著冒號。 在整個模組中，都可以看到任何分割區中的宣告。 不需要採取任何特殊預防措施來避免發生單一定義規則（ODR）錯誤。 您可以在一個資料分割中宣告名稱（函式、類別等），並在另一個資料分割中定義它。 分割區的執行檔案的開頭如下：

```cpp
module Foo:part1
```

而分割區介面檔案的開頭就像這樣：

```cpp
export module Foo:part1
```

若要存取另一個分割區中的宣告，分割區必須匯入，但它只能使用分割區名稱，而不是模組名稱：

```cpp
module Foo:part2;
import :part1;
```

主要介面單位必須匯入並重新匯出所有模組的介面分割區檔案，如下所示：

```cpp
export import :part1
export import :part2
...
```

主要介面單位可以匯入資料分割執行檔案，但無法匯出它們，因為這些檔案不允許匯出任何名稱。 這可讓模組保有模組內部的執行詳細資料。

## <a name="modules-and-header-files"></a>模組和標頭檔

您可以將標頭檔放在模組來源檔案中，方法是在模組宣告之前放置 `#include` 指示詞。 這些檔案會被視為位於*全域模組片段*中。 模組只能在*全域模組片段*中看到其明確包含的標頭中的名稱。 全域模組片段只包含實際使用的符號。

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

您可以使用傳統的標頭檔來控制要匯入的模組：

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>匯入的標頭檔

> [!NOTE]
> 本節僅供參考。 舊版匯入尚未在 Microsoft C++編譯器中執行。

有些標頭是完全獨立的，可以使用**import**關鍵字來帶入它們。 匯入的標頭和匯入的模組之間的主要差異在於，緊接在 import 語句之後的匯入程式中，會顯示標頭中的任何預處理器定義。 （*不*會顯示該標頭所包含之任何檔案中的預處理器定義）。

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>請參閱

[模組、匯入、匯出](import-export-module.md)
