---
title: "-Oy （框架指標省略） |Microsoft 文件"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs:
- C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15a760d1a9df383356ead2eb2d1e1b08e8b9ca57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="oy-frame-pointer-omission"></a>/Oy (框架指標省略)

在呼叫堆疊上隱藏框架指標的建立。

## <a name="syntax"></a>語法

> /Oy [-]

## <a name="remarks"></a>備註

這個選項會加速函式呼叫，因為並不需要設定及移除框架指標。 而且也能夠釋出更多暫存器 (Intel 386 或以上的 EBP)，以供儲存經常使用的變數和子運算式。

**/Oy**啟用框架指標省略和**/Oy-**停用省略。 **/Oy**僅適用於 x86 編譯器。

如果您的程式碼需要 EBP 架構定址，您可以指定**/Oy-**選項之後**/Ox**選項，或使用[最佳化](../../preprocessor/optimize.md)與 「**y**"和**關閉**獲得最大最佳化與 EBP 架構定址的引數。 編譯器會偵測大部分需要 EBP 架構定址的情況 (例如，對於 `_alloca` 和 `setjmp` 函式以及處理結構化例外狀況)。

[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)和[/O1、 /O2 （最小化的大小、 最大化的速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)選項代表**/Oy**。 指定**/Oy-**之後**/Ox**， **/O1**，或**/O2**選項會停用**/Oy**，無論它是明確或隱含。

**/Oy**編譯器選項會使得使用偵錯工具更困難，因為編譯器會隱藏框架指標資訊。 如果您指定偵錯編譯器選項 ([/Z7、 /Zi、 /ZI](../../build/reference/z7-zi-zi-debug-information-format.md))，我們建議您指定**/Oy-**之後任何最佳化編譯器選項的選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下**最佳化**屬性頁。

1. 修改**省略框架指標**屬性。 這個屬性中加入或移除僅**/Oy**選項。 如果您想要新增**/Oy-**選項，請按一下**命令列**和修改**其他選項**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。

## <a name="see-also"></a>請參閱

[/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)

[編譯器選項](../../build/reference/compiler-options.md)

[設定編譯器選項](../../build/reference/setting-compiler-options.md)