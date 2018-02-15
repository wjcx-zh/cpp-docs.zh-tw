---
title: _aligned_msize_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_msize_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0c26a876f6ef4f77d4f9c649a3993fe666cb6f3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
傳回堆積中所配置的記憶體區塊大小 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `memblock`  
 記憶體區塊的指標。  
  
 [輸入] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 [in] `offset`  
 記憶體配置中要強制對齊的位移。  
  
## <a name="return-value"></a>傳回值  
 傳回不帶正負號的整數大小 (以位元組為單位)。  
  
## <a name="remarks"></a>備註  
 `alignment` 和 `offset` 值必須與傳遞至配置區塊函式的值相同。  
  
 `_aligned_msize_dbg` 是 [_aligned_msize](../../c-runtime-library/reference/aligned-msize.md) 函式的偵錯版本。 當 [_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_msize_dbg` 的呼叫會降至 `_aligned_msize` 的呼叫。 `_aligned_msize` 和 `_aligned_msize_dbg` 都會計算基底堆積中的記憶體區塊大小，但 `_aligned_msize_dbg` 增加了偵錯功能：在傳回大小的記憶體區塊使用者部分的任一端包含緩衝區。  
  
 這個函式會驗證其參數。 如果 `memblock` 為 Null 指標，或 `alignment` 不是 2 的乘冪，則 `_msize` 會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果已處理錯誤，則此函式會將 `errno` 設為 `EINVAL` 並傳回 -1。  
  
 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)