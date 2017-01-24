---
title: "_lrotl、_lrotr | Microsoft Docs"
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
  - "_lrotl"
  - "_lrotr"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lrotr"
  - "lrotl"
  - "_lrotr"
  - "_lrotl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lrotl 函式"
  - "_lrotr 函式"
  - "位元"
  - "位元, 旋轉"
  - "lrotl 函式"
  - "lrotr 函式"
  - "旋轉位元"
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lrotl、_lrotr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

旋轉的位元向左移 \(`_lrotl`\) 或向右移 \(`_lrotr`\)。  
  
## 語法  
  
```  
  
      unsigned long _lrotl(  
   unsigned long value,  
   int shift   
);  
unsigned long _lrotr(  
   unsigned long value,  
   int shift   
);  
```  
  
#### 參數  
 *value*  
 旋轉的值。  
  
 `shift`  
 將 *值*向左移的位元數。  
  
## 傳回值  
 兩個函式傳回旋轉的值。  不會回傳錯誤。  
  
## 備註  
 `_lrotl` 和 `_lrotr` 函式由 `shift` 位元旋轉 *值* 。  `_lrotl` 旋轉值向左。  `_lrotr` 旋轉值向右。  兩個函式包裝位元旋轉 *值* 結尾對其他結尾。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lrotl`|\<stdlib.h\>|  
|`_lrotr`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_lrot.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned long val = 0x0fac35791;  
  
   printf( "0x%8.8lx rotated left eight times is 0x%8.8lx\n",   
            val, _lrotl( val, 8 ) );  
   printf( "0x%8.8lx rotated right four times is 0x%8.8lx\n",   
            val, _lrotr( val, 4 ) );  
}  
```  
  
## Output  
  
```  
0xfac35791 rotated left eight times is 0xc35791fa  
0xfac35791 rotated right four times is 0x1fac3579  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_rotl、\_rotl64、\_rotr、\_rotr64](../../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)