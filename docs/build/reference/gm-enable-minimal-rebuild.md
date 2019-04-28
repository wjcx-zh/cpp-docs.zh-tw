---
title: /Gm (啟用最少重建)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292060"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (啟用最少重建)

已取代。 啟用最少重建，其可判定是否需要重新編譯包含已變更 C++ 類別定義 (儲存於標頭 (.h) 檔) 的 C++ 原始程式檔。

## <a name="syntax"></a>語法

```
/Gm
```

## <a name="remarks"></a>備註

**/Gm**已被取代。 它可能不會觸發組建，以對特定種類的標頭檔的變更。 您可能會安全地移除此選項，從您的專案。 若要改善建置時間，我們建議使用先行編譯標頭，並增量和平行建置選項改為。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**一節[依分類排列的編譯器選項](compiler-options-listed-by-category.md)。

編譯器在第一次編譯期間，會在專案的 .idb 檔中，儲存原始程式檔與類別定義之間的相依性資訊  （相依性資訊會告知哪個原始程式檔是取決於哪個類別定義，及位於哪個.h 檔定義中）。後續編譯會使用儲存在.idb 檔中的資訊來判斷是否原始程式檔需要重新編譯，即使它包含已修改的.h 檔案。

> [!NOTE]
> 最少重建依賴於包含檔之間未變更的類別定義。 對於專案來說，類別定義必須是全域的 (給定類別應該只有一個定義)，這是因為 .idb 檔中的相依性資訊是針對整個專案建立的。 如果專案中類別具有多個定義，請停用最少重建。

由於 incremental linker 不支援使用包含在.obj 檔案中的 Windows 中繼資料[/ZW （Windows 執行階段編譯）](zw-windows-runtime-compilation.md)選項時， **/Gm**選項與不相容 **/ZW**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **產生程式碼**屬性頁。

1. 修改**啟用最少重建**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
