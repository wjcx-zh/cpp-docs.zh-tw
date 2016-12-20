---
title: "_aligned_offset_recalloc | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_recalloc"
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
  - "aligned_offset_recalloc"
  - "_aligned_offset_recalloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_offset_recalloc 函式"
  - "_aligned_offset_recalloc 函式"
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更配置與 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 。  
  
## 語法  
  
```  
void * _aligned_offset_recalloc(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### 參數  
 `memblock`  
 目前的記憶體區塊指標。  
  
 `num`  
 項目數  
  
 `size`  
 位元組長度。每個項目。  
  
 `alignment`  
 對齊值，必須為 2 的整數次方。  
  
 `offset`  
 讓記憶體配置強制對齊的位移。  
  
## 傳回值  
 `_aligned_offset_recalloc` 傳回 Void 指標到重新配置 \(和可捲動\) 的記憶體區塊。  如果大小為零，而且緩衝區引數不是 `NULL`，或者，如果沒有展開區塊的足夠的記憶體可用對特定大小，傳回值為 `NULL` 。  如為前者，原始區塊被釋放。  在第二種情況下，未變更原始區塊。  傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要取得 void 之外的類型指標，請在傳回值上使用類型轉換。  
  
 `_aligned_offset_recalloc` 會標示為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## 備註  
 像 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md)， `_aligned_offset_recalloc` 允許結構能夠於結構的位移中對齊。  
  
 `_aligned_offset_recalloc` 以 `malloc`為基礎。  如需有關使用 `_aligned_offset_malloc` 的詳細資訊，請參閱[malloc](../../c-runtime-library/reference/malloc.md)。  如果 `memblock` 是 `NULL`，函式內部呼叫 `_aligned_offset_malloc` 。  
  
 如果記憶體配置失敗或者要求大小 \(`num` \* `size`\)大於`_HEAP_MAXREQ`，這個函式會將 `errno` 設為 `ENOMEM`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外， `_aligned_offset_recalloc` 會驗證其參數。  如果 `alignment` 不是 2 的次方，或 `offset` 大於或等於要求的大小且非零，這個函式會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這個函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_offset_recalloc`|\<malloc.h\>|  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)   
 [\_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [\_aligned\_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)