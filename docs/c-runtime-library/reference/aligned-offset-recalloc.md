---
title: _aligned_offset_recalloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c2586cdd836795a31e457edcba42292a6901ec6f
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc
變更使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。  
  
## <a name="syntax"></a>語法  
  
```  
void * _aligned_offset_recalloc(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 目前記憶體區塊指標。  
  
 `num`  
 項目數。  
  
 `size`  
 每個項目的長度 (位元組)。  
  
 `alignment`  
 對齊值，其必須是 2 的整數次方。  
  
 `offset`  
 記憶體配置中要強制對齊的位移。  
  
## <a name="return-value"></a>傳回值  
 `_aligned_offset_recalloc` 會傳回重新配置後 (且可能有移動) 記憶體區塊的 Void 指標。 若大小為 0，且緩衝區引數不是 `NULL`，則傳回值為 `NULL`，或者，若沒有足夠的可用記憶體將區塊展開為指定大小，傳回值也會是 NULL。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。  
  
 `_aligned_offset_recalloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="remarks"></a>備註  
 和 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 一樣，`_aligned_offset_recalloc` 也可讓結構對齊結構中的位移。  
  
 `_aligned_offset_recalloc` 是以 `malloc` 為基礎。 如需使用 `_aligned_offset_malloc` 的詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。 如果 `memblock` 是 `NULL`，則函式會在內部呼叫 `_aligned_offset_malloc`。  
  
 若記憶體配置失敗，或是要求的大小 (`num` * `size`) 大於 `_HEAP_MAXREQ`，則此函式會將 `errno` 設為 `ENOMEM`。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_recalloc` 也會驗證其參數。 如果 `alignment` 不是 2 的乘冪，或如果 `offset` 大於或等於要求的大小及非零值，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_aligned_offset_recalloc`|\<malloc.h>|  
  
## <a name="see-also"></a>另請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)   
 [_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)
