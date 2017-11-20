---
title: "-Qsafe_fp_loads |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f79a73565a78c8972d9d77b809cd77d774b821f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads
需要浮點值的整數移動指令，並停用特定浮點數載入最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
/Qsafe_fp_loads  
```  
  
## <a name="remarks"></a>備註  
 **/Qsafe_fp_loads** ，才可以使用的編譯器中，以 x86 為目標，而非在 x64 或 ARM 為目標的編譯器中使用。  
  
 **/Qsafe_fp_loads**強制編譯器使用整數移動指令，而非浮點移動指令，記憶體和 MMX 之間移動資料暫存器。 這個選項也會停用浮點數值的暫存器載入最佳化，當值在載入時可能會導致例外狀況 (例如 NaN 值)，可在多個控制路徑中載入。  
  
 此選項會覆寫[/fp： 除了](../../build/reference/fp-specify-floating-point-behavior.md)。 **/Qsafe_fp_loads**指定所指定的編譯器行為的子集**/fp： 除了**。  
  
 **/Qsafe_fp_loads**與不相容[/clr](../../build/reference/clr-common-language-runtime-compilation.md)和[/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md)。 如需浮動點編譯器選項的詳細資訊，請參閱[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)