---
title: /std (指定語言標準版本)
description: MSVC 編譯器選項/std 指定編譯器所支援的 C 或 c + + 語言標準。
ms.date: 09/11/2020
f1_keywords:
- /std
- -std
- /std:c++14
- /std:c++17
- /std:c11
- /std:c17
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 82f37377dc223bfe3f5e578e1c7f390da91752a1
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075825"
---
# <a name="std-specify-language-standard-version"></a>`/std` (指定語言標準版本) 

從指定的 C 或 c + + 語言標準版本啟用支援的 C 和 c + + 語言功能。

## <a name="syntax"></a>語法

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**\
> **`/std:c11`**\
> **`/std:c17`**

## <a name="remarks"></a>備註

**`/std`** 選項可在 Visual Studio 2017 和更新版本中使用。 它是用來控制在程式碼的編譯期間啟用的特定版本 ISO C 或 c + + 程式設計語言標準功能。 此選項可讓您停用對特定語言和程式庫功能的支援：可能會中斷符合特定語言標準版本之現有程式碼的支援。

### <a name="c-standards-support"></a>C + + 標準支援

依預設， **`/std:c++14`** 會指定，以停用在較新版 c + + 語言標準中找到的語言和標準程式庫功能。 使用  **`/std:c++17`** 可啟用 c + + 17 標準特定功能和行為。 若要明確啟用目前已執行的編譯器和標準程式庫功能，建議用於下一個草稿標準，請使用 **`/std:c++latest`** 。 所有 c + + 20 功能都需要 **`/std:c++latest`** ; 當完成時， **`/std:c++20`** 將會啟用新的選項。

預設 **`/std:c++14`** 選項會啟用由 MSVC 編譯器所執行的一組 c + + 14 功能。 此選項會停用編譯器和標準程式庫對較新版本語言標準的變更或新功能的支援。 它不會停用舊版 MSVC 編譯器中已執行的一些 c + + 17 功能。 若要避免在 Visual Studio 2015 Update 2 之前，對已取得或之前的功能具有相依性之使用者的重大變更，當指定選項時，這些功能會保持啟用狀態 **`/std:c++14`** ：

