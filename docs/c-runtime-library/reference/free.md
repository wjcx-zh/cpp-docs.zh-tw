---
title: free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- free
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
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fa01be1421c4b241a86a02e97cb444404ce8f734
ms.lasthandoff: 02/24/2017

---
# <a name="free"></a>free
取消配置或釋放記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 要釋放之先前配置的記憶體區塊。  
  
## <a name="remarks"></a>備註  
 `free` 函式會取消配置 `calloc`、`malloc` 或 `realloc` 呼叫先前所配置的記憶體區塊 (`memblock`)。 所釋放的位元組數目相當於配置 (或重新配置，如果為 `realloc`) 區塊時所要求的位元組數目。 如果 `memblock` 是 `NULL`，則會忽略指標，並立即傳回 `free`。 嘗試釋放無效指標 (`calloc`、`malloc` 或 `realloc` 未配置之記憶體區塊的指標) 可能會影響後續配置要求，並導致錯誤。  
  
 若釋放記憶體發生錯誤，會使用來自作業系統且具有失敗性質的資訊設定 `errno`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 釋放記憶體區塊之後，[_heapmin](../../c-runtime-library/reference/heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`free` 會解析為 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `free` 標記為 `__declspec(noalias)`，表示保證函式不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。  
  
 若要釋放使用 [_malloca](../../c-runtime-library/reference/malloca.md) 所配置的記憶體，請使用 [_freea](../../c-runtime-library/reference/freea.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`free`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [malloc](../../c-runtime-library/reference/malloc.md) 的範例。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_freea](../../c-runtime-library/reference/freea.md)
