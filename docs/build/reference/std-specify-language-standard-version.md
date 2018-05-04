---
title: -std （指定語言 Standard 版本） |Microsoft 文件
ms.custom: ''
ms.date: 11/16/2017
ms.topic: reference
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs:
- C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fed80f0f9763b7e988c40a9d9f38f4e0f18eeb1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="std-specify-language-standard-version"></a>/std （指定語言 Standard 版本）

啟用支援 c + + 語言功能，從指定版本的 c + + 語言標準。

## <a name="syntax"></a>語法

> /std: [c + + 14 | c + + 17 | c + + 最新]

## <a name="remarks"></a>備註

**/Std**選項用來控制特定版本的 ISO c + + 程式設計語言程式碼的編譯期間啟用標準的功能。 此選項可讓您停用可能會中斷現有的程式碼語言的特定版本符合標準的某些新語言和程式庫功能的支援。 根據預設， **/std:c + + 14**指定，則會停用語言和標準程式庫中的功能更新版本的 c + + 語言標準。 使用 **/std:c + + 17**啟用 C + + 17 標準特定功能和行為。 若要明確啟用最新支援的編譯器和標準程式庫功能，請使用 **/std:c + + 最新**。

預設值 **/std:c + + 14**選項可讓 C + + 14 功能由 Visual c + + 編譯器實作的集合。 編譯器和標準程式庫支援已變更的功能或新的語言標準，除了某些 C + + 17 功能已實作在舊版的 Visual c + + 編譯器中的較新版本中，會停用此選項。 若要避免的重大變更的使用者已採取的相依性從 Visual Studio 2015 Update 2 開始可用的功能，這些功能仍會啟用時 **/std:c + + 14**指定選項：

- [規則附有括號內的初始清單](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [範本參數中的類型名稱](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [移除三併詞](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空間和列舉值的屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字元常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

如需詳細資訊的 C + + 14 和 C + + 17 功能啟用時 **/std:c + + 14**已指定，請參閱附註中的[Visual c + + 語言一致性](../../visual-cpp-language-conformance.md)。
  
**/Std:c + + 17**選項可讓一組完整的 C + + 17 功能，Visual c + + 編譯器實作。 此選項會對 C++ 標準中，在 C++17 之後推出但屬於進行中草稿及瑕疵更新版本的變更或新增功能，停用編譯器及標準程式庫支援。  
  
**/Std:c + + 最新**選項可讓 Visual c + + 最追蹤所實作的 c + + 語言和程式庫功能組 C + + 20 工作草稿和缺失最新更新的 c + + 標準未包含在 C + + 17。 使用這個參數來取得，使用 post 要求的 C + + 17 語言編譯器和標準程式庫所支援的功能。 如需支援的語言和程式庫功能的清單，請參閱[What's New for Visual c + +](../../what-s-new-for-visual-cpp-in-visual-studio.md)。 **/Std:c + + 最新**選項不會啟用受保護的功能 **/ 實驗**切換。  
  
**/Std**作用中期間 c + + 編譯選項可以偵測到使用[ \_MSVC\_LANG](../../preprocessor/predefined-macros.md)前置處理器巨集。 如需詳細資訊，請參閱[前置處理器巨集](../../preprocessor/predefined-macros.md)。

**/Std:c + + 14**和 **/std:c + + 最新**選項會從開始使用 Visual c + + 2015 Update 3。 **/Std:c + + 17**選項是從開始使用 Visual c + + 2017 15.3 版本。 如先前所述，某些 C + + 17 標準的啟用行為 **/std:c + + 14**選項，但所有其他 C + + 17 功能會啟用 **/std:c + + 17**。
  
> [!NOTE]
> 根據 Visual c + + 編譯器版本或更新等級，某些 C + + 14 或 C + + 17 功能可能未完全實作或完全符合您指定當 **/std:c + + 14**或 **/std:c + + 17**選項。 例如，Visual c + + 2017 RTM 編譯器不完全支援 C + + 14 標準`constexpr`，運算式 SFINAE 或 2 階段名稱查閱。 如需 Visual c + + 中的發行版本的 c + + 語言一致性的概觀，請參閱[Visual c + + 語言一致性](../../visual-cpp-language-conformance.md)。 
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**組態屬性**， **C/c + +**，**語言**。  
  
3.  在**c + + 語言標準**，選擇了語言標準，以支援從下拉式清單控制項，然後選擇 **確定**或**套用**以儲存變更。  
  
## <a name="see-also"></a>另請參閱  
  
[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)   
