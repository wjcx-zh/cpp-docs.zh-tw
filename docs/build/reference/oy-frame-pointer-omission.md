---
title: /Oy (框架指標省略)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: d6d896079c08ed2cf595b95ed41045885c83b5bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431729"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (框架指標省略)

在呼叫堆疊上隱藏框架指標的建立。

## <a name="syntax"></a>語法

> /Oy [-]

## <a name="remarks"></a>備註

這個選項會加速函式呼叫，因為並不需要設定及移除框架指標。 它也會釋放出更多的暫存，一般用途。

**/Oy**啟用框架指標省略並 **/Oy-** 停用省略。 **/Oy**僅適用於 x86 編譯器。

如果您的程式碼需要 EBP 架構定址，您可以指定 **/Oy-** 選項之後 **/Ox**選項，或使用[最佳化](../../preprocessor/optimize.md)具有 「**y**"並**關閉**獲得最大程度最佳化 EBP 架構定址的引數。 編譯器會偵測大部分需要 EBP 架構定址的情況 (例如，對於 `_alloca` 和 `setjmp` 函式以及處理結構化例外狀況)。

[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)並[/o1，/o2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)選項會隱含 **/Oy**。 指定 **/Oy-** 之後 **/Ox**， **/o1**，或 **/o2**選項停用 **/Oy**，不論是明確或隱含。

**/Oy**編譯器選項會使得使用偵錯工具更困難，因為編譯器會隱藏框架指標資訊。 如果您指定偵錯編譯器選項 ([/z7，/Zi，/ZI](../../build/reference/z7-zi-zi-debug-information-format.md))，我們建議您指定 **/Oy-** 之後任何最佳化編譯器選項的選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **最佳化**屬性頁。

1. 修改**省略框架指標**屬性。 這個屬性中加入或移除只有 **/Oy**選項。 如果您想要新增 **/Oy-** 選項，請按一下**命令列**並修改**其他選項**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)

[編譯器選項](../../build/reference/compiler-options.md)

[設定編譯器選項](../../build/reference/setting-compiler-options.md)
