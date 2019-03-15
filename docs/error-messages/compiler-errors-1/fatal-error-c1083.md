---
title: 嚴重錯誤 C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 522bc4a36be59d4e2c9425e50b1238eb9f4aba61
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822193"
---
# <a name="fatal-error-c1083"></a>嚴重錯誤 C1083

> 無法開啟*filetype*檔案: '*檔案*':*訊息*

找不到它所需要的檔案時，編譯器會產生 C1083 錯誤。 有許多可能的原因造成此錯誤。 不正確的 include 搜尋路徑或遺失或命名標頭檔的最常見的原因，但其他檔案類型和問題也可能導致 C1083。 以下是一些常見的原因為何，編譯器會產生這個錯誤。

## <a name="the-specified-file-name-is-wrong"></a>指定的檔案名稱錯誤

檔案名稱可能輸入錯誤。 例如，套用至物件的

`#include <algorithm.h>`

可能沒有找到您要的檔案。 大部分的 c + + 標準程式庫標頭檔並沒有.h 副檔名。 \<演算法 > 標頭會找不到由此`#include`指示詞。 若要修正此問題，確認正確的檔案名稱輸入，如此範例所示：

`#include <algorithm>`

某些 C 執行階段程式庫標頭位於標準 Include 目錄的子目錄中。 例如，若要包含 sys/types.h>，您必須包含 sys 子目錄名稱中的`#include`指示詞：

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>檔案未包含在 include 搜尋路徑

編譯器無法使用 `#include` 或 `#import` 指示詞中指出的搜尋規則來找到檔案。 例如，當標頭檔名稱是用引號括住，

`#include "myincludefile.h"`

這會告訴編譯器尋找第一次，包含原始程式檔的相同目錄中的檔案，並再查詢指定在建置環境的其他位置。 如果引號中含有絕對路徑，則編譯器只會在該位置尋找檔案。 如果引號中含有相對路徑，則編譯器會在來源目錄相對的目錄中尋找檔案。

如果名稱括在括弧中，

`#include <stdio.h>`

