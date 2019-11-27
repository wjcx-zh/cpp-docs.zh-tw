---
title: /GX (啟用例外狀況處理)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245093"
---
# <a name="gx-enable-exception-handling"></a>/GX (啟用例外狀況處理)

已取代。 會使用假設使用 `extern "C"` 所宣告的函式永遠不會擲回例外狀況，以啟用同步例外狀況處理。

## <a name="syntax"></a>語法

```
/GX
```

## <a name="remarks"></a>備註

**/Gx**已被取代。 請改用對等的[/ehsc](eh-exception-handling-model.md)選項。 如需已被取代的編譯器選項清單，請參閱[依分類列出的編譯器選項](compiler-options-listed-by-category.md)中的**已被取代和移除的編譯器選項**一節。

根據預設，當您使用 Visual Studio 開發環境進行編譯時， **/ehsc**（相當於 **/gx**）就會生效。 使用命令列工具時，不會指定任何例外狀況處理。 這相當於 **/GX-** 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在流覽窗格中，選擇 [設定] [**屬性**]、[ **CC++/** ]、[**命令列**]。

1. 在 [其他選項] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/EH (例外狀況處理模型)](eh-exception-handling-model.md)
