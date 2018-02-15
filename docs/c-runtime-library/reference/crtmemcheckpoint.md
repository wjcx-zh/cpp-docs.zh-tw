---
title: _CrtMemCheckpoint | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
dev_langs:
- C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37333b2b4621b9434a9fe1a924162957d5ea824f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint
取得偵錯堆積的目前狀態，並儲存在應用程式提供的 `_CrtMemState` 結構中 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>參數  
 `state`  
 指向 `_CrtMemState` 結構以填入記憶體檢查點。  
  
## <a name="remarks"></a>備註  
 `_CrtMemCheckpoint` 函式會建立任何指定時間之偵錯堆積目前狀態的快照。 其他堆積狀態函式 (例如 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) ) 可使用此快照協助偵測記憶體流失及其他問題。 若未定義 [_DEBUG](../../c-runtime-library/debug.md) ，將會在前置處理期間移除對 `_CrtMemState` 的呼叫。  
  
 應用程式必須將指標傳遞至先前配置之 `_CrtMemState` 結構的執行個體，其定義在 Crtdbg.h 的 `state` 參數中。 如果 `_CrtMemCheckpoint` 在檢查點建立期間遇到錯誤，函式會產生描述問題的 `_CRT_WARN` 偵錯報告。  
  
 如需堆積狀態函式及 `_CrtMemState` 結構的詳細資訊，請參閱 [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
 如果 `state` 為 `NULL`，將會叫用無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會設定為 `EINVAL`，並傳回函式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>、\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
 **程式庫：** 僅限 UCRT 的偵錯版本。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)