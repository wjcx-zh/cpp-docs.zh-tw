---
title: /Gm (啟用最少重建)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439638"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (啟用最少重建)

已被取代。 啟用最少重建，其可判定是否需要重新編譯包含已變更 C++ 類別定義 (儲存於標頭 (.h) 檔) 的 C++ 原始程式檔。

## <a name="syntax"></a>語法

```
/Gm
```

## <a name="remarks"></a>備註

**/Gm**已被取代。 它可能不會針對特定種類的標頭檔變更觸發組建。 您可以從專案中安全地移除此選項。 若要改善組建時間，我們建議您改為使用先行編譯的標頭和累加式和平行組建選項。 如需已被取代的編譯器選項清單，請參閱[依分類列出的編譯器選項](compiler-options-listed-by-category.md)中的**已被取代和移除的編譯器選項**一節。

編譯器在第一次編譯期間，會在專案的 .idb 檔中，儲存原始程式檔與類別定義之間的相依性資訊 (相依性資訊會告知哪個原始程式檔與哪個類別定義相依，以及該定義位於哪個 .h 檔)。後續編譯會使用儲存在 .idb 檔中的資訊，來判定是否需要編譯原始程式檔，即使其包括已修改的 .h 檔。

> [!NOTE]
> 最少重建依賴於包含檔之間未變更的類別定義。 對於專案來說，類別定義必須是全域的 (給定類別應該只有一個定義)，這是因為 .idb 檔中的相依性資訊是針對整個專案建立的。 如果專案中類別具有多個定義，請停用最少重建。

由於增量連結器不支援使用[/ZW （Windows 執行階段編譯）](zw-windows-runtime-compilation.md)選項的 .obj 檔案中包含的 Windows 中繼資料，因此 **/Gm**選項與 **/ZW**不相容。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在 [ **C/C++**  > 程式**代碼產生**] 屬性頁中選取 [設定**屬性**] > 。

1. 修改 [**啟用最少重建**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
