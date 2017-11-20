---
title: "-arch (x86) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
caps.latest.revision: "33"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1dd4689cf4e2ef4c4f6601396110327c74773b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="arch-x86"></a>/arch (x86)
在 x86 上，為程式碼產生指定架構。 另請參閱[/arch (x64)](../../build/reference/arch-x64.md)和[/arch (ARM)](../../build/reference/arch-arm.md)。  
  
## <a name="syntax"></a>語法  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## <a name="arguments"></a>引數  
 **/arch:IA32**  
 指定沒有增強的指令，同時指定用於浮點數計算的 x87。  
  
 **/arch:SSE**  
 啟用 SSE 指令的使用。  
  
 **/arch:SSE2**  
 啟用 SSE2 指令的使用。 這是預設值指示，在 x86 平台，如果沒有**/arch**指定選項。  
  
 **/arch: avx**  
 啟用 Intel Advanced Vector Extensions 指令的使用。  
  
 **/arch: avx2**  
 啟用 Intel Advanced Vector Extensions 2 指令的使用。  
  
## <a name="remarks"></a>備註  
 SSE 及 SSE2 指令在各種 Intel 及 AMD 處理器上存在。 AVX 指令在 Intel Sandy Bridge 處理器及 AMD Bulldozer 處理器上存在。 AVX2 指令由 Intel Haswell 和 Broadwell 處理器及 AMD Excavator 處理器支援。  
  
 `_M_IX86_FP`，`__AVX__`和`__AVX2__`巨集指出，如果有的話， **/arch**編譯器選項使用。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch: avx2**選項和`__AVX2__`巨集已引入 Visual Studio 2013 Update 2 12.0.34567.1 版。  
  
 最佳化工具選擇何時及如何使用 SSE 及 SSE2 指令時**/arch**指定。 當最佳化工具判定在計算某些純量浮點數時，使用 SSE/SSE2 指令及暫存器要比使用 x87 浮點數暫存器堆疊更快時，它會使用 SSE 及 SSE2 指令。 因此，在計算浮點數時，您的程式碼可能實際上是使用 x87 與 SSE/SSE2 的混合。 此外，在**/arch:SSE2**，SSE2 指令可用於部分 64 位元整數作業。  
  
 除了使用 SSE 及 SSE2 指令之外，編譯器還會使用支援 SSE 及 SSE2 之處理器修訂上存在的其他指令。 例如，最先出現在 Intel 處理器 Pentium Pro 修訂上的 CMOV 指令。  
  
 根據預設，的 x86 編譯器會產生程式碼，它使用 SSE2 指令，因為您必須指定**/arch:IA32**停用的 SSE 及 SSE2 指令的產生適用於 x86 處理器。  
  
 **/arch**只會影響程式碼產生原生函式。 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時， **/arch**不有對 managed 函式的程式碼產生任何影響。  
  
 **/arch**和[/QIfist](../../build/reference/qifist-suppress-ftol.md)不能在相同編譯單位。 具體來說，如果您未使用 `_controlfp` 來修改 FP 控制字組，則執行階段啟始程式碼會將 x87 FPU 控制字組精確度控制欄位，設定為 53 個位元。 因此，運算式中的每一個浮點數及雙精度浮點數運算都會使用 53 個位元的有效位數及 15 個位元的指數。 不過，每一個 SSE 單精確度運算會使用 24 個位元的有效位數及 8 個位元的指數，而 SSE2 雙精確度運算會使用 53 個位元的有效位數及 11 個位元的指數。 如需詳細資訊，請參閱 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。 在一個運算式樹狀架構可能存在這些差異，但在每一個子運算式之後涉及使用者指派的情況下除外。 請考慮下列事項：  
  
```cpp  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 比較：  
  
```cpp  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>在 Visual Studio 中設定 AVX、AVX2、IA32、SSE 或 SSE2 的這個編譯器選項  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**組態屬性**， **C/c + +**資料夾。  
  
3.  選取**程式碼產生**屬性頁。  
  
4.  修改**啟用進階指令集**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)