編譯器會依循由建置環境中，定義搜尋路徑 **/I**編譯器選項 **/X**編譯器選項，而**INCLUDE**環境變數。 如需詳細資訊，包括用來尋找檔案的搜尋順序有關的特定詳細資料請參閱 < [#include 指示詞 （C/c + +）](../../preprocessor/hash-include-directive-c-cpp.md)並[#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。

如果您的 include 檔案是相對於您的來源目錄，另一個目錄中，而且您使用中的相對路徑您 include 指示詞，您必須使用雙引號括住，而非角括弧。 比方說，如果您的標頭檔 myheader.h 專案來源名為標頭的子目錄中，然後此範例中將找不到檔案並造成 C1083:

`#include <headers\myheader.h>`

不過，這個範例才能運作：

`#include "headers\myheader.h"`

相對路徑也可以搭配 include 搜尋路徑上的目錄。 如果您新增至目錄**INCLUDE**環境變數，或者您**Include 目錄**在 Visual Studio 中的路徑不也會將路徑的一部分加入 include 指示詞。 比方說，如果您的標頭是位於 \path\example\headers\myheader.h，而且您加入至 \path\example\headers\ 您**Include 目錄**路徑，在 Visual Studio 中，但您`#include`指示詞是指做為檔案

`#include <headers\myheader.h>`

然後如果找不到檔案。 使用正確的路徑，相對於包含搜尋路徑中指定的目錄。 在此範例中，您可以將變更包含搜尋路徑 \path\example\,或移除 headers\ 路徑區段從`#include`指示詞。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 Vcpkg

如果您嘗試將協力廠商程式庫設定為組建的一部分時，您會看到此錯誤，請考慮使用[Vcpkg](../../vcpkg.md)，Visual c + + 套件管理員安裝及建置程式庫。 Vcpkg 支援大量且不斷成長[協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並設定所有組態屬性和相依性所需的建置成功，為您專案的一部分。 如需詳細資訊，請參閱相關[Visual c + + 部落格](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)張貼。

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>此檔案會在您的專案，但不是包含搜尋路徑

即使當標頭檔所示**方案總管 中**專案的一部分，檔案才找得到編譯器時參考這些由`#include`或`#import`來源中的指示詞檔案，並位於包含搜尋路徑。 不同類型的組建可能會使用不同的搜尋路徑。 **/X**編譯器選項可以用來將目錄排除包含搜尋路徑。 這樣可讓不同的組建使用同名但存放在不同目錄下的 Include 檔案。 這是除了使用前置處理器命令進行條件式編譯以外的另一種作法。 如需詳細資訊 **/X**編譯器選項，請參閱[/X （忽略標準 Include 路徑）](../../build/reference/x-ignore-standard-include-paths.md)。

若要修正此問題，請修正編譯器用來搜尋包含或匯入之檔案的路徑。 新的專案會使用預設值會包含搜尋路徑。 您可能必須修改包含搜尋路徑，以加入您專案的目錄。 如果您在命令列上編譯，請將路徑加入至**INCLUDE**環境變數或 **/I**編譯器選項以指定檔案的路徑。

若要在 Visual Studio 中設定 include 目錄路徑，開啟專案的**屬性頁** 對話方塊。 選取  **VC + + 目錄**下方**組態屬性**左的窗格中，然後編輯**Include 目錄**屬性。 如需有關在 Visual Studio 中編譯器所搜尋的每位使用者及每個專案目錄的詳細資訊，請參閱[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)。 如需詳細資訊 **/I**編譯器選項，請參閱[/I （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md)。

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>命令列包含或 LIB 環境未設定

在命令列叫用編譯器時，通常會使用環境變數指定搜尋路徑。 如果所描述的搜尋路徑**INCLUDE**或是**LIB**未正確設定環境變數，可以產生 C1083 錯誤。 我們強烈建議使用開發人員命令提示字元捷徑設定基本的環境，供命令列組建。 如需詳細資訊，請參閱 <<c0> [ 建置 C/c + + 命令列上](../../build/building-on-the-command-line.md)。 如需如何使用環境變數的詳細資訊，請參閱[How to:在組建中使用環境變數](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)。

## <a name="the-file-may-be-locked-or-in-use"></a>檔案可能已鎖定或在使用中

如果您使用另一個程式來編輯，或存取檔案，它可能會有鎖定的檔案。 請嘗試關閉其他程式中的檔案。 有時候另一個程式都可以是 Visual Studio 本身，如果您使用的平行編譯選項。 如果關閉平行建置選項會消失，錯誤，則這是問題。 其他平行建置系統也可以有此問題。 請小心設定檔案和專案的相依性，因此建置順序正確無誤。 在某些情況下，請考慮建立中繼的專案，以強制執行常見的檔案可能由多個專案建置的組建相依性順序。 有時候防毒程式暫時鎖定最近變更掃描的檔案。 可能的話，請考慮您專案的組建目錄排除防毒掃描程式。

## <a name="the-wrong-version-of-a-file-name-is-included"></a>包含錯誤的檔案名稱版本

C1083 錯誤也可能表示包含了錯誤版本的檔案。 包含錯誤檔案版本的例子像是，組建包含的檔案在其 `#include` 指示詞中參考了該組建不適用的標頭檔。 例如，某些檔案可能只適用於 x86 建置，或偵錯組建。 找不到標頭檔時，編譯器會產生 C1083 錯誤。 若要修正這個問題，請使用正確的檔案，而不是將標頭檔或目錄加入至組建中。

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>先行編譯標頭檔未經先行編譯

當專案已設定為使用先行編譯標頭檔時，必須已建立相關的 .pch 檔案，才能編譯用到標頭內容的檔案。 例如，在新專案的專案目錄中會自動建立 stdafx.cpp 檔案。 請先編譯該檔案以建立先行編譯標頭檔  在標準的建置程序設計中，這會自動完成。 如需詳細資訊，請參閱 <<c0> [ 建立先行編譯標頭檔](../../build/creating-precompiled-header-files.md)。

## <a name="additional-causes"></a>其他原因

- 您已安裝的 SDK 或協力廠商程式庫，但您尚未 SDK 後開啟新的開發人員命令提示字元視窗，或安裝程式庫。 如果 SDK 或文件庫會將檔案加入**INCLUDE**路徑，您可能需要開啟新的開發人員命令提示字元視窗來挑選這些環境變數的變更。

- 檔案使用 managed 程式碼，但編譯器選項 **/clr**未指定。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

- 編譯檔案使用不同 **/analyze**編譯器選項設定與用來先行編譯標頭。 當專案的標頭中都會先行編譯時，全都應該使用相同 **/analyze**設定。 如需詳細資訊，請參閱 [/analyze (程式碼分析)](../../build/reference/analyze-code-analysis.md)。

- 檔案或目錄已建立的 Windows 子系統適用於 Linux、 啟用每個目錄區分大小寫時，和指定的路徑或檔案大小寫不符的路徑或磁碟上的檔案的大小寫。

- 檔案、目錄或磁碟為唯讀。

- Visual Studio 或命令列工具並沒有足夠的權限來讀取檔案或目錄。 這種情形，例如，當專案檔具有不同的擁有權，比執行 Visual Studio 或命令列工具的處理序。 有時可以修正此問題，以系統管理員身分執行 Visual Studio 或開發人員命令提示字元。

- 檔案控制代碼不足。 請關閉部分應用程式，再重新編譯。 在一般情況下，這種狀況並不常見。 不過，在實體記憶體有限的電腦上建置大型專案時，有可能會發生這種狀況。

## <a name="example"></a>範例

下列範例會產生 C1083 錯誤時的標頭檔`"test.h"`來源目錄中，或在 include 搜尋路徑上不存在。

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

如需如何建置 C/c + + 專案，在 IDE 中或命令列上的相關資訊和設定環境變數的詳細資訊，請參閱[的專案和組建系統](../../build/projects-and-build-systems-cpp.md)。

## <a name="see-also"></a>另請參閱

- [MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)
