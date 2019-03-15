---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819686"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

需要浮點值的整數移動指令，並停用特定浮點數載入最佳化。

## <a name="syntax"></a>語法

> **/Qsafe_fp_loads**

## <a name="remarks"></a>備註

**/Qsafe_fp_loads**僅供以 x86 為目標，而非在 x64 或 ARM 為目標的編譯器中使用。

**/Qsafe_fp_loads**強制編譯器使用整數移動指令而非浮點移動指令，來移動之間的記憶體和 MMX 暫存器。 這個選項也會停用浮點數值的暫存器載入最佳化，當值在載入時可能會導致例外狀況 (例如 NaN 值)，可在多個控制路徑中載入。

此選項會覆寫[/fp： 除了](fp-specify-floating-point-behavior.md)。 **/Qsafe_fp_loads**指定所指定的編譯器行為的子集 **/fp： 除了**。

**/Qsafe_fp_loads**與不相容[/clr](clr-common-language-runtime-compilation.md)並[/fp: fast](fp-specify-floating-point-behavior.md)。 如需浮點編譯器選項的詳細資訊，請參閱[/fp （指定浮點行為）](fp-specify-floating-point-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 輸入中的編譯器選項**其他選項** 方塊中。 選擇**確定**以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
