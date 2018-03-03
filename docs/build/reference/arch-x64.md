---
title: "-arch (x64) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27a453601988c22ed03ae9cb267480d88d6a1cc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="arch-x64"></a>/arch (x64)
在 x64 上，為程式碼產生指定架構。 另請參閱[/arch (x86)](../../build/reference/arch-x86.md)和[/arch (ARM)](../../build/reference/arch-arm.md)。  
  
## <a name="syntax"></a>語法  
  
```  
/arch:[AVX|AVX2]  
```  
  
## <a name="arguments"></a>引數  
 **/arch: avx**  
 啟用 Intel Advanced Vector Extensions 指令的使用。  
  
 **/arch: avx2**  
 啟用 Intel Advanced Vector Extensions 2 指令的使用。  
  
## <a name="remarks"></a>備註  
 **/arch**只會影響程式碼產生原生函式。 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時， **/arch**不有對 managed 函式的程式碼產生任何影響。  
  
 `__AVX__`前置處理器符號會定義當**/arch: avx**編譯器選項已指定。 `__AVX2__`前置處理器符號會定義當**/arch: avx2**編譯器選項已指定。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch: avx2**選項已引入 Visual Studio 2013 Update 2 12.0.34567.1 版。  
  
### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /arch:AVX 或 /arch:AVX2 編譯器選項  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**組態屬性**， **C/c + +**資料夾。  
  
3.  選取**程式碼產生**屬性頁。  
  
4.  在**啟用進階指令集**下拉式清單方塊中，選擇**Advanced Vector Extensions (/ /arch: AVX)**或**Advanced Vector Extensions 2 (/ /arch: AVX2)**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## <a name="see-also"></a>請參閱  
 [/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)