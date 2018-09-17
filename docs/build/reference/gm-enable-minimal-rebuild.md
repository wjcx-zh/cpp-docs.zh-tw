---
title: -Gm （啟用最少重建） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs:
- C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f18881e79a3f82941f04dccbde210b2c62dcbca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725760"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (啟用最少重建)

啟用最少重建，其可判定是否需要重新編譯包含已變更 C++ 類別定義 (儲存於標頭 (.h) 檔) 的 C++ 原始程式檔。

## <a name="syntax"></a>語法

```
/Gm
```

## <a name="remarks"></a>備註

編譯器在第一次編譯期間，會在專案的 .idb 檔中，儲存原始程式檔與類別定義之間的相依性資訊  （相依性資訊會告知哪個原始程式檔是取決於哪個類別定義，及位於哪個.h 檔定義中）。後續編譯會使用儲存在.idb 檔中的資訊來判斷是否原始程式檔需要重新編譯，即使它包含已修改的.h 檔案。

> [!NOTE]
>  最少重建依賴於包含檔之間未變更的類別定義。 對於專案來說，類別定義必須是全域的 (給定類別應該只有一個定義)，這是因為 .idb 檔中的相依性資訊是針對整個專案建立的。 如果專案中類別具有多個定義，請停用最少重建。

由於 incremental linker 不支援使用包含在.obj 檔案中的 Windows 中繼資料[/ZW （Windows 執行階段編譯）](../../build/reference/zw-windows-runtime-compilation.md)選項時， **/Gm**選項與不相容 **/ZW**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改**啟用最少重建**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)