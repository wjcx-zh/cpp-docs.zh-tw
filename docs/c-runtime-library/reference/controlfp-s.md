---
title: _controlfp_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _controlfp_s
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
- controlfp_s
- _controlfp_s
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 4345539f7ecd836280bed94c4bb2b125dfa08107
ms.contentlocale: zh-tw
ms.lasthandoff: 02/28/2017

---
# <a name="controlfps"></a>_controlfp_s
取得和設定浮點控制字組。 這版的 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _controlfp_s(  
    unsigned int *currentControl,  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>參數  
 `currentControl`  
 目前的控制字組位元值。  
  
 `newControl`  
 新的控制字組位元值。  
  
 `mask`  
 要設定之新控制字組位元的遮罩。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零，或 `errno` 值錯誤碼。  
  
## <a name="remarks"></a>備註  
 `_controlfp_s` 函式是與平台無關且更安全的 `_control87` 版本，可將浮點控制字組放入 `currentControl` 中所儲存的位址，並使用 `newControl` 進行設定。 值中的位元表示浮點控制狀態。 浮點控制狀態可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您也可以使用 `_controlfp_s` 來遮罩或取消遮罩浮點例外狀況。  
  
 如果 `mask` 的值等於 0，`_controlfp_s` 會取得浮點控制字組，並將擷取到的值儲存至 `currentControl`。  
  
 如果 `mask` 為非零，則會設定控制字組的新值：針對 `mask` 中所設定的任何位元 (即等於 1)，會使用 `new` 中的對應位元來更新控制字組。 換句話說，`fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`))，其中 `fpcntrl` 是浮點控制字組。 在此情況下，`currentControl` 會在變更完成之後設為此值；它不是舊的控制字組位元值。  
  
> [!NOTE]
>  根據預設，執行階段程式庫會遮罩所有浮點例外狀況。  
  
 `_controlfp_s` 幾乎等同於 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台上的 `_control87` 函式。 如果您的目標是 x86、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 平台，您可以使用 `_control87` 或 `_controlfp_s`。  
  
 `_control87` 與 `_controlfp_s` 之間的差異在於它們如何處理 `DENORMAL` 值。 針對 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台，`_control87` 可以設定和清除 DENORMAL OPERAND 例外狀況遮罩。 `_controlfp_s` 不會修改 DENORMAL OPERAND 例外狀況遮罩。 這個範例示範差異：  
  
```C  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call.  
unsigned int current_word = 0;  
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged.  
```  
  
 下列「十六進位值」表格顯示遮罩常數 (`mask`) 和新控制項值 (`newControl`) 的可能值。 使用下面所列的可攜式常數 (`_MCW_EM`、`_EM_INVALID` 等) 作為這些函式的引數，而不是明確地提供十六進位值。  
  
 Intel (x86) 衍生的平台支援硬體中的 DENORMAL 輸入和輸出值。 x86 行為是保留 DENORMAL 值。 支援 SSE2 的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台會清除 DENORMAL 運算元和結果，或強制為零。 `_controlfp_s`、`_controlfp` 和 `_control87` 函式提供遮罩來變更此行為。 下列範例示範如何使用此遮罩：  
  
```C  
unsigned int current_word = 0;  
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，`_controlfp_s` 函式套用至 FPSCR 暫存器。 在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 結構上，只會影響 MXCSR 暫存器中所儲存的 SSE2 控制字組。 在 Intel (x86) 平台上，`_controlfp_s` 會影響 x87 和 SSE2 (如果有的話) 的控制字組。 這兩個控制字組可能彼此不一致 (例如，因為前一次呼叫 [__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md))；如果兩個控制字組不一致，`_controlfp_s` 會在 `currentControl` 中設定 `EM_AMBIGUOUS` 旗標。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構上，不支援變更無效模式或浮點精確度。 如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上使用精確度控制遮罩，此函式會引發判斷提示，並叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。  
  
 如果未正確地設定遮罩，則此函式會產生無效參數例外狀況 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 若允許繼續執行，此函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
 當您使用時，此函式會忽略[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯，因為 common language runtime (CLR) 只支援預設的浮點精確度。  
  
### <a name="mask-constants-and-values"></a>遮罩常數和值  
  
 針對 `_MCW_EM` 遮罩，清除它會設定例外狀況，以允許硬體例外狀況；設定它則會隱藏例外狀況。 如果發生 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`，則除非執行下一個浮點指令，否則不會擲回任何硬體例外狀況。 若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 之後立即產生硬體例外狀況，請呼叫 FWAIT MASM 指令。  
  
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
|`_controlfp_s`|\<float.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
// crt_contrlfp_s.c  
// processor: x86  
// This program uses _controlfp_s to output the FP control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access (on)  
  
int main( void )  
{  
    double a = 0.1;  
    unsigned int control_word;  
    int err;  
  
    // Show original FP control word and do calculation.  
    err = _controlfp_s(&control_word, 0, 0);  
    if ( err ) /* handle error here */;  
  
    printf( "Original: 0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Set precision to 24 bits and recalculate.  
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);  
    if ( err ) /* handle error here */;  
  
    printf( "24-bit:   0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Restore default precision-control bits and recalculate.  
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);  
    if ( err ) /* handle error here */;  
  
    printf( "Default:  0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
}  
```  
  
```Output  
Original: 0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0xa001f  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)
