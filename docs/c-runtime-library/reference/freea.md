---
title: _freea | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _freea
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
- freea
- _freea
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 18
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: bd53960a97cc6647008b683e354df664941428e9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="freea"></a>_freea
取消配置或釋放記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 要釋放之先前配置的記憶體區塊。  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="remarks"></a>備註  
 `_freea` 函式會取消配置 [_malloca](../../c-runtime-library/reference/malloca.md) 呼叫先前所配置的記憶體區塊 (`memblock`)。 `_freea` 確認是否在堆積或堆疊上配置記憶體。 如果配置於堆疊，則 `_freea` 不會執行任何動作。 如果配置於堆積，所釋放的位元組數目相當於配置區塊時所要求的位元組數目。 如果 `memblock` 是 `NULL`，則會忽略指標，並立即傳回 `_freea`。 嘗試釋放無效指標 (未由 `_malloca` 所配置之記憶體區塊的指標) 可能會影響後續配置要求，並導致錯誤。  
  
 `_freea`呼叫`free`內部如果找到，在堆積上配置記憶體。 記憶體在堆積還是堆疊上取決於在記憶體之已配置記憶體正前方的位址所放置的標記。  
  
 若釋放記憶體發生錯誤，會使用來自作業系統且具有失敗性質的資訊設定 `errno`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 釋放記憶體區塊之後，[_heapmin](../../c-runtime-library/reference/heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。  
  
 `_freea` 呼叫必須伴隨所有 `_malloca` 呼叫。 它也是在相同記憶體上呼叫 `_freea` 兩次的錯誤。 當應用程式與偵錯版本的 C 執行階段程式庫相連結時 (特別是使用藉由定義 `_CRTDBG_MAP_ALLOC` 所啟用的 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) 功能)，較容易找到遺漏或重複的 `_freea` 呼叫。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `_freea` 標記為 `__declspec(noalias)`，表示保證函式不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_malloca](../../c-runtime-library/reference/malloca.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)
