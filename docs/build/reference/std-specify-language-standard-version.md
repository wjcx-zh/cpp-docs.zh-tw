---
title: /std (指定語言標準版本)
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: eef44858064b89d4a836c80a48552599bceec242
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223820"
---
# <a name="std-specify-language-standard-version"></a>`/std`（指定語言標準版本）

從指定的 C++ 語言標準版本啟用支援的 C++ 語言功能。

## <a name="syntax"></a>語法

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**]

## <a name="remarks"></a>備註

**`/std`** Visual Studio 2017 和更新版本提供選項。 它可用來控制編譯器代碼編譯期間所啟用的版本特定 ISO c + + 程式設計語言標準功能。 此選項可讓您停用特定新語言和程式庫功能的支援：可能會破壞符合特定語言版本的現有程式碼。 預設 **`/std:c++14`** 會指定，這會停用在較新版本的 c + + 語言標準中找到的語言和標準程式庫功能。 使用 **`/std:c++17`** 來啟用 c + + 17 標準特有的功能和行為。 若要明確啟用目前執行的編譯器和標準程式庫功能，建議用於下一個草稿標準，請使用 **`/std:c++latest`** 。 所有 c + + 20 功能都需要 **`/std:c++latest`** ; 當完成執行時， **`/std:c++20`** 將會啟用新的選項。

預設 **`/std:c++14`** 選項會啟用由 MSVC 編譯器所實作為 c + + 14 功能的集合。 此選項會停用編譯器和標準程式庫對較新語言版本中變更或新功能的支援。 它不會停用某些已在舊版 MSVC 編譯器中實作為的 c + + 17 功能。 為避免已針對 Visual Studio 2015 Update 2 中的可用功能取得相依性的使用者進行重大變更，當指定選項時，這些功能仍會啟用 **`/std:c++14`** ：

- [`auto`使用括弧的規則-init-清單](https://wg21.link/n3922)

- [`typename`在範本範本-參數](https://wg21.link/n4051)

- [移除三併詞](https://wg21.link/n4086)

- [命名空間和列舉程式的屬性](https://wg21.link/n4266)

- [u8 字元常值](https://wg21.link/n4267)

當您指定可供使用時，會啟用 c + + 14 和 c + + 17 功能的清單 **`/std:c++14`** 。 如需詳細資訊，請參閱[Microsoft c + + 語言一致性表格](../../overview/visual-cpp-language-conformance.md)中的附注。

**`/std:c++17`** 選項會啟用由 MSVC 編譯器所執行的一組完整的 c + + 17 功能。 這個選項會停用 c + + 17 之後新增或變更之功能的編譯器和標準程式庫支援。 其中包括 c + + 標準的工作草稿和瑕疵更新版本中的 C + + 17 後變更。

**`/std:c++latest`** 選項會啟用目前在編譯器和程式庫中實作為 C + + 17 語言和程式庫功能。 這些功能可能包括 c + + 20 工作草稿的變更、不包含在 c + + 17 中的瑕疵更新，以及草稿標準的實驗性提案。 如需支援的語言和程式庫功能清單，請參閱 [Visual C++ 的新功能](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 **`/std:c++latest`** 選項不會啟用參數所保護的功能 **`/experimental`** ，但可能需要啟用它們。

> [!IMPORTANT]
> 所啟用的編譯器和程式庫功能 **`/std:c++latest`** 代表未來的 c + + 標準中可能出現的功能，以及已核准的 c + + 20 功能。 未核准的功能會是中斷性變更或移除的項目 (恕不另行通知)，並且會以不變更原狀的基礎來提供。

**`/std`** 使用[ \_ MSVC \_ LANG](../../preprocessor/predefined-macros.md)預處理器宏，可以偵測 c + + 編譯期間生效的選項。 如需詳細資訊，請參閱 [前置處理器巨集](../../preprocessor/predefined-macros.md)。

**`/std:c++14`** **`/std:c++latest`** 從 Visual Studio 2015 Update 3 開始提供和選項。 **`/std:c++17`** 從 Visual Studio 2017 15.3 版開始提供此選項。 如先前所述，選項會啟用某些 c + + 17 標準行為 **`/std:c++14`** ，但是所有其他 c + + 17 功能都是由啟用 **`/std:c++17`** 。 在完成執行之前，會啟用 c + + 20 功能 **`/std:c++latest`** 。

> [!NOTE]
> 視 MSVC 編譯器版本或更新層級而定，當您指定選項時，可能無法完全執行或完全符合 c + + 17 功能 **`/std:c++17`** 。 如需依發行版本 Visual C++ 之 c + + 語言一致性的總覽，請參閱[Microsoft c + + 語言一致性表格](../../overview/visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] ****、[C/C++] ****、[語言]****。

1. 在 [C++語言標準]**** 中，從下拉式清單中選擇要支援的語言標準，然後選擇[確定]**** 或 [套用]**** 來儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
