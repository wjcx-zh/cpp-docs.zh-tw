---
title: /FR、/Fr (建立 .Sbr 檔案)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 73642baba77a62cac531ae7b2842ec9953b338ec
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508698"
---
# <a name="fr-fr-create-sbr-file"></a>/FR、/Fr (建立 .Sbr 檔案)

建立 .sbr 檔案。

## <a name="syntax"></a>語法

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>備註

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。

在建置流程中，Microsoft 瀏覽資訊檔維護公用程式 (BSCMAKE) 會使用這些檔案建立 .BSC 檔案，用以顯示瀏覽資訊。

**/FR** 會建立具有完整符號資訊的 .sbr 檔案。

**/Fr** 會建立不含本機變數資訊的 .sbr 檔案。

若您未指定 `filename`，.sbr 檔案會取得與原始程式檔相同的基底名稱。

**/Fr** 已被取代，請改用 **/FR** 。 如需詳細資訊，請參閱 [Compiler Options Listed by Category](compiler-options-listed-by-category.md)中的＜已取代及移除的編譯器選項＞。

> [!NOTE]
>  請勿變更 .sbr 副檔名。 BSCMAKE 要求中繼檔必須具有該副檔名。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在瀏覽窗格中，依序選擇 [C/C++] 及 [瀏覽資訊]  屬性頁面。

1. 修改 [瀏覽資訊檔]  或 [啟用瀏覽資訊]  屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
