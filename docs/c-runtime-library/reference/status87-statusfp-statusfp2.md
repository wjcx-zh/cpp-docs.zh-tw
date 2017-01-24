---
title: "_status87、_statusfp、_statusfp2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_statusfp2"
  - "_statusfp"
  - "_status87"
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
  - "_statusfp2"
  - "_statusfp"
  - "statusfp2"
  - "_status87"
  - "status87"
  - "statusfp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "浮點函式, 取得狀態字"
  - "浮點數, 狀態字"
  - "status87 函式"
  - "狀態字, 取得浮點"
  - "statusfp 函式"
  - "_statusfp 函式"
  - "_statusfp2 函式"
  - "statusfp2 函式"
  - "_status87 函式"
  - "浮點函式"
  - "狀態字"
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _status87、_statusfp、_statusfp2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得浮點狀態字組。  
  
## 語法  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### 參數  
 `px86`  
 這個位址會填入這個 x87 浮點單位的狀態字組。  
  
 `pSSE2`  
 這個位址會填入這個 SSE2 浮點單位的狀態字組。  
  
## 傳回值  
 對於 `_status87` 和 `_statusfp`，傳回值的位元表示浮點狀態。  關於 `_statusfp` 傳回位元的定義，請參閱 FLOAT.H Include 檔。  許多數學程式庫函式修改浮點狀態字組，會造成無法預期的結果。  最佳化可對於 `_status87`、 `_statusfp` 和相關函式的呼叫進行重新排列、合併和排除浮點運算。  使用 [\/Od \(停用 \(偵錯\)\)](../../build/reference/od-disable-debug.md) 編譯器選項或 [fenv\_access](../../preprocessor/fenv-access.md) pragma 指示詞可防止重新排列浮點運算的最佳化。  如果在浮點狀態字組的已知狀態間進行的浮點作業較少，則從 `_clearfp` 和 `_statusfp` 的傳回值，以及 `_statusfp2` 的傳回參數會更可靠。  
  
## 備註  
 `_statusfp` 函式會取得浮點狀態字組。  狀態字組是浮點處理器狀態和其他由浮點例外狀況處理常式所偵測到的狀況 \(例如、浮點堆疊溢位或反向溢位\) 所組合而成。  在狀態字組的內容傳回之前，揭露的例外狀況會被檢查。  這表示呼叫端會被通知有尚未解決的例外狀況。  在 x86 平台上， `_statusfp` 會傳回 x87 和 SSE2 浮點狀態的組合。  在 x64 平台上，傳回的狀態是以 SSE 的 MXCSR 狀態為基礎。  在 ARM 平台上， `_statusfp` 會從 FPSCR 暫存器傳回狀態。  
  
 `_statusfp` 是與平台無關且可移植版本的 `_status87` 。  它與 Intel \(x86\) 平台的 `_status87` 相同，且 x64 和 ARM 平台也都支援。  為了確保您的浮點程式碼對所有結構皆可相容，請使用 `_statusfp`。  如果您只使用 x86 平台，您可以使用 `_status87` 或 `_statusfp`。  
  
 對於有 x87 和一個 SSE2 浮點處理器的晶片\(例如 Pentium IV\)，我們建議您使用 `_statusfp2`。  `_statusfp2` 對於 x87 或 SSE2 浮點處理器，會使用浮點狀態字組填滿位址。  對於支援 x87 和 SSE2 浮點處理器的晶片，如果使用了 `_statusfp` 或 `_controlfp` 並且 這個動作是模稜兩可的 \(因為可能是 x87 或 SSE2 浮點狀態字組\)，EM\_AMBIGUOUS 會設為 1。  `_statusfp2` 函式在 x86 平台上才支援。  
  
 因為 Common Language Runtime \(CLR\) 只支援預設浮點精確度，這些函式對於 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 編譯並不是很有用。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_statusfp.c  
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c  
// This program creates various floating-point errors and  
// then uses _statusfp to display messages that indicate these problems.  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access(on)  
  
double test( void )  
{  
   double a = 1e-40;  
   float b;  
   double c;  
  
   printf("Status = 0x%.8x - clear\n", _statusfp());  
  
   // Assignment into b is inexact & underflows:   
   b = (float)(a + 1e-40);  
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());  
  
   // c is denormal:   
   c = b / 2.0;   
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",   
            _statusfp());  
  
   // Clear floating point status:   
   _clearfp();  
   return c;  
}  
  
int main(void)  
{  
   return (int)test();  
}  
```  
  
  **Status \= 0x00000000 \- clear**  
**Status \= 0x00000003 \- inexact, underflow**  
**Status \= 0x00080003 \- inexact, underflow, denormal**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)