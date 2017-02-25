---
title: "_aligned_recalloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_recalloc"
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
  - "aligned_recalloc"
  - "_aligned_recalloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_recalloc 函式"
  - "_aligned_recalloc 函式"
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更配置與 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 。  
  
## 語法  
  
```  
void * _aligned_recalloc(  
   void *memblock,   
   size_t num,  
   size_t size,   
   size_t alignment  
);  
```  
  
#### 參數  
 \[in\] `memblock`  
 目前的記憶體區塊指標。  
  
 \[in\] `num`  
 項目的數目。  
  
 \[in\] `size`  
 大小 \(單位為每個項目。  
  
 \[in\] `alignment`  
 對齊值，必須為 2 的整數次方。  
  
## 傳回值  
 `_aligned_recalloc` 傳回 Void 指標到重新配置 \(和可捲動\) 的記憶體區塊。  如果大小為零，而且緩衝區引數不是 `NULL`，或者，如果沒有展開區塊的足夠的記憶體可用對特定大小，傳回值為 `NULL` 。  如為前者，原始區塊被釋放。  在第二種情況下，未變更原始區塊。  傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要取得 void 之外的類型指標，請在傳回值上使用類型轉換。  
  
 它是重新配置記憶體和變更區塊對齊的錯誤。  
  
## 備註  
 `_aligned_recalloc` 以 `malloc`為基礎。  如需有關使用 `_aligned_offset_malloc` 的詳細資訊，請參閱[malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果記憶體配置失敗或者要求大小大於 `_HEAP_MAXREQ`，這個函式會將 `errno` 設為 `ENOMEM`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外， `_aligned_recalloc` 會驗證其參數。  如果 `alignment` 不是2的冪次方，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_recalloc`|\<malloc.h\>|  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)   
 [\_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)