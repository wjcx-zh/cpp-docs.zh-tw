---
title: /std (指定語言標準版本)
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 52aa99cf5bdf7ddcf83a8423b946a03d2ca95d2d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079259"
---
# <a name="std-specify-language-standard-version"></a>/std (指定語言標準版本)

從指定的 C++ 語言標準版本啟用支援的 C++ 語言功能。

## <a name="syntax"></a>語法

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>備註

Visual Studio 2017 及更新版本有提供 **/std** 選項。 該選項會用來控制特定版本的 ISO C++ 程式設計語言標準功能，而這些功能會在編譯您的程式碼時啟用。 此選項可讓您停用某些新語言和程式庫功能的支援，因為這些功能可能會破壞符合特定語言標準版本的現有程式碼。 根據預設，系統會指定 **/std:c++14**，以停用較新版 C++ 語言標準中找到的語言和標準程式庫功能。 使用 **/std:c++17** 可啟用 C++ 17 標準特有的功能和行為。 若要明確啟用目前實作的編譯器和標準程式庫功能以用於下一個草稿標準，請使用 **/std:c++latest**。 所有 c + + 20 功能都需要 **/std： C + + 最新版本**;完成執行時，將會啟用新的 **/std： c + + 20**選項。

預設的 **/std:c++14** 選項能啟用 MSVC 編譯器實作的一組 C++14 功能。 針對最近語言標準版本中的已變更或新建功能，此選項能停用編譯器和標準程式庫支援，但一些已實作在舊版 MSVC 編譯器中的 C++17 功能除外。 若使用者已經依賴使用自 Visual Studio 2015 Update 2 起開始提供的功能，為避免對使用者造成中斷性變更，指定 **/std:c++14** 選項時，這些功能仍可使用：

- [自動化規則，附有以大括號括住的初始清單](https://wg21.link/n3922)

- [範本參數中的類型名稱](https://wg21.link/n4051)

- [移除三併詞](https://wg21.link/n4086)

- [命名空間和列舉程式的屬性](https://wg21.link/n4266)

- [u8 字元常值](https://wg21.link/n4267)

如需在 **/std**時啟用 c + + 14 和 c + + 17 功能的其他資訊，請參閱[Microsoft C++語言一致性表格](../../overview/visual-cpp-language-conformance.md)中的附注。

**/std:c++17** 選項能啟用 MSVC 編譯器實作的一整組 C++17 功能。 此選項會對 C++ 標準中，在 C++17 之後推出但屬於進行中草稿及瑕疵更新版本的變更或新增功能，停用編譯器及標準程式庫支援。

**/std:c++latest** 選項可啟用目前在編譯器和程式庫中實作的 post-C++17 語言和程式庫功能。 這些功能可能包括 C++20 工作草稿及 C++ 標準的瑕疵更新 (不包含在 C++17 中)，還有草稿標準的實驗性提案。 如需支援的語言和程式庫功能清單，請參閱 [Visual C++ 的新功能](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 **/std:c++latest** 選項不會啟用由 **/experimental** 參數保護的功能，但您可能必須啟用這些功能。

> [!IMPORTANT]
> 由 **/std:c++latest** 啟用的編譯器和程式庫功能代表可能出現在未來 C++ 標準的功能，也是代表已核准的 C++20 功能。 未核准的功能會是中斷性變更或移除的項目 (恕不另行通知)，並且會以不變更原狀的基礎來提供。

使用MSVC[LANG\_ 前置處理器巨集，可偵測到 C++ 編譯期間生效的 \_/std](../../preprocessor/predefined-macros.md) 選項。 如需詳細資訊，請參閱 [前置處理器巨集](../../preprocessor/predefined-macros.md)。

**/std:c++14** 和 **/std:c++latest** 選項會在 Visual Studio 2015 Update 3 中開始提供。 **/std:c++17** 選項會在 Visual Studio 2017 15.3 版中開始提供。 如先前所述，某些 C++17 標準行為會由 **/std:c++14** 選項啟用，但所有其他 C++17 功能都會由 **/std:c++17**啟用。 C++20 功能會由 **/std:latest** 啟用，直到實作完成為止。

> [!NOTE]
> 視 MSVC 編譯器版本或更新層級而定，當您指定 **/std:c++17** 選項時，C++17 功能可能未完全實作或完全一致。 如需 Visual C++ by C++發行版本中語言一致性的總覽，請參閱[Microsoft C++語言一致性表格](../../overview/visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性]、[C/C++]、[語言]。

1. 在 [C++語言標準] 中，從下拉式清單中選擇要支援的語言標準，然後選擇[確定] 或 [套用] 來儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
