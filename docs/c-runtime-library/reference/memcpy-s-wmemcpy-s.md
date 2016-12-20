---
title: "memcpy_s、wmemcpy_s | Microsoft Docs"
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
  - "memcpy_s"
  - "wmemcpy_s"
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
  - "wmemcpy_s"
  - "memcpy_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "memcpy_s 函式"
  - "wmemcpy_s 函式"
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# memcpy_s、wmemcpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製緩衝區之間的位元組。 這些是舊版 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t memcpy_s(  
   void *dest,  
   size_t destSize,  
   const void *src,  
   size_t count   
);  
errno_t wmemcpy_s(  
   wchar_t *dest,  
   size_t destSize,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### 參數  
 `dest`  
 新的緩衝區。  
  
 `destSize`  
 目的地緩衝區，以位元組為單位 memcpy\_s 和 wmemcpy\_s 寬字元 \(wchar\_t\) 的大小。  
  
 `src`  
 要複製的緩衝區。  
  
 `count`  
 要複製的字元數目。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|`dest`|`destSize`|`src`|傳回值|`dest` 的內容。|  
|------------|----------------|-----------|---------|-----------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`dest` 已清空|  
|any|\< `count`|any|`ERANGE`|`dest` 已清空|  
  
## 備註  
 `memcpy_s` 會將 `count` 位元組從 `src` 複製至 `dest`；`wmemcpy_s` 會複製 `count` 個寬字元 \(兩個位元組\)。 如果來源和目的地重疊，則 `memcpy_s` 的行為是未定義。 使用 `memmove_s` 處理重疊的區域。  
  
 這些函式會驗證它們的參數。 如果 `dest` 或 `src` 是 null 指標，或 `destSize` 小於 `count`, ，這些函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`memcpy_s`|\<memory.h\> 或 \<string.h\>|  
|`wmemcpy_s`|\<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_memcpy_s.c  
// Copy memory in a more secure way.  
  
#include <memory.h>  
#include <stdio.h>  
  
int main()  
{  
   int a1[10], a2[100], i;  
   errno_t err;  
  
   // Populate a2 with squares of integers  
   for (i = 0; i < 100; i++)  
   {  
      a2[i] = i*i;  
   }  
  
   // Tell memcpy_s to copy 10 ints (40 bytes), giving  
   // the size of the a1 array (also 40 bytes).  
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );      
   if (err)  
   {  
      printf("Error executing memcpy_s.\n");  
   }  
   else  
   {  
     for (i = 0; i < 10; i++)  
       printf("%d ", a1[i]);  
   }  
   printf("\n");  
}  
```  
  
```Output  
0 1 4 9 16 25 36 49 64 81   
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove、wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)