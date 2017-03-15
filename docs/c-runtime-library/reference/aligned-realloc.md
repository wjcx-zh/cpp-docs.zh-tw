---
title: "_aligned_realloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_realloc"
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
  - "_aligned_realloc"
  - "aligned_realloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_realloc 函式"
  - "_aligned_realloc 函式"
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _aligned_realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 配置的記憶體區塊大小。  
  
## 語法  
  
```  
void * _aligned_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment  
);  
```  
  
#### 參數  
 \[in\] `memblock`  
 目前的記憶體區塊指標。  
  
 \[in\] `size`  
 要求的記憶體配置大小。  
  
 \[in\] `alignment`  
 對齊值，必須為 2 的整數次方。  
  
## 傳回值  
 `_aligned_realloc` 傳回 Void 指標到重新配置 \(和可捲動\) 的記憶體區塊。  如果大小為零，而且緩衝區引數不是 `NULL`，或者，如果沒有展開區塊的足夠的記憶體可用對特定大小，傳回值為 `NULL` 。  如為前者，原始區塊被釋放。  在第二種中，未變更原始區塊。  傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要取得 void 之外的類型指標，請在傳回值上使用類型轉換。  
  
 它是重新配置記憶體和變更區塊對齊的錯誤。  
  
## 備註  
 `_aligned_realloc` 以 `malloc`為基礎。  如需有關使用 `_aligned_offset_malloc` 的詳細資訊，請參閱[malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果記憶體配置失敗或者要求大小大於 `_HEAP_MAXREQ`，這個函式會將 `errno` 設為 `ENOMEM`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外， `_aligned_realloc` 會驗證其參數。  如果 `alignment` 不是2的冪次方，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_realloc`|\<malloc.h\>|  
  
## 範例  
 如需詳細資訊，請參閱 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)