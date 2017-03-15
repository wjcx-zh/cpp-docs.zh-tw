---
title: _query_new_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 10
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 38b5022412f3f07806fcb7a2cea373457c8b405f
ms.lasthandoff: 02/24/2017

---
# <a name="querynewmode"></a>_query_new_mode
傳回整數，此整數表示 `_set_new_mode` 為 `malloc` 所設定的新處理常式模式。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>傳回值  
 傳回 `malloc` 的目前新處理常式模式，也就是 0 或 1。 傳回值 1 表示無法配置記憶體時，`malloc` 會呼叫新的處理常式模式；傳回值 0 則表示不會呼叫。  
  
## <a name="remarks"></a>備註  
 C++ `_query_new_mode` 函式會傳回整數，此整數表示 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式為 [malloc](../../c-runtime-library/reference/malloc.md) 所設定的新處理常式模式。 此新的處理常式模式會指出無法配置記憶體時，`malloc` 是否會呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`malloc` 不會在失敗時呼叫新處理常式。 您可以用 `_set_new_mode` 覆寫這個行為，以便在失敗時，`malloc` 會呼叫新處理常式，就和 **new** 運算子在無法配置記憶體時所執行的方法相同。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_query_new_mode`|\<new.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)
