---
title: /C (前置處理時保留註解)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: 6d0cf8e5f628f3f5301f54d7c853bfc2ab63cb7e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988364"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (前置處理時保留註解)

在前置處理過程中保留註解。

## <a name="syntax"></a>語法

```
/C
```

## <a name="remarks"></a>備註

這個編譯器選項需要 **/e**、 **/p**或 **/EP**選項。

下列程式碼範例會顯示原始程式碼批註。

```cpp
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

這個範例會產生下列輸出。

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] 資料夾。

1. 按一下 [**預處理器**] 屬性頁。

1. 修改 [**保留批註**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/E (前置處理至 stdout)](e-preprocess-to-stdout.md)<br/>
[/P (前置處理至檔案)](p-preprocess-to-a-file.md)<br/>
[/EP (前置處理至 stdout 不加 #line 指示詞)](ep-preprocess-to-stdout-without-hash-line-directives.md)
