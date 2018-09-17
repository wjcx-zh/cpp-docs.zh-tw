---
title: -Gy （啟用函式階層連結） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09faa1a1d2b6743b7fce31af32ba4fe1572b592e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704999"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (啟用函式階層連結)

允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。

## <a name="syntax"></a>語法

```
/Gy[-]
```

## <a name="remarks"></a>備註

連結器會需要為來排除或排序 DLL 或.exe 檔案中的個別函式的 Comdat 函式個別封裝。

您可以使用連結器選項[/OPT （最佳化）](../../build/reference/opt-optimizations.md)的.exe 檔案中排除未參考的封裝函式。

您可以使用連結器選項[/ORDER （Put 函式的順序）](../../build/reference/order-put-functions-in-order.md)来包含的封裝函式中指定的順序中的.exe 檔案。

如果它們具現化呼叫，一律會封裝內嵌函式 (發生，例如，如果內嵌已關閉或需要為函式位址)。 此外，自動封裝在類別宣告中定義的 c + + 成員函式;其他函式則不會，並選取此選項需要將它們編譯為封裝函式。

> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)選項，用於編輯後繼續，會自動設定 **/Gy**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改**啟用函式層級連結**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)