- [`auto`使用括弧的規則-init 清單](https://wg21.link/n3922)

- [`typename` 在範本範本中參數](https://wg21.link/n4051)

- [移除三併詞](https://wg21.link/n4086)

- [命名空間和列舉程式的屬性](https://wg21.link/n4266)

- [u8 字元常值](https://wg21.link/n4267)

當您指定可供使用時，會啟用 c + + 14 和 c + + 17 功能的清單 **`/std:c++14`** 。 如需詳細資訊，請參閱 [Microsoft c + + 語言一致性表格](../../overview/visual-cpp-language-conformance.md)中的附注。

**`/std:c++17`** 選項會啟用 MSVC 編譯器所執行的一組完整的 c + + 17 功能。 此選項會針對 c + + 17 之後新增或變更的功能，停用編譯器和標準程式庫支援。 這包括 c + + 標準的工作草稿和瑕疵更新版本中的 C + + 17 變更。

**`/std:c++latest`** 選項會啟用目前在編譯器和程式庫中執行的 C + + 17 語言和程式庫功能。 這些功能可能包括 c + + 20 工作草稿的變更、c + + 17 未包含的瑕疵更新，以及 Draft 標準的實驗性提案。 如需支援的語言和程式庫功能清單，請參閱 [Visual C++ 的新功能](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 **`/std:c++latest`** 選項不會啟用參數所保護的功能 **`/experimental`** ，但可能需要啟用這些功能。

> [!IMPORTANT]
> 所啟用的編譯器和程式庫功能 **`/std:c++latest`** 代表可能出現在未來 c + + 標準中的功能，以及已核准的 c + + 20 功能。 未核准的功能會是中斷性變更或移除的項目 (恕不另行通知)，並且會以不變更原狀的基礎來提供。

**`/std`** 使用[ \_ MSVC \_ LANG](../../preprocessor/predefined-macros.md)預處理器宏可以偵測到 c + + 編譯期間生效的選項。 如需詳細資訊，請參閱 [前置處理器巨集](../../preprocessor/predefined-macros.md)。

**`/std:c++14`** 和 **`/std:c++latest`** 選項從 Visual Studio 2015 Update 3 開始提供。 **`/std:c++17`** 從 Visual Studio 2017 15.3 版開始，可以使用此選項。 如上所述，選項會啟用部分 c + + 17 標準行為 **`/std:c++14`** ，但會啟用所有其他 c + + 17 功能 **`/std:c++17`** 。 在完成執行之前，會啟用 c + + 20 功能 **`/std:c++latest`** 。

> [!NOTE]
> 視 MSVC 編譯器版本或更新層級而定，當您指定選項時，可能無法完全實行或完全符合 c + + 17 功能 **`/std:c++17`** 。 如需 Visual C++ by 發行版本中的 c + + 語言一致性總覽，請參閱 [Microsoft c + + 語言一致性表格](../../overview/visual-cpp-language-conformance.md)。

### <a name="c-standards-support"></a>C 標準支援

根據預設，當程式碼編譯為 C 時，MSVC 編譯器不符合特定 C 標準。 它採用數個 Microsoft 擴充功能來實行 ANSI C89，其中有些是 ISO C99 的一部分。 某些 Microsoft 擴充功能可以使用編譯器選項來停用 [`/Za`](za-ze-disable-language-extensions.md) ，但其他可以維持有效。 您無法指定嚴格的 C89 一致性。

從 Visual Studio 2019 版本16.8 開始，您可以 **`/std:c11`** **`/std:c17`** 針對編譯為 C 的程式碼指定或。這些選項會指定與 ISO C11 和 ISO C17 對應的一致性模式。 因為需要新的預處理器來支援這些標準，所以 **`/std:c11`** 和 **`/std:c17`** 編譯器選項 [`/Zc:preprocessor`](zc-preprocessor.md) 會自動設定選項。 如果您想要使用傳統 (舊版) 預處理器的 C11 或 C17，您必須 **`/Zc:preprocessor-`** 明確地設定編譯器選項。 設定 **`/Zc:preprocessor-`** 選項可能會導致非預期的行為，不建議使用。

> [!NOTE]
> 在發行時，最新的 Windows SDK 和 UCRT 程式庫尚未支援 C11 和 C17 程式碼。 需要 Windows SDK 和 UCRT 的發行前版本。 如需詳細資訊和安裝指示，請參閱 [Visual Studio 中的安裝 C11 和 C17 支援](../../overview/install-c17-support.md)。

當您指定 **`/std:c11`** 或時 **`/std:c17`** ，MSVC 會支援 C11 和 C17 的所有必要功能。 編譯器選項會啟用對這些功能的支援：

- **`_Pragma`**

- **`restrict`**

- **`_Noreturn`** 和 \<stdnoreturn.h>

- **`_Alignas`**、 **`_Alignof`** 和 \<stdalign.h>

- **`_Generic`** 和 \<tgmath.h>

- **`_Static_assert`**

當您的原始程式檔具有 *`.c`* 副檔名，或當您指定編譯器選項時，IDE 會使用 IntelliSense 的 C 設定和程式碼反白顯示 [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) 。 目前，IntelliSense 醒目提示只適用于關鍵字，而不是標準標頭所引進的宏。

由於 C17 主要是錯誤修正的 ISO C11 版本，因此 C11 的 MSVC 支援已經包含所有相關的瑕疵報告。 目前，除了宏之外，C11 和 C17 版本之間沒有任何差異 `__STDC_VERSION__` 。 它會 `201112L` 針對 C11 和 C17 展開至 `201710L` 。

編譯器不支援 ISO C11 的任何選用功能。 這些 C11 的其中幾個選擇性功能是 C99 的必要功能，MSVC 尚未針對架構的理由執行這些功能。 您可以使用功能測試宏（例如） `__STDC_NO_VLA__` 來偵測個別功能的編譯器支援層級。 如需有關 C 特定預先定義宏的詳細資訊，請參閱 [預先定義的宏](../../preprocessor/predefined-macros.md)。

- Visual Studio 2019 16.8 版版本中沒有符合的多執行緒、不可部分完成或複數支援。

- `aligned_alloc` 因為 Windows 堆積的執行，所以遺漏了支援。 替代方法是使用 [`_aligned_malloc`](../../c-runtime-library/reference/aligned-malloc.md) 。

- 目前尚未針對提供 DR 400 支援 `realloc` ，因為這項變更會中斷 ABI。

- 未規劃 (VLA) 支援的可變長度陣列。 變數長度陣列的效率通常比可比較的固定大小陣列低。 相較于當安全且安全地執行時，與相等的堆積記憶體配置相比，它們也是沒有效率的。 Vla 提供相當於的攻擊媒介 `gets()` ，已被取代並計畫移除。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] ****、[C/C++] ****、[語言]****。

1. 在 c **+ + 語言標準** (或 c **語言標準**) 中，從下拉式控制項選擇要支援的語言標準，然後選擇 **[確定]** **或 [** 套用] 以儲存變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
