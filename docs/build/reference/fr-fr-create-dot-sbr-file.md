---
title: -FR、-Fr （建立）。Sbr 檔案） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs:
- C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5691a87f7350c7816e8ddb58d5591e16cc18189
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709596"
---
# <a name="fr-fr-create-sbr-file"></a>/FR、/Fr (建立 .Sbr 檔案)

建立 .sbr 檔案。

## <a name="syntax"></a>語法

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>備註

在建置流程中，Microsoft 瀏覽資訊檔維護公用程式 (BSCMAKE) 會使用這些檔案建立 .BSC 檔案，用以顯示瀏覽資訊。

**/FR** 會建立具有完整符號資訊的 .sbr 檔案。

**/Fr** 會建立不含本機變數資訊的 .sbr 檔案。

若您未指定 `filename`，.sbr 檔案會取得與原始程式檔相同的基底名稱。

**/Fr** 已被取代，請改用 **/FR** 。 如需詳細資訊，請參閱 [Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md)中的＜已取代及移除的編譯器選項＞。

> [!NOTE]
>  請勿變更 .sbr 副檔名。 BSCMAKE 要求中繼檔必須具有該副檔名。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 在瀏覽窗格中，依序選擇 [C/C++] 及 [瀏覽資訊]  屬性頁面。

1. 修改 [瀏覽資訊檔]  或 [啟用瀏覽資訊]  屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>。

## <a name="see-also"></a>另請參閱

[輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[指定路徑名稱](../../build/reference/specifying-the-pathname.md)