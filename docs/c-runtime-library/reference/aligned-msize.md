---
title: _aligned_msize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 375eb2921ac47be819eeb050fa87643c50a52289
ms.lasthandoff: 02/24/2017

---
# <a name="alignedmsize"></a>_aligned_msize
傳回堆積中所配置的記憶體區塊大小。  
  
## <a name="syntax"></a>語法  
  
```  
size_t _msize(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `memblock`  
 記憶體區塊的指標。  
  
 [in] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 [in] `offset`  
 記憶體配置中要強制對齊的位移。  
  
## <a name="return-value"></a>傳回值  
 傳回不帶正負號的整數大小 (以位元組為單位)。  
  
## <a name="remarks"></a>備註  
 `_aligned_msize` 函式會傳回以位元組為單位的記憶體區塊大小，由 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_realloc](../../c-runtime-library/reference/aligned-realloc.md) 呼叫所配置。 `alignment` 和 `offset` 值必須與傳遞至配置區塊函式的值相同。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`_aligned_msize` 會解析為 [_aligned_msize_dbg](../../c-runtime-library/reference/aligned-msize-dbg.md)。 如需在偵錯程序期間如何管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 這個函式會驗證其參數。 如果 `memblock` 為 Null 指標，或 `alignment` 不是 2 的乘冪，則 `_msize` 會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果已處理錯誤，則此函式會將 `errno` 設為 `EINVAL` 並傳回 -1。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_msize`|\<malloc.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)
