---
title: "_control87、_controlfp、__control87_2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _control87
- _controlfp
- __control87_2
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: 34
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: a6a25c035a55ca247f0d81f5c206207463672881
ms.lasthandoff: 02/24/2017

---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2
取得和設定浮點控制字組。 `_controlfp` 已有更安全的版本可用；請參閱 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned int _control87(   
   unsigned int new,  
   unsigned int mask   
);  
unsigned int _controlfp(   
   unsigned int new,  
   unsigned int mask   
);  
int __control87_2(  
   unsigned int new,  
   unsigned int mask,  
   unsigned int* x86_cw,  
   unsigned int* sse2_cw  
);  
```  
  
#### <a name="parameters"></a>參數  
 `new`  
 新的控制字組位元值。  
  
 `mask`  
 要設定之新控制字組位元的遮罩。  
  
 `x86_cw`  
 填入 x87 浮點單位的控制字組。 傳入 0 (`NULL`)，僅設定 SSE2 控制字組。  
  
 `sse2_cw`  
 SSE 浮點單位的控制字組。 傳入 0 (`NULL`)，僅設定 x87 控制字組。  
  
## <a name="return-value"></a>傳回值  
 針對 `_control87` 和 `_controlfp`，傳回值中的位元表示浮點控制狀態。 如需 `_control87` 所傳回位元的完整定義，請參閱 FLOAT.H。  
  
 針對 `__control87_2`，傳回值是 1，表示成功。  
  
## <a name="remarks"></a>備註  
 `_control87` 函式會取得和設定浮點控制字組。 浮點控制字組可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您也可以使用 `_control87` 來遮罩或取消遮罩浮點例外狀況。 如果 `mask` 的值等於 0，`_control87` 會取得浮點控制字組。 如果 `mask` 為非零，則會設定控制字組的新值：針對 `mask` 中為開啟的任何位元 (即等於 1)，會使用 `new` 中的對應位元來更新控制字組。 換句話說，`fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`))，其中 `fpcntrl` 是浮點控制字組。  
  
> [!NOTE]
>  根據預設，執行階段程式庫會遮罩所有浮點例外狀況。  
  
 `_controlfp` 是 `_control87` 之與平台無關的可攜式版本。 它幾乎等同於 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台上的 `_control87` 函式。 如果您的目標是 x86、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 平台，請使用 `_control87` 或 `_controlfp`。  
  
 `_control87` 與 `_controlfp` 之間的差異在於它們如何處理 DENORMAL 值。 針對 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台，`_control87` 可以設定和清除 DENORMAL OPERAND 例外狀況遮罩。 `_controlfp` 不會修改 DENORMAL OPERAND 例外狀況遮罩。 這個範例示範差異：  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 下列「十六進位值」表格顯示遮罩常數 (`mask`) 和新控制項值 (`new`) 的可能值。 使用下面所列的可攜式常數 (`_MCW_EM`、`_EM_INVALID` 等) 作為這些函式的引數，而不是明確地提供十六進位值。  
  
 Intel (x86) 衍生的平台支援硬體中的 DENORMAL 輸入和輸出值。 x86 行為是保留 DENORMAL 值。 支援 SSE2 的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台會清除 DENORMAL 運算元和結果，或強制為零。 `_controlfp` 和 `_control87` 函式提供遮罩來變更此行為。 下列範例示範如何使用此遮罩。  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，`_control87` 和 `_controlfp` 函式套用至 FPSCR 暫存器。 在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 結構上，只會影響 MXCSR 暫存器中所儲存的 SSE2 控制字組。 在 Intel (x86) 平台上，`_control87` 和 `_controlfp` 會影響 x87 和 SSE2 (如果有的話) 的控制字組。 `__control87_2` 函式會一併或分開控制 x87 和 SSE2 浮點單位。 如果您想要影響這兩個單元，請將兩個整數的位址傳入 `x86_cw` 和 `sse2_cw`。 如果您只想要影響一個單位，請傳入該參數的位址，但傳入 0 (NULL) 表示影響其他單位。 如果針對其中一個參數傳遞 0，則此函式不會影響該浮點單位。 如果程式碼的一部分使用 x87 浮點單位，而程式碼的另一個部分使用 SSE2 浮點單位，則此函式可能十分有用。 如果您在程式的某個部分使用 `__control87_2` 並設定不同的浮點控制字組值，接著使用 `_control87` 或 `_controlfp` 進一步操作控制字組，則 `_control87` 和 `_controlfp` 可能無法傳回單一控制字組來代表這兩個浮點單位的狀態。 在這種情況下，這些函式會在所傳回整數值中設定 `EM_AMBIGUOUS` 旗標，表示兩個控制單字不一致。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構上，不支援變更無效模式或浮點精確度。 如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上使用精確度控制遮罩，此函式會引發判斷提示，並叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。  
  
> [!NOTE]
> ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 結構不支援  `__control87_2`。 如果您使用 `__control87_2`，並針對 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 結構編譯您的程式，編譯器會產生錯誤。  
  
 這些函式會被忽略，當您使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯，因為 common language runtime (CLR) 僅支援預設浮點有效位數。  
  
 **十六進位值**  
  
 針對 `_MCW_EM` 遮罩，清除遮罩會設定例外狀況，以允許硬體例外狀況；設定遮罩則會隱藏例外狀況。 如果發生 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`，則除非執行下一個浮點指令，否則不會擲回任何硬體例外狀況。 若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 之後立即產生硬體例外狀況，請呼叫 `FWAIT` MASM 指令。  
  
|遮罩|十六進位值|常數|十六進位值|  
|----------|---------------|--------------|---------------|  
|`_MCW_DN` (異常控制項)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` (插斷例外狀況遮罩)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` (無限大控制項)<br /><br /> (ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上不予支援)。|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` (四捨五入控制項)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` (精確度控制項)<br /><br /> (ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上不予支援)。|0x00030000|`_PC_24` (24 位元)<br /><br /> `_PC_53` (53 位元)<br /><br /> `_PC_64` (64 位元)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_control87`, `_controlfp`, `_control87_2`|\<float.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
  
      // crt_cntrl87.c  
// processor: x86  
// This program uses __control87_2 to output the x87 control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access (on)  
  
int main( void )  
{  
    double a = 0.1;  
    unsigned int control_word_x87;  
  
    // Show original x87 control word and do calculation.  
    control_word_x87 = __control87_2(0, 0,  
                                     &control_word_x87, 0);  
    printf( "Original: 0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Set precision to 24 bits and recalculate.  
    control_word_x87 = __control87_2(_PC_24, MCW_PC,  
                                     &control_word_x87, 0);  
    printf( "24-bit:   0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Restore default precision-control bits and recalculate.  
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,   
                                     &control_word_x87, 0 );  
    printf( "Default:  0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)
