---
title: /Ge (啟用堆疊探查)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: a785ec041370e0bcbb2ce8b698bfba89235a0a0c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812131"
---
# <a name="ge-enable-stack-probes"></a>/Ge (啟用堆疊探查)

啟動堆疊探查，每個函式呼叫的本機變數需要的儲存體。

## <a name="syntax"></a>語法

```
/Ge
```

## <a name="remarks"></a>備註

這項機制是很有用，如果您重寫的堆疊探查功能。 建議您改用[/Gh (啟用 _penter 攔截函式)](gh-enable-penter-hook-function.md)而不是重寫堆疊探查。

[/Gs （控制堆疊檢查呼叫）](gs-control-stack-checking-calls.md)具有相同的效果。

**/Ge**是已被取代; 從 Visual Studio 2005 中，編譯器會自動產生堆疊檢查。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**中[依分類排列的編譯器選項](compiler-options-listed-by-category.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
