---
title: /Qsafe_fp_loads |Microsoft 文件
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1462303f9e178c70a845066bc7a0a3ce78a99e15
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

需要浮點值的整數移動指令，並停用特定浮點數載入最佳化。

## <a name="syntax"></a>語法

> **/Qsafe_fp_loads**

## <a name="remarks"></a>備註

**/Qsafe_fp_loads** ，才可以使用的編譯器中，以 x86 為目標，而非在 x64 或 ARM 為目標的編譯器中使用。

**/Qsafe_fp_loads**強制編譯器使用整數移動指令，而非浮點移動指令，記憶體和 MMX 之間移動資料暫存器。 這個選項也會停用浮點數值的暫存器載入最佳化，當值在載入時可能會導致例外狀況 (例如 NaN 值)，可在多個控制路徑中載入。

此選項會覆寫[/fp： 除了](../../build/reference/fp-specify-floating-point-behavior.md)。 **/Qsafe_fp_loads**指定所指定的編譯器行為的子集 **/fp： 除了**。

**/Qsafe_fp_loads**與不相容[/clr](../../build/reference/clr-common-language-runtime-compilation.md)和[/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md)。 如需浮動點編譯器選項的詳細資訊，請參閱[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 輸入中的編譯器選項**其他選項**方塊。 選擇**確定**以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](../../build/reference/q-options-low-level-operations.md)  
[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
