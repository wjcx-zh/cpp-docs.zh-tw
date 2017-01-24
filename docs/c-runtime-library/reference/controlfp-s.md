---
title: "_controlfp_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_controlfp_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "controlfp_s"
  - "_controlfp_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_controlfp_s 函式"
  - "controlfp_s 函式"
  - "EM_AMBIGUOUS"
  - "浮點函式, 設定控制字組"
  - "浮點數, 控制字組"
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _controlfp_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得和設定浮點控制字。  這些 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _controlfp_s(  
    unsigned int *currentControl,  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### 參數  
 `currentControl`  
 目前控制項的文字值。  
  
 `newControl`  
 新的控制字位元值。  
  
 `mask`  
 設置的新控制字位元的遮罩。  
  
## 傳回值  
 如果成功就是零，如果失敗，則`errno`值為錯誤碼。  
  
## 備註  
 `_controlfp_s` 函式是 `_control87`與平台無關且更安全的版本，使用 `newControl`，讓浮點控制字輸入地址並儲存於 `currentControl` 與設定他。  位元值表示浮點控制項狀態。  浮點控制狀態可讓程式根據平台來變更浮點算術套件的精確度、四捨五入以及無限方式。  您也可以使用 `_controlfp_s` 對浮點例外狀況作遮罩或去遮罩。  
  
 如果 `mask` 的值等於 0，則 `_controlfp_s` 取得在 `currentControl`的浮點控制字並儲存擷取的值。  
  
 如果 `mask` 是非零值，則新的控制字之值會被設置： 對於 `mask` 的任何被設定的位元 \(那就是等於 1\)， `new` 裡對應的位元會用於更新控制字。  換句話說， `fpcntrl``=` \(\(`fpcntrl``& ~mask`\)&#124;\(`new & mask`\)\) 其中 `fpcntrl` 是浮點控制字。  在這個案例中，在變更完成之後， `currentControl` 會設定為值；它不是舊的控制文字的值。  
  
> [!NOTE]
>  根據預設，執行階段程式庫遮罩所有浮點例外狀況。  
  
 `_controlfp_s`幾乎同於 Intel \(x86\) [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]和 ARM 平台的`_control87` 函式。  如果您是以 x86， [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]或 ARM 平台鎖定目標，您可以使用 `_control87` 或 `_controlfp_s`。  
  
 `_control87` 和 `_controlfp_s` 的差異在於它們如何處理 `DENORMAL` 值。  對Intel \(x86\) 平台 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]與 ARM 平台來說，`_control87`會設置並清除 DENORMAL OPERAND 例外狀況遮罩。  `_controlfp_s` 不會修改 DENORMAL 運算元例外狀況遮罩。  此範例將示範其差異：  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call.  
unsigned int current_word = 0;  
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged.  
```  
  
 常數遮罩的可能值 \(`mask`\) 和新控制項的值 \(`newControl`\) 如下十六進位值表格所示。  使用如下所列的可移植常數 \(`_MCW_EM` 、 `_EM_INVALID` 等等\) 為參數予這些函式，而不要直接提供十六進位值。  
  
 Intel \(x86\) 裝置平台於硬體支援 DENORMAL 的輸入和輸出值。   x86 行為是為了保留 DENORMAL 值。  安排 SSE2 支援啟用 DENORMAL 運算元並導致被清除或受強制設定為零的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台。  `_controlfp_s` ， `_controlfp`和 `_control87`函式提供遮罩來變更此行為。  以下範例將說明此遮罩的用法:  
  
```  
unsigned int current_word = 0;  
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上， `_controlfp_s` 函式套用至 FPSCR 暫存器。  在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構，只有儲存在 MXCSR 暫存器中的SSE2控制字會受影響。  在 Intel \(x86\) 平台上，`_controlfp_s` 會影響 x87 和 SSE2 的此控制字\(如果有的話\)。  兩個控制字可能是不一致的\(例如，由於[\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 的先前呼叫\)；如果兩個控制字不一致，`_controlfp_s` 在`currentControl` 設定`EM_AMBIGUOUS` 旗標。  這是用來表示控制字可能無法精確地表示兩個浮點控制字的狀態之警告。  
  
 在 ARM架構 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構中不支援無限模式或浮點精確度的變更。  如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台使用精準度控制遮罩，函式會調用一個提示而叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  
  
 如果遮罩未正確設定，這個函式會產生無效參數例外狀況，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
 當您使用 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 來編譯是會忽略這些函式，因為 Common Language Runtime \(CLR\) 只支援預設浮點精準度。  
  
 **十六進位值**  
  
 對於 `_MCW_EM` 遮罩，清除它設定允許硬體例外狀況的例外狀況；設定其會隱藏例外狀況。  如果 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 發生，在下一個浮點指示執行前不會擲回硬體例外狀況。  若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 後的立即產生硬體例外狀況，請呼叫 FWAIT MASM 指令。  
  
|遮罩|十六進位值|常數|十六進位值|  
|--------|-----------|--------|-----------|  
|`_MCW_DN` \(Denormal 控制項\)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` \(中斷例外狀況遮罩\)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` \(無限控制項\)<br /><br /> \(不支援在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台\)。|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` \(捨入控制項\)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` \(精準度控制\)<br /><br /> \(不支援在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台\)。|0x00030000|`_PC_24` \(24 位元\)<br /><br /> `_PC_53` \(53 位元\)<br /><br /> `_PC_64` \(64 位元\)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_controlfp_s`|\<float.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_contrlfp_s.c  
// processor: x86  
// This program uses _controlfp_s to output the FP control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
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
  
## Output  
  
```  
Original: 0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0xa001f  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87、\_statusfp、\_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)