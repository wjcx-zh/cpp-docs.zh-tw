---
title: _aligned_offset_malloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7322f5a3fbf7bf3d9352181a68db17fad4bc9fcb
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc
針對指定的對齊界限配置記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `size`  
 要求的記憶體配置的大小。  
  
 [in] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 [in] `offset`  
 記憶體配置中要強制對齊的位移。  
  
## <a name="return-value"></a>傳回值  
 已配置之記憶體區塊的指標，或為 `NULL` (作業失敗時)。  
  
## <a name="remarks"></a>備註  
 `_aligned_offset_malloc` 適用於巢狀元素需要對齊的情況，例如，如果巢狀類別需要對齊時。  
  
 `_aligned_offset_malloc` 是以 `malloc` 為基礎，如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 `_aligned_offset_malloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
 若記憶體配置失敗，或是要求的大小大於 `errno`，則此函式會將 `ENOMEM` 設為 `_HEAP_MAXREQ`。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_malloc` 也會驗證其參數。 如果 `alignment` 不是 2 的乘冪，或如果 `offset` 大於或等於 `size` 及非零值，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_aligned_offset_malloc`|\<malloc.h>|  
  
## <a name="example"></a>範例  
 如需詳細資訊，請參閱 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)
