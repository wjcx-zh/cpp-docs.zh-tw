---
title: /U、/u (取消定義符號)
description: 使用 Microsoft C/c + + 編譯器/U 和/u 選項來取消預處理器符號的定義。
ms.date: 09/03/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 78effabba2fa72e5ab7f2dfc6ef91f22383b063f
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609202"
---
# <a name="u-u-undefine-symbols"></a>/U、/u (取消定義符號)

**`/U`** 編譯器選項會取消指定指定的預處理器符號。 **`/u`** 編譯器選項會取消定義編譯器所定義的 Microsoft 特定符號。

## <a name="syntax"></a>語法

> **`/U`**\[ ]*符號*\
> **`/u`**

## <a name="arguments"></a>引數

*象徵*<br/>
要取消定義的預處理器符號。

## <a name="remarks"></a>備註

和選項都不能取消定義使用指示詞所 **`/U`** **`/u`** 建立的符號 **`#define`** 。

**`/U`** 選項可以取消定義先前使用選項定義的符號 **`/D`** 。

根據預設，編譯器可能會定義大量的 Microsoft 特定符號。 以下是一些常見的案例：

| 符號 | 函式 |
|--|--|
| `_CHAR_UNSIGNED` | 預設 char 類型為未簽署。 當 [`/J`](j-default-char-type-is-unsigned.md) 指定選項時定義。 |
| `_CPPRTTI` | 為以選項編譯的程式碼定義 [`/GR`](gr-enable-run-time-type-information.md) 。 |
| `_CPPUNWIND` | 為以選項編譯的程式碼定義 [`/EHsc`](eh-exception-handling-model.md) 。 |
| `_DLL` | 當 [`/MD`](md-mt-ld-use-run-time-library.md) 指定選項時定義。 |
| `_M_IX86` | 根據預設，x86 目標的定義為600。 |
| `_MSC_VER` | 定義為每個編譯器版本的唯一整數值。 如需詳細資訊，請參閱 [預先定義的宏](../../preprocessor/predefined-macros.md)。 |
| `_WIN32` | 針對 WIN32 應用程式所定義。 永遠會定義。 |
| `_MT` | 在 [`/MD`](md-mt-ld-use-run-time-library.md) 指定或選項時定義 [`/MT`](md-mt-ld-use-run-time-library.md) 。 |

如需 Microsoft 專有預先定義宏的完整清單，請參閱 [預先定義的宏](../../preprocessor/predefined-macros.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **Advanced** ] 屬性頁。

1. 修改取消 **定義的預處理器定義** 或取消 **定義所有預處理器的定義** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[**`/J`** (預設 char 類型為未簽署) ](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`** (啟用執行時間類型資訊) ](gr-enable-run-time-type-information.md)<br/>
[**`/EH`** (例外狀況處理模型) ](eh-exception-handling-model.md)<br/>
[**`/MD`**、 **`/MT`** 、 **`/LD`** (使用執行時間程式庫) ](md-mt-ld-use-run-time-library.md)
