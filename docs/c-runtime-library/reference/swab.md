---
title: _swab | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01f23047436b7ff8cee16b42cc6ae0d8c2a9fd78
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="swab"></a>_swab
交換位元組。  
  
## <a name="syntax"></a>語法  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
## <a name="parameters"></a>參數  
 `src`  
 要複製並交換的資料。  
  
 `dest`  
 交換資料的儲存位置。  
  
 `n`  
 要複製並交換的位元組數目。  
  
## <a name="return-value"></a>傳回值
 `swab` 函式未傳回值。 如果 `src` 或 `dest` 指標為 NULL，或是 `n` 小於零，且叫用無效的參數處理常式，函式會將 `errno` 設定為 `EINVAL`，如 [ 參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需這個及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。
 
## <a name="remarks"></a>備註  
 如果 `n` 為偶數，`_swab` 函式會從 `src` 複製 `n` 個位元組、交換每一對相鄰的位元組，然後將結果儲存在 `dest`。 如果 `n` 是奇數，`_swab` 會複製並交換 `src` 的前 `n-1` 個位元組，且不會複製最後一個位元組。 `_swab` 函式通常用來準備要傳輸到使用不同位元組順序之機器的二進位資料。  
  
## <a name="requirements"></a>需求  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_swab`|C: \<stdlib.h> C++: \<cstdlib> 或 \<stdlib.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
```C 
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "...........................";  
  
int main()  
{  
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);  
    _swab(from, to, sizeof(from));  
    printf("After:  %s\n        %s\n\n", from, to);  
}  
```  
  
```Output  
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes  
        ...........................  
  
After:  BADCFEHGJILKNMPORQTSVUXWZY  
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.  
```  
  
## <a name="see-also"></a>請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)