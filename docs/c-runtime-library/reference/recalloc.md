---
title: _recalloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _recalloc
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
- _recalloc
- recalloc
dev_langs:
- C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: 9
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
ms.openlocfilehash: 89626019b42a478b2dfe3800e2f732ba6b90d106
ms.lasthandoff: 02/24/2017

---
# <a name="recalloc"></a>_recalloc
結合 `realloc` 和 `calloc`。 重新配置記憶體中的陣列，並將其項目初始化為 0。  
  
## <a name="syntax"></a>語法  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 先前配置之記憶體區塊的指標。  
  
 `num`  
 項目數。  
  
 `size`  
 每個項目的長度 (位元組)。  
  
## <a name="return-value"></a>傳回值  
 `_recalloc` 會傳回重新配置後 (且可能有移動) 記憶體區塊的 `void` 指標。  
  
 如果沒有足夠的可用記憶體將區塊展開為指定大小，原始區塊會保持不變，並傳回 `NULL`。  
  
 如果要求的大小為零，則會釋放 `memblock` 所指向的區塊；傳回值是 `NULL`，且 `memblock` 保持指向已釋放的區塊。  
  
 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 `void` 以外之類型的指標，請對傳回值使用類型轉換。  
  
## <a name="remarks"></a>備註  
 _`recalloc` 函式會變更已配置的記憶體區塊的大小。 `memblock` 引數指向記憶體區塊的開頭。 如果 `memblock` 為 `NULL`，則 \_`recalloc` 的行為方式與 [calloc](../../c-runtime-library/reference/calloc.md) 相同，並且會配置 `num` * `size` 個位元組的新區塊。 每個元素都會初始化為 0。 如果 `memblock` 不是 `NULL`，它應該是由先前呼叫 `calloc`、[malloc](../../c-runtime-library/reference/malloc.md) 或 [realloc](../../c-runtime-library/reference/realloc.md) 所傳回的指標。  
  
 因為新區塊可能會在新的記憶體位置，所以 _`recalloc` 傳回的指標並不保證是透過 `memblock` 引數傳遞的指標。  
  
 如果記憶體配置失敗，或所要求的記憶體數量超過 `_HEAP_MAXREQ`，`_recalloc` 會將 `errno` 設定為 `ENOMEM`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `recalloc` 會呼叫 `realloc` 以使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式來設定新的處理常式模式。 此新的處理常式模式會指出失敗時，`realloc` 是否會呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`realloc` 不會在失敗時呼叫新的處理常式來配置記憶體。 您可以覆寫這個預設行為，因此，在 _`recalloc` 無法配置記憶體時，`realloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 若要覆寫預設值，請及早在程式中呼叫  
  
```  
_set_new_mode(1)  
```  
  
 或與 NEWMODE.OBJ 連結。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，_`recalloc` 會解析為 [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `_recalloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_recalloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [連結選項](../../c-runtime-library/link-options.md)
