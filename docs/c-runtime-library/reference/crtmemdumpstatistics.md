---
title: _CrtMemDumpStatistics | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 524c875f5cf25eb41d09e0f5dc99c32efcae8661
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics
針對採用使用者可讀格式的指定堆積狀態，傾印偵錯標頭資訊 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void _CrtMemDumpStatistics(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>參數  
 `state`  
 要傾印的堆積狀態指標。  
  
## <a name="remarks"></a>備註  
 `_CrtMemDumpStatistics` 函式會針對採用使用者可讀格式的指定堆積狀態，傾印偵錯標頭資訊。 應用程式會使用此傾印統計資料追蹤配置及偵測記憶體問題。 記憶體狀態可能包含特定堆積狀態或兩個狀態之間的差異。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtMemDumpStatistics` 的呼叫。  
  
 `state` 參數必須是指向 `_CrtMemState` 結構的指標，該結構已由 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填入或由 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) 傳回再呼叫 `_CrtMemDumpStatistics`。 如果 `state` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則 `errno` 會設定為 `EINVAL` ，而且不會採取任何動作。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需堆積狀態函式和 `_CrtMemState` 結構的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需如何在偵錯版本的基底堆積中配置、初始化和管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`_CrtMemDumpStatistics`|\<crtdbg.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
