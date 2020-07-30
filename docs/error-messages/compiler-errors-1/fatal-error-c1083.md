---
title: 嚴重錯誤 C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: f51e93475f104f165895c9d7e2733d741af30502
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389775"
---
# <a name="fatal-error-c1083"></a>嚴重錯誤 C1083

> 無法開啟檔案*類型*檔案： '*file*'：*訊息*

當編譯器找不到所需的檔案時，會產生 C1083 錯誤。 此錯誤的可能原因有很多。 不正確的 include 搜尋路徑或遺失或 misnamed 標頭檔是最常見的原因，但其他檔案類型和問題也可能造成 C1083。 以下是一些編譯器產生此錯誤的常見原因。

## <a name="the-specified-file-name-is-wrong"></a>指定的檔案名稱錯誤

檔案名稱可能輸入錯誤。 例如

`#include <algorithm.h>`

可能沒有找到您要的檔案。 大部分 c + + 標準程式庫標頭檔的副檔名都不是 .h。 這個指示詞 \<algorithm> 找不到標頭 `#include` 。 若要修正此問題，請確認已輸入正確的檔案名，如下列範例所示：

`#include <algorithm>`

某些 C 執行階段程式庫標頭位於標準 Include 目錄的子目錄中。 例如，若要包含 *`sys/types.h`* ，您必須在指示詞 *`sys`* 中包含子目錄名稱 `#include` ：

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>檔案不包含在 include 搜尋路徑中

編譯器無法使用 `#include` 或 `#import` 指示詞中指出的搜尋規則來找到檔案。 例如，當標頭檔名稱以引號括住時，

`#include "myincludefile.h"`

這會告訴編譯器先在包含原始程式檔的相同目錄中尋找檔案，然後再查看組建環境所指定的其他位置。 如果引號中含有絕對路徑，則編譯器只會在該位置尋找檔案。 如果引號中含有相對路徑，則編譯器會在來源目錄相對的目錄中尋找檔案。

如果名稱是以角括弧括住，

`#include <stdio.h>`

編譯器會遵循由組建環境、 **`/I`** 編譯器選項、 **`/X`** 編譯器選項和**INCLUDE**環境變數所定義的搜尋路徑。 如需詳細資訊，包括用來尋找檔案之搜尋順序的特定詳細資料，請參閱 #include 指示詞[（c/c + +）](../../preprocessor/hash-include-directive-c-cpp.md)和[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。

如果您的 include 檔案位於與來原始目錄相對的另一個目錄中，而且您在 include 指示詞中使用相對路徑，則必須使用雙引號，而不是角括弧。 例如，如果您的標頭檔位於 *`myheader.h`* 名為 header 的專案來源子目錄中，則此範例找不到檔案並導致 C1083：

`#include <headers\myheader.h>`

但此範例可運作：

`#include "headers\myheader.h"`

相對路徑也可以與 include 搜尋路徑上的目錄搭配使用。 如果您在 Visual Studio 中將目錄新增至**include**環境變數或**include 目錄**路徑，請勿同時將部分的路徑新增至 include 指示詞。 例如，如果您的標頭位於 *`\path\example\headers\myheader.h`* ，而且您 *`\path\example\headers\`* 在 Visual Studio 中新增至**Include 目錄**路徑，但您的指示詞將檔案 `#include` 稱為

`#include <headers\myheader.h>`

但找不到檔案。 請使用與 include 搜尋路徑中指定之目錄相對的正確路徑。 在此範例中，您可以將 include 搜尋路徑變更為 *`\path\example\`* ，或從指示詞 *`headers\`* 中移除路徑區段 `#include` 。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 vcpkg

