---
title: _aligned_offset_realloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
dev_langs: C++
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b90b8b2ff057e42425825ae7d02b8d0901a5e45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="alignedoffsetrealloc"></a>_aligned_offset_realloc
變更使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小。  
  
## <a name="syntax"></a>語法  
  
```  
void * _aligned_offset_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 目前記憶體區塊指標。  
  
 `size`  
 記憶體配置的大小。  
  
 `alignment`  
 對齊值，其必須是 2 的整數次方。  
  
 `offset`  
 記憶體配置中要強制對齊的位移。  
  
## <a name="return-value"></a>傳回值  
 `_aligned_offset_realloc` 會傳回重新配置後 (且可能有移動) 記憶體區塊的 Void 指標。 若大小為 0，且緩衝區引數不是 `NULL`，則傳回值為 `NULL`，或者，若沒有足夠的可用記憶體將區塊展開為指定大小，傳回值也會是 NULL。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。  
  
 `_aligned_offset_realloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="remarks"></a>備註  
 和 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 一樣，`_aligned_offset_realloc` 也可讓結構對齊結構中的位移。  
  
 `_aligned_offset_realloc` 是以 `malloc` 為基礎。 如需使用 `_aligned_offset_malloc` 的詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。 如果 `memblock` 是 `NULL`，則函式會在內部呼叫 `_aligned_offset_malloc`。  
  
 若記憶體配置失敗，或是要求的大小大於 `errno`，則此函式會將 `ENOMEM` 設為 `_HEAP_MAXREQ`。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_realloc` 也會驗證其參數。 如果 `alignment` 不是 2 的乘冪，或如果 `offset` 大於或等於 `size` 及非零值，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_aligned_offset_realloc`|\<malloc.h>|  
  
## <a name="example"></a>範例  
 如需詳細資訊，請參閱 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)