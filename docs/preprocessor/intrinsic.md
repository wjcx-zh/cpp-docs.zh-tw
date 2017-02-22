---
title: "intrinsic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "intrinsic_CPP"
  - "vc-pragma.intrinsic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "intrinsic pragma"
  - "Pragma, intrinsic"
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# intrinsic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 pragma 引數清單中指定的函式呼叫為內建 \(Intrinsic\)。  
  
## 語法  
  
```  
  
#pragma intrinsic( function1 [, function2, ...] )  
```  
  
## 備註  
 **intrinsic** pragma 會告知編譯器，函式具有已知行為。如果會產生較佳的效能，則編譯器可能會呼叫函式，而不會以內嵌指令取代函式呼叫。  
  
 內建形式的程式庫函式如下所列。  一旦看見 **intrinsic** pragma，就會對包含所指定內建函式的第一個函式定義生效。  此作用會持續到原始程式檔的結尾，或是指定相同內建函式的 **function** pragma 出現為止。  **intrinsic** pragma 只能在函式定義之外 \(也就是在全域層級上\) 使用。  
  
 下列函式具有內建形式，這些內建形式會在您指定 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md) 時使用：  
  
|||||  
|-|-|-|-|  
|[\_disable](../intrinsics/disable.md)|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|  
|[\_enable](../intrinsics/enable.md)|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../misc/labs-llabs.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|[\_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|[\_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||  
|[\_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[\_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||  
|[\_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||  
  
 使用內建函式的程式速度較快，因為它們不需額外負擔函式呼叫，但是也因為會產生額外的程式碼，所以體積比較大。  
  
 **x86 專屬資訊**  
  
 \_disable 和 \_enable 內建會產生停用\/啟用中斷的核心模式指令，在核心模式驅動程式方面可能會很實用。  
  
## 範例  
 在命令列中使用 "cl \-c \-FAs sample.c" 編譯下列程式碼並查看 sample.asm，這些指令會變成 x86 指令 CLI 和 STI：  
  
```  
// pragma_directive_intrinsic.cpp  
// processor: x86  
#include <dos.h>   // definitions for _disable, _enable  
#pragma intrinsic(_disable)  
#pragma intrinsic(_enable)  
void f1(void) {  
   _disable();  
   // do some work here that should not be interrupted  
   _enable();  
}  
int main() {  
}  
```  
  
 **x86 專屬資訊結束**  
  
 下列浮點函式沒有真正的內建形式。  它們是使用版本直接將引數傳遞至浮點晶片，而不是將引數推送至程式堆疊：  
  
|||||  
|-|-|-|-|  
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)||  
  
 當您指定 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md)、[\/Og](../build/reference/og-global-optimizations.md) 和 [\/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) \(或是包含 \/Og: [\/Ox](../build/reference/ox-full-optimization.md)、[\/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md) 和 \/O2 的任何選項\) 時，下列浮點函式具有真正的內建形式：  
  
|||||  
|-|-|-|-|  
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)||||  
  
 您可以使用 [\/fp:strict](../build/reference/fp-specify-floating-point-behavior.md) 或 [\/Za](../build/reference/za-ze-disable-language-extensions.md) 覆寫產生真正內建浮點選項的作業。  在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。  
  
 如需如何啟用\/停用原始程式文字區塊之內建的詳細資訊和範例，請參閱 [\# pragma 函式](../preprocessor/function-c-cpp.md)。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)