如果您在嘗試將協力廠商程式庫設定為組建的一部分時看到此錯誤，請考慮使用 [`vcpkg`](../../vcpkg.md) c + + 封裝管理員來安裝和建立程式庫。 vcpkg 支援大量且不斷成長[的協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並將成功組建所需的所有設定屬性和相依性設為專案的一部分。

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>檔案位於您的專案中，但不是包含搜尋路徑

即使標頭檔列于**方案總管**中做為專案的一部分，只有在原始程式檔中的或指示詞參考檔案時，編譯器才會找到這些檔案 `#include` ，而且這些檔案 `#import` 位於 include 搜尋路徑中。 不同類型的組建可能會使用不同的搜尋路徑。 **`/X`** 編譯器選項可以用來排除 include 搜尋路徑中的目錄。 這樣可讓不同的組建使用同名但存放在不同目錄下的 Include 檔案。 這是除了使用前置處理器命令進行條件式編譯以外的另一種作法。 如需編譯器選項的詳細資訊 **`/X`** ，請參閱[ `/X` （忽略標準的 Include 路徑）](../../build/reference/x-ignore-standard-include-paths.md)。

若要修正此問題，請修正編譯器用來搜尋包含或匯入之檔案的路徑。 新的專案會使用預設包含搜尋路徑。 您可能必須修改 [包含搜尋路徑]，才能為您的專案新增目錄。 如果您要在命令列上進行編譯，請新增**INCLUDE**環境變數或編譯器選項的路徑， **`/I`** 以指定檔案的路徑。

若要在 Visual Studio 中設定 include 目錄路徑，請開啟專案的 [**屬性頁**] 對話方塊。 在左窗格的 [設定] [**屬性**] 下選取 [ **VC + + 目錄**]，然後編輯 [ **Include 目錄**] 屬性。 如需 Visual Studio 中編譯器所搜尋之每個使用者和每個專案目錄的詳細資訊，請參閱[VC + + 目錄屬性頁](../../build/reference/vcpp-directories-property-page.md)。 如需編譯器選項的詳細資訊 **`/I`** ，請參閱[ `/I` （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md)。

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>未設定命令列包含或 LIB 環境

在命令列叫用編譯器時，通常會使用環境變數指定搜尋路徑。 如果**INCLUDE**或**LIB**環境變數所描述的搜尋路徑未正確設定，則可以產生 C1083 錯誤。 我們強烈建議使用開發人員命令提示字元快捷方式來設定命令列組建的基本環境。 如需詳細資訊，請參閱[在命令列上建立 c/c + +](../../build/building-on-the-command-line.md)。 如需如何使用環境變數的詳細資訊，請參閱[如何：在組建中使用環境變數](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)。

## <a name="the-file-may-be-locked-or-in-use"></a>檔案可能已鎖定或在使用中

如果您使用其他程式來編輯或存取檔案，它可能會鎖定檔案。 嘗試在另一個程式中關閉檔案。 如果您使用平行編譯選項，有時候另一個程式可以 Visual Studio 本身。 如果關閉 [平行組建] 選項會使錯誤消失，這就是問題所在。 其他平行組建系統也可能會發生此問題。 請小心設定檔案和專案相依性，使組建順序正確。 在某些情況下，請考慮建立中繼專案，以強制執行可能由多個專案建立之通用檔案的組建相依性順序。 有時，防毒程式會暫時鎖定最近變更的檔案以進行掃描。 可能的話，請考慮從防毒軟體掃描程式排除您的專案組建目錄。

## <a name="the-wrong-version-of-a-file-name-is-included"></a>包含錯誤的檔案名稱版本

C1083 錯誤也可能表示包含了錯誤版本的檔案。 包含錯誤檔案版本的例子像是，組建包含的檔案在其 `#include` 指示詞中參考了該組建不適用的標頭檔。 例如，某些檔案可能只適用于 x86 組建或 Debug 組建。 找不到標頭檔時，編譯器會產生 C1083 錯誤。 若要修正這個問題，請使用正確的檔案，而不是將標頭檔或目錄加入至組建中。

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>先行編譯標頭檔未經先行編譯

當專案設定為使用先行編譯標頭檔時，您必須建立相關的檔案， *`.pch`* 才能編譯使用標頭內容的檔案。 例如，檔案 *`pch.cpp`* （ *`stdafx.cpp`* 在 Visual Studio 2017 和更早版本中）會自動在新專案的專案目錄中建立。 請先編譯該檔案以建立先行編譯標頭檔  在一般的組建流程設計中，這會自動完成。 如需詳細資訊，請參閱[建立先行編譯標頭檔](../../build/creating-precompiled-header-files.md)。

## <a name="additional-causes"></a>其他原因

- 您已安裝 SDK 或協力廠商程式庫，但在安裝 SDK 或程式庫之後，尚未開啟新的開發人員命令提示字元視窗。 如果 SDK 或程式庫將檔案新增至**INCLUDE**路徑，您可能需要開啟新的開發人員命令提示字元視窗，以挑選這些環境變數變更。

- 檔案使用 managed 程式碼，但 **`/clr`** 未指定編譯器選項。 如需詳細資訊，請參閱[ `/clr` （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

- 檔案是使用不同的編譯器選項設定進行編譯， **`/analyze`** 而不是用來先行編譯標頭。 當專案的標頭先行編譯時，全部都應該使用相同的 **`/analyze`** 設定。 如需詳細資訊，請參閱[ `/analyze` （程式碼分析）](../../build/reference/analyze-code-analysis.md)。

- 檔案或目錄是由適用于 Linux 的 Windows 子系統所建立、每個目錄的區分大小寫已啟用，而且指定的路徑或檔案大小寫不符合磁片上路徑或檔案的大小寫。

- 檔案、目錄或磁碟為唯讀。

- Visual Studio 或命令列工具沒有足夠的許可權可以讀取檔案或目錄。 例如，當專案檔案的擁有權與執行 Visual Studio 或命令列工具的進程不同時，就會發生這種情況。 有時候，您可以藉由以系統管理員身分執行 Visual Studio 或開發人員命令提示字元來修正此問題。

- 檔案控制代碼不足。 請關閉部分應用程式，再重新編譯。 在一般情況下，這種狀況並不常見。 不過，在實體記憶體有限的電腦上建置大型專案時，有可能會發生這種狀況。

## <a name="example"></a>範例

當標頭檔不 `"test.h"` 存在於來原始目錄或 include 搜尋路徑中時，下列範例會產生 C1083 錯誤。

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

如需如何在 IDE 中或在命令列上建立 C/c + + 專案，以及如何設定環境變數的詳細資訊，請參閱[專案和組建系統](../../build/projects-and-build-systems-cpp.md)。

## <a name="see-also"></a>另請參閱

- [MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)
