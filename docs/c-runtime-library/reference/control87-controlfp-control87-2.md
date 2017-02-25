---
title: "_control87、_controlfp、__control87_2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_control87"
  - "_controlfp"
  - "__control87_2"
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
  - "_control87"
  - "__control87_2"
  - "control87"
  - "_controlfp"
  - "controlfp"
  - "control87_2"
  - "_control87_2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__control87_2 函式"
  - "_control87 函式"
  - "_controlfp 函式"
  - "control87 函式"
  - "control87_2 函式"
  - "controlfp 函式"
  - "EM_AMBIGUOUS"
  - "浮點函式"
  - "浮點函式, 設定控制字組"
  - "浮點數, 控制字組"
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# _control87、_controlfp、__control87_2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得和設定浮點控制字。  `_controlfp` 的可用更安全版本，請參閱 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md) 。  
  
## 語法  
  
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
  
#### 參數  
 `new`  
 新的控制字位元值。  
  
 `mask`  
 設置的新控制字位元的遮罩。  
  
 `x86_cw`  
 用 x87 浮點單位的控制字填滿。  將 0 \(`NULL`\) 傳入以只設定 SSE2 控制字。  
  
 `sse2_cw`  
 SSE 浮點單位的控制字。  將 0 \(`NULL`\) 傳入以只設定 x87 控制字。  
  
## 傳回值  
 對於 `_control87` 和 `_controlfp` ，位在回傳表示浮點控制狀態值的位元。  如需由 `_control87` 回傳的這些位元之完整定義，請參閱 FLOAT.H 。  
  
 對 `__control87_2`來說，傳回值為 1則表示成功。  
  
## 備註  
 `_control87` 函式取得並設置浮點控制字。  浮點控制字可讓程式根據平台來變更浮點算術套件的精確度、四捨五入以及無限方式。  您也可以使用 `_control87` 對浮點例外狀況作遮罩或去遮罩。  如果 `mask` 的值等於 0 ， `_control87` 取得浮點控制字。  如果 `mask` 的值非零，新的控制字之值會被設置： 對於 `mask` 的任何開啟的位元 \(那就是等於 1\)， `new` 裡對應的位元會用於更新控制字。  換句話說， `fpcntrl``=` \(\(`fpcntrl``& ~mask`\)&#124;\(`new & mask`\)\) 其中 `fpcntrl` 是浮點控制字。  
  
> [!NOTE]
>  根據預設，執行階段程式庫遮罩所有浮點例外狀況。  
  
 `_controlfp` 是與平台無關的且可移植版本的 `_control87` 。  它幾乎同於 Intel \(x86\)、 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]和 ARM 平台的 `_control87` 函式。  如果您以 x86 、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 平台為目標，請使用  `_control87`或 `_controlfp`。  
  
 `_control87` 和 `_controlfp` 的差異在於它們如何處理 DENORMAL 值。  對Intel \(x86\) 平台、 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]與 ARM 平台來說，`_control87`會設置並清除 DENORMAL OPERAND 例外狀況遮罩。  `_controlfp` 不會修改 DENORMAL 運算元例外狀況遮罩。  此範例將示範其差異：  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 常數遮罩的可能值 \(`mask`\) 和新控制項的值 \(`new`\) 如下十六進位值表格所示。  使用如下所列的可移植常數 \(`_MCW_EM` 、 `_EM_INVALID` 等等\) 為參數予這些函式，而不要直接提供十六進位值。  
  
 Intel \(x86\) 裝置平台於硬體支援 DENORMAL 的輸入和輸出值。   x86 行為是為了保留 DENORMAL 值。  安排 SSE2 支援啟用 DENORMAL 運算元並導致被清除或受強制設定為零的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台。  `_controlfp` 函式和 `_control87` 函式提供遮罩來變更此行為。  以下範例將說明此遮罩的用法。  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上， `_control87` 函式和 `_controlfp` 函式套用至 FPSCR 暫存器。  在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構，只有儲存在 MXCSR 暫存器中的SSE2控制字會受影響。  在 Intel \(x86\) 平台上， `_control87` 和 `_controlfp` 會影響 x87 和 SSE2 的此控制字\(如果有的話\)。  函式 `__control87_2` 允許 x87 和 SSE2 浮點數單位都可以同時或分別控制。  如果您想要同時影響單位，請傳入兩個整數的位置予 `x86_cw` 和 `sse2_cw` 。  如果您只想要影響一個單位，請傳入一個參數的位置，並在另一傳入 0 \(空\) 。  如果有一個參數被傳入 0 ，此函式將不會影響該浮點單位。  這個功能在部分程式碼使用 x87 浮點單位而另一部分使用 SSE2 浮點單位時可能很有用。  如果您在一部分的應用程式使用 `__control87_2` 並設置不同的值予浮點控制字，然後再使用 `_control87` 或 `_controlfp` 來修改控制字，那麼 `_control87` 和 `_controlfp` 可能無法回傳單一控制字來表示兩個浮點單位的狀態。  在此狀況下，這些函式設置回傳整數裏的 `EM_AMBIGUOUS` 旗標來表示兩個控制字之間存在不協調的情況。  這是用來表示控制字可能無法精確地表示兩個浮點控制字的狀態之警告。  
  
 在 ARM架構 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構中不支援無限模式或浮點精確度的變更。  如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台使用精準度控制遮罩，函式會調用一個提示而叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  
  
> [!NOTE]
>  `__control87_2` 在 ARM架構 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構皆不支援。  如果您使用 `__control87_2` 且將您的應用程式以 ARM結構或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 結構來編譯，編譯器會產生錯誤。  
  
 當您使用 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 來編譯是會忽略這些函式，因為 Common Language Runtime \(CLR\) 只支援預設浮點精準度。  
  
 **十六進位值**  
  
 對於 `_MCW_EM` 遮罩，清除遮罩會設置例外狀況，它允許硬體例外狀況。設定遮罩會隱藏例外狀況。  如果 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 發生，在下一個浮點指示執行前不會擲回硬體例外狀況。  若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 後立即產生硬體例外狀況，請呼叫`FWAIT`MASM 指令。  
  
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
|`_control87`, `_controlfp`, `_control87_2`|\<float.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
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
  
## Output  
  
```  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87、\_statusfp、\_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)