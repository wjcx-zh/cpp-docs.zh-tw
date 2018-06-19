---
title: -/arch (ARM) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a411d0c7d07fb7392baaaa4fb8a8377fcb36598
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369860"
---
# <a name="arch-arm"></a>/arch (ARM)
為 ARM 上的程式碼產生指定架構。 另請參閱[/arch (x86)](../../build/reference/arch-x86.md)和[/arch (x64)](../../build/reference/arch-x64.md)。  
  
## <a name="syntax"></a>語法  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>引數  
 **/arch: armv7ve**  
 啟用 ARMv7VE 虛擬擴充功能指令。  
  
 **/arch: vfpv4**  
 啟用 ARM VFPv4 指令。 如果未指定此選項，VFPv3 就是預設值。  
  
## <a name="remarks"></a>備註  
 `_M_ARM_FP` （僅適用於 ARM) 的巨集指出哪些，若有的話， **/arch**編譯器選項使用。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時， **/arch**不有對 managed 函式的程式碼產生任何影響。 **/arch**只會影響程式碼產生原生函式。  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /arch:ARMv7VE 或 /arch:VFPv4 編譯器選項  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +** 資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  在**其他選項**方塊中，加入`/arch:ARMv7VE`或`/arch:VFPv4`。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)