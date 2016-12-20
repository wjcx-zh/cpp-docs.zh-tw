---
title: "_aligned_offset_malloc | Microsoft Docs"
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
  - "_aligned_offset_malloc"
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
  - "_aligned_offset_malloc"
  - "aligned_offset_malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_offset_malloc 函式"
  - "aligned_offset_malloc 函式"
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的對齊界限配置記憶體。  
  
## 語法  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### 參數  
 \[in\] `size`  
 要求的記憶體配置大小。  
  
 \[in\] `alignment`  
 對齊值，必須為 2 的整數次方。  
  
 \[in\] `offset`  
 讓記憶體配置強制對齊的位移。  
  
## 傳回值  
 指向配置的記憶體區塊之指標。若作業失敗則為 `NULL` 。  
  
## 備註  
 `_aligned_offset_malloc` 適用於在巢狀項目需要對齊的情況；例如，如果在巢狀類別需要對齊時。  
  
 `_aligned_offset_malloc` 是根據 `malloc`；如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 `_aligned_offset_malloc` 會標示為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
 如果記憶體配置失敗或者要求大小大於 `_HEAP_MAXREQ`，這個函式會將 `errno` 設為 `ENOMEM`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外， `_aligned_offset_malloc` 會驗證其參數。  如果 `alignment` 不是 2 的次方，或 `offset` 大於或等於 `size` 並且不是零，這個函式會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_offset_malloc`|\<malloc.h\>|  
  
## 範例  
 如需詳細資訊，請參閱 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)