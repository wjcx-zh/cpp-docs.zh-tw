---
title: "memcpy_s、wmemcpy_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcpy_s
- wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemcpy_s
- memcpy_s
dev_langs: C++
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ac0b4cd7783cd41d480777fe8116a0facea58a28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="memcpys-wmemcpys"></a>memcpy_s、wmemcpy_s
複製緩衝區之間的位元組。 這些是 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `dest`  
 新的緩衝區。  
  
 `destSize`  
 memcpy_s 和寬字元 (wchar_t) 的 wmemcpy_s 之目的緩衝區大小 (以位元組為單位)。  
  
 `src`  
 要複製的緩衝區。  
  
 `count`  
 要複製的字元數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`dest`|`destSize`|`src`|`count`|傳回值|`dest` 的內容。|  
|------------|----------------|-----------|---|------------------|------------------------|  
|any|任何|任何|0|0|未修改|  
|`NULL`|任何|任何|非零|`EINVAL`|未修改|  
|任何|任何|`NULL`|非零|`EINVAL`|`dest` 已歸零|  
|任何|< `count`|任何|非零|`ERANGE`|`dest` 已歸零|  
  
## <a name="remarks"></a>備註  
 `memcpy_s` 會將 `count` 位元組從 `src` 複製至 `dest`；`wmemcpy_s` 會複製 `count` 個寬字元 (兩個位元組)。 如果來源和目的地重疊，則 `memcpy_s` 的行為是未定義。 使用 `memmove_s` 處理重疊的區域。  
  
 這些函式會驗證它們的參數。 如果 `count` 為非零且 `dest` 或 `src` 為 null 指標，或是 `destSize` 小於 `count`，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 `EINVAL` 或 `ERANGE`，並將 `errno` 設為傳回值。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`memcpy_s`|\<memory.h> 或 \<string.h>|  
|`wmemcpy_s`|\<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove、wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy、wcscpy、_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)