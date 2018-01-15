---
title: _CrtIsMemoryBlock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
dev_langs: C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec6bea115ba509c7275a2d220cf4b10c6faecae9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock
確認指定的記憶體區塊位於本機堆積，且具有有效的偵錯堆積區塊類型識別項 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `userData`  
 要確認之記憶體區塊開頭的指標。  
  
 [輸入] `size`  
 指定區塊的大小 (以位元組為單位)。  
  
 [輸出] `requestNumber`  
 區塊之配置數目的指標，或為 `NULL`。  
  
 [輸出] `filename`  
 要求區塊之原始程式檔名的指標，或為 `NULL`。  
  
 [輸出] `linenumber`  
 原始程式檔中行號的指標，或為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 如果指定的記憶體區塊位於本機堆積，且具有有效的偵錯堆積區塊類型識別項，`_CrtIsMemoryBlock` 會傳回 `TRUE`；否則函式會傳回 `FALSE`。  
  
## <a name="remarks"></a>備註  
 `_CrtIsMemoryBlock` 函式會確認指定的記憶體區塊位於應用程式的本機堆積，且具有有效的區塊類型識別項。 此函式也可用來取得物件配置順序編號，以及原始要求記憶體區塊配置的原始程式檔名/行號。 針對 `requestNumber`、`filename` 或 `linenumber` 參數傳遞非 NULL 值，會導致 `_CrtIsMemoryBlock` 將這些參數設定為記憶體區塊偵錯標頭中的值 (如果在本機堆積中找到此區塊)。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtIsMemoryBlock` 的呼叫。  
  
 如果 `_CrtIsMemoryBlock` 失敗，它會傳回 `FALSE` 且輸出參數會初始化為預設值︰`requestNumber` 和 `lineNumber` 會設定為 0，而 `filename` 會設定為 `NULL`。  
  
 因為此函式會傳回 `TRUE` 或 `FALSE`，所以可將該函式傳遞至其中一個 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 如果指定的位址不在本機堆積內，則下列範例會造成判斷提示失敗：  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 如需如何搭配其他偵錯函式和巨集使用 `_CrtIsMemoryBlock` 的詳細資訊，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 主題的範例。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)