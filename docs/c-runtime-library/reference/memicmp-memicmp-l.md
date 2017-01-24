---
title: "_memicmp、_memicmp_l | Microsoft Docs"
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
  - "_memicmp_l"
  - "_memicmp"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_memicmp"
  - "memicmp_l"
  - "_memicmp_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_memicmp 函式"
  - "_memicmp_l 函式"
  - "memicmp 函式"
  - "memicmp_l 函式"
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _memicmp、_memicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較兩個緩衝區裏的字元 \(大小寫視為相異\) 。  
  
## 語法  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `buf1`  
 第一個緩衝區。  
  
 `buf2`  
 第二個緩衝區。  
  
 `count`  
 字元數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 回傳表示兩個緩衝區大小關係的值。  
  
|傳回值|buf1 和 buf2 前 count 位元組的大小關係|  
|---------|----------------------------------|  
|\< 0|`buf1` 小於 `buf2` 。|  
|0|`buf1` 與 `buf2` 相同。|  
|\> 0|`buf1` 大於 `buf2`。|  
|`_NLSCMPERROR`|發生錯誤。|  
  
## 備註  
 `_memicmp` 函式逐位元組地比較 `buf1` 和 `buf2` 的前 `count` 字元。  此比較忽略大小寫。  
  
 如果 `buf1` 或 `buf2` 之一是空指標，此函式會呼叫無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，此函式回傳 `_NLSCMPERROR` 並設置 `errno` 為 `EINVAL` 。  
  
 `_memicmp` 在區域設定相依的動作時使用目前的區域設定。 `_memicmp_l` 除了使用傳入的區域設定以外其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_memicmp`|\<memory.h\> 或 \<string.h\>|  
|`_memicmp_l`|\<memory.h\> 或 \<string.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
  **Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'**  
**First is equal to second.**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)