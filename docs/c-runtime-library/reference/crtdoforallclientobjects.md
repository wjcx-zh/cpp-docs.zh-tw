---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs: C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dff8b99d6378928583cea0c5eec7d69130c56557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects
針對堆積中的所有 `_CLIENT_BLOCK` 類型呼叫應用程式提供的函式 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void _CrtDoForAllClientObjects(   
   void ( * pfn )( void *, void * ),  
   void *context  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfn`  
 應用程式提供的函式回呼函式的指標。 此函式的第一個參數指向資料。 第二個參數是傳遞至 `_CrtDoForAllClientObjects`呼叫的內容指標。  
  
 `context`  
 要傳遞至應用程式提供之函式的應用程式提供的內容的指標。  
  
## <a name="remarks"></a>備註  
 `_CrtDoForAllClientObjects` 函式會在堆積的連結清單中搜尋具有 `_CLIENT_BLOCK` 類型的記憶體區塊，並在找到此類型的區塊時，呼叫應用程式提供的函式。 找到的區塊和 `context` 參數會作為引數傳遞至應用程式提供的函式。 應用程式可以在偵錯期間追蹤特定配置群組，方法是透過明確呼叫偵錯堆積函式以配置記憶體，並為區塊指定分派 `_CLIENT_BLOCK` 區塊類型。 然後就可以分別追蹤這些區塊，並在遺漏偵測期間和記憶體狀態報告期間個別回報這些區塊。  
  
 若 `_CRTDBG_ALLOC_MEM_DF` 旗標的 [_CRTDBG_ALLOC_MEM_DF](../../c-runtime-library/crtdbgflag.md) 位元欄位未開啟，會立即傳回 `_CrtDoForAllClientObjects` 。 若未定義 [_DEBUG](../../c-runtime-library/debug.md) ，將會在前置處理期間移除對 `_CrtDoForAllClientObjects` 的呼叫。  
  
 如需 `_CLIENT_BLOCK` 類型及其他偵錯函式可以如何使用該類型的詳細資訊，請參閱 [Types of blocks on the debug heap](/visualstudio/debugger/crt-debug-heap-details)呼叫的內容指標。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
 若 `pfn` 為 `NULL`，將會叫用無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)呼叫的內容指標。 如果允許繼續執行，[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會設定為 `EINVAL`，並傳回函式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtDoForAllClientObjects`|\<crtdbg.h>、\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
 **程式庫：** 僅限偵錯版的 C 執行階段程式庫。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)   
 [堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)