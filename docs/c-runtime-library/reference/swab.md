---
title: "swab | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_swab"
  - "stdlib/_swab"
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
  - "swab"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swab 函式"
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _swab
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

交換位元組。  
  
## 語法  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
#### 參數  
 `src`  
 要複製和交換的位元組。  
  
 `dest`  
 交換資料的存放位置。  
  
 `n`  
 要複製和交換的位元組數。  
  
## 備註  
 如果 `n` 是偶數， `_swab` 函式從 `src` 複製 `n` 個位元組，交換每一對相鄰的位元組，然後將結果儲存在 `dest` 。  如果 `n` 是奇數， `_swab` 複製並交換 `src` 裏的前 `n-1` 個位元組。  `_swab` 通常用來為傳送二進制資料到不同位元組序的機器做準備。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_swab`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "..........................";  
  
int main()  
{  
    printf( "Before: %s\n        %s\n\n", from, to );  
    _swab( from, to, sizeof( from ) );  
    printf( "After:  %s\n        %s\n\n", from, to );  
}  
```  
  
  **Before: BADCFEHGJILKNMPORQTSVUXWZY**  
 **..........................**  
**After: BADCFEHGJILKNMPORQTSVUXWZY**  
 **ABCDEFGHIJKLMNOPQRSTUVWXYZ**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)