---
title: -C （前置處理期間保留註解） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs:
- C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20973969385d0b5c61872a12f4d0168420bc2eef
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713177"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (前置處理時保留註解)

在前置處理過程中保留註解。

## <a name="syntax"></a>語法

```
/C
```

## <a name="remarks"></a>備註

這個編譯器選項需要 **/E**， **/P**，或 **/EP**選項。

下列程式碼範例會顯示來源的程式碼註解。

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

此範例會產生下列輸出。

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **前置處理器**屬性頁。

1. 修改**保留註解**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/E （前置處理至 stdout）](../../build/reference/e-preprocess-to-stdout.md)
[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)
[/EP （前置處理至 stdout 不 #line 指示詞）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)