---
title: /std （指定語言標準版本）
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 03f7e095dc8b09b743d42cd6df0aaeb1a1dd3f02
ms.sourcegitcommit: e9568560cdb95e83a8fba1e9bca21ece910d20b7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52453907"
---
# <a name="std-specify-language-standard-version"></a>/std （指定語言標準版本）

啟用支援 c + + 語言功能，從指定版本的 c + + 語言標準。

## <a name="syntax"></a>語法

> / std:\[c++14\|c++17\|c + + 最新]

## <a name="remarks"></a>備註

**/Std**選項是可在 Visual Studio 2017 及更新版本。 它用來控制特定版本的 ISO c + + 程式設計語言啟用您的程式碼在編譯期間的標準功能。 此選項可讓您停用之某些新語言和程式庫功能的支援可能會中斷現有的程式碼符合特定版本的語言標準。 根據預設， **/std: c + + 14**指定，則會停用的語言和標準程式庫中的功能更新版本的 c + + 語言標準。 使用 **/std: c + + 17**來啟用 C + + 17 標準特有的功能和行為。 若要明確啟用的目前實作的編譯器和標準程式庫功能，針對下一步 的草稿標準，使用 **/std: c + + 最新**。

預設值 **/std: c + + 14**選項可讓一組 C + + 14 功能由 Visual c + + 編譯器實作。 編譯器和標準程式庫支援變更的功能或新的語言標準，除了一些 c++17 功能已經實作在舊版的 Visual c + + 編譯器中的較新版本，會停用此選項。 若要避免重大變更的 Visual Studio 2015 Update 2 起提供的功能已經拍攝的相依性的使用者，這些功能仍然可何時 **/std: c + + 14**指定選項：

- [規則附有括號內的初始清單](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [在範本 template 參數中的類型名稱](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [移除三併詞](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空間和列舉的屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字元常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

如需詳細資訊的 C + + 14 和 C + + 17 功能啟用時 **/std: c + + 14**會指定，請參閱[Visual c + + 語言一致性](../../visual-cpp-language-conformance.md)。

**/Std: c + + 17**選項會啟用整組 c++17 功能由 Visual c + + 編譯器實作。 此選項會對 C++ 標準中，在 C++17 之後推出但屬於進行中草稿及瑕疵更新版本的變更或新增功能，停用編譯器及標準程式庫支援。

**/Std: c + + 最新**選項可讓 post-c++17 語言和程式庫中的編譯器和程式庫目前實作的功能。 這些可能包括從 C + + 20 草稿及瑕疵更新 c + + 標準的 C + + 17，以及實驗的提案草稿標準未包含的功能。 如需支援的語言和程式庫功能的清單，請參閱 < [What's New for Visual c + +](../../what-s-new-for-visual-cpp-in-visual-studio.md)。 **/Std: c + + 最新**選項不會啟用保護功能 **/ experimental**參數，但可能必須啟用它們。

> [!IMPORTANT]
> 啟用的編譯器和程式庫功能 **/std: c + + 最新**會作為-是並不支援。 會受限於重大變更或移除，恕不另行通知。 作為預覽可能會出現在標準，下一版的語言功能，但標準是進行中的工作。 使用  **/std: c + + 17**最新的 ISO c + + 標準中使用的功能。

**/Std**作用中期間 c + + 編譯選項可以使用偵測[ \_MSVC\_LANG](../../preprocessor/predefined-macros.md)前置處理器巨集。 如需詳細資訊，請參閱 <<c0> [ 前置處理器巨集](../../preprocessor/predefined-macros.md)。

**/Std: c + + 14**並 **/std: c + + 最新**選項會在 Visual c + + 2015 Update 3 開始提供。 **/Std: c + + 17**選項是在 Visual c + + 2017 15.3 版開始提供。 如先前所述，某些 C + + 17 標準會啟用行為 **/std: c + + 14**選項，但所有其他 c++17 功能會啟用 **/std: c + + 17**。

> [!NOTE]
> Visual c + + 編譯器版本或更新層級，根據特定 C + + 14 或 C + + 17 功能可能未完全實作或完全符合標準時您所指定 **/std: c + + 14**或是 **/std: c + + 17**選項。 例如，Visual c + + 2017 RTM 編譯器不完全支援 C + + 14 符合標準`constexpr`，運算式 SFINAE 或 2 階段名稱查閱。 如需 Visual c + + 中的發行版本的 c + + 語言一致性的概觀，請參閱 < [Visual c + + 語言一致性](../../visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性**， **C/c + +**，**語言**。

1. 在  **c + + 語言標準**，選擇的語言標準，以支援從下拉式清單中的控制項，然後選擇**確定**或**套用**以儲存變更。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
