---
title: "memmove、wmemmove | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memmove"
  - "wmemmove"
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
apitype: "DLLExport"
f1_keywords: 
  - "memmove"
  - "wmemmove"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "memmove 函式"
  - "wmemmove 函式"
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# memmove、wmemmove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移動一個緩衝區至另一個。  這些函式已有更安全的版本可用，請參閱 [memmove\_s、wmemmove\_s](../../c-runtime-library/reference/memmove-s-wmemmove-s.md)。  
  
## 語法  
  
```  
void *memmove(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemmove(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### 參數  
 `dest`  
 目的物件。  
  
 `src`  
 物件來源  
  
 `count`  
 要複製的位元組數目 \(`memmove`\) 或字元 \(`wmemmove`\)。  
  
## 傳回值  
 `dest` 的值  
  
## 備註  
 複製 `count` 位元組\(`memmove`\) 或字元\(`wmemmove`\)從 `src` 的字元加入至 `dest` 如果來源區域和目的地陣列區域重疊，兩個函式皆保證原始來源位元組在重疊的區域在覆寫之前複製。  
  
 **安全性提示** 確定目的緩衝區大於或等於來源緩衝區。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 `memmove` 和 `wmemmove` 函式才會被取代，如果常數 `_CRT_SECURE_DEPRECATE_MEMORY` 在包含陳述式之前針對要被取代的函式，如以下範例所示:  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <string.h>  
or  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`memmove`|\<string.h\>|  
|`wmemmove`|\<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_memcpy.c  
// Illustrate overlapping copy: memmove  
// always handles it correctly; memcpy may handle  
// it correctly.  
//  
  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
  
char str1[7] = "aabbcc";  
  
int main( void )  
{  
   printf( "The string: %s\n", str1 );  
   memcpy( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
  
   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string  
  
   printf( "The string: %s\n", str1 );  
   memmove( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
}  
```  
  
  **The string: aabbcc**  
**New string: aaaabb**  
**The string: aabbcc**  
**New string: aaaabb**   
## .NET Framework 對等用法  
 [System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)  
  
## 請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)