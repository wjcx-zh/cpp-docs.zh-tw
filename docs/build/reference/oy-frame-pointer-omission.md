---
title: /Oy (框架指標省略)
ms.date: 11/19/2018
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
ms.openlocfilehash: 7884f52cc22766c6b1a864fc01abcd73f92cfabb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817955"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (框架指標省略)

在呼叫堆疊上隱藏框架指標的建立。

## <a name="syntax"></a>語法

> /Oy[-]

## <a name="remarks"></a>備註

這個選項會加速函式呼叫，因為並不需要設定及移除框架指標。 它也會釋放出更多的暫存，一般用途。

**/Oy**啟用框架指標省略並 **/Oy-** 停用省略。 在 x64 編譯器 **/Oy**並 **/Oy-** 不提供。

如果您的程式碼會要求框架定址，您可以指定 **/Oy-** 選項之後 **/Ox**選項，或使用[最佳化](../../preprocessor/optimize.md)具有 「**y**"和**關閉**引數，以獲得最大程度最佳化框架定址。 編譯器偵測到的是需要框架定址的大部分情況下 (例如，對於`_alloca`和`setjmp`函式和結構化例外狀況處理)。

[/Ox （啟用最速度最佳化）](ox-full-optimization.md)並[/o1，/o2 （最小大小、 最快速度）](o1-o2-minimize-size-maximize-speed.md)選項會隱含 **/Oy**。 指定 **/Oy-** 之後 **/Ox**， **/o1**，或 **/o2**選項停用 **/Oy**，不論是明確或隱含。

**/Oy**編譯器選項會使得使用偵錯工具更困難，因為編譯器會隱藏框架指標資訊。 如果您指定偵錯編譯器選項 ([/z7，/Zi，/ZI](z7-zi-zi-debug-information-format.md))，我們建議您指定 **/Oy-** 之後任何最佳化編譯器選項的選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **最佳化**屬性頁。

1. 修改**省略框架指標**屬性。 這個屬性中加入或移除只有 **/Oy**選項。 如果您想要新增 **/Oy-** 選項中，選取**命令列** 屬性頁面，然後修改**其他選項**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
