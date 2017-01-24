---
title: "_aligned_malloc | Microsoft Docs"
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
  - "_aligned_malloc"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_aligned_malloc"
  - "alligned_malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_malloc 函式"
  - "aligned_malloc 函式"
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對指定的對齊界限配置記憶體。  
  
## 語法  
  
```  
void * _aligned_malloc(  
    size_t size,   
    size_t alignment  
);  
```  
  
#### 參數  
 `size`  
 要求的記憶體配置大小。  
  
 `alignment`  
 對齊值，其必須是 2 的整數次方。  
  
## 傳回值  
 已配置之記憶體區塊的指標，或為 `NULL` \(作業失敗時\)。  指標是 `alignment` 的倍數。  
  
## 備註  
 `_aligned_malloc` 是以 [malloc](../../c-runtime-library/reference/malloc.md) 為基礎。  
  
 `_aligned_malloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
 若記憶體配置失敗，或是要求的大小大於 `errno`，則此函式會將 `ENOMEM` 設為 `_HEAP_MAXREQ`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_malloc` 也會驗證其參數。  如果 `alignment` 不是 2 的乘冪，或 `size` 為零，則此函式會叫用無效參數處理常式 \(如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述\)。  若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_malloc`|\<malloc.h\>|  
  
## 範例  
  
```  
// crt_aligned_malloc.c  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main() {  
    void    *ptr;  
    size_t  alignment,  
            off_set;  
  
    // Note alignment should be 2^N where N is any positive int.  
    alignment = 16;  
    off_set = 5;  
  
    // Using _aligned_malloc  
    ptr = _aligned_malloc(100, alignment);  
    if (ptr == NULL)  
    {  
        printf_s( "Error allocation aligned memory.");  
        return -1;  
    }  
    if (((unsigned long long)ptr % alignment ) == 0)  
        printf_s( "This pointer, %p, is aligned on %zu\n",  
                  ptr, alignment);  
    else  
        printf_s( "This pointer, %p, is not aligned on %zu\n",   
                  ptr, alignment);  
  
    // Using _aligned_realloc  
    ptr = _aligned_realloc(ptr, 200, alignment);  
    if ( ((unsigned long long)ptr % alignment ) == 0)  
        printf_s( "This pointer, %p, is aligned on %zu\n",  
                  ptr, alignment);  
    else  
        printf_s( "This pointer, %p, is not aligned on %zu\n",   
                  ptr, alignment);  
    _aligned_free(ptr);  
  
    // Using _aligned_offset_malloc  
    ptr = _aligned_offset_malloc(200, alignment, off_set);  
    if (ptr == NULL)  
    {  
        printf_s( "Error allocation aligned offset memory.");  
        return -1;  
    }  
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)  
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",  
                  ptr, off_set, alignment);  
    else  
        printf_s( "This pointer, %p, does not satisfy offset %zu "  
                  "and alignment %zu\n",ptr, off_set, alignment);  
  
    // Using _aligned_offset_realloc  
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);  
    if (ptr == NULL)  
    {  
        printf_s( "Error reallocation aligned offset memory.");  
        return -1;  
    }  
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)  
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",  
                  ptr, off_set, alignment);  
    else  
        printf_s( "This pointer, %p, does not satisfy offset %zu and "  
                  "alignment %zu\n", ptr, off_set, alignment);  
  
    // Note that _aligned_free works for both _aligned_malloc  
    // and _aligned_offset_malloc. Using free is illegal.  
    _aligned_free(ptr);  
}  
```  
  
  **This pointer, 3280880, is aligned on 16**  
**This pointer, 3280880, is aligned on 16**  
**This pointer, 3280891, is offset by 5 on alignment of 16**  
**This pointer, 3280891, is offset by 5 on alignment of 16**   
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)