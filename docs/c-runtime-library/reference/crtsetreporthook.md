---
title: _CrtSetReportHook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
dev_langs: C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c1fb85ab41c02bb9f604f024f86ebb42706eeda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook
將用戶端定義的報告函式連結到 C 執行階段偵錯報告處理序，以進行安裝 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### <a name="parameters"></a>參數  
 `reportHook`  
 要連結到 C 執行階段偵錯報告處理序的新用戶端定義報告函式。  
  
## <a name="return-value"></a>傳回值  
 傳回上一個用戶端定義的報告函式。  
  
## <a name="remarks"></a>備註  
 `_CrtSetReportHook` 可讓應用程式將自己的報告函式用於 C 執行階段偵錯程式庫報告處理序。 因此，每當呼叫 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 產生偵錯報告時，都會先呼叫應用程式的報告函式。 這項功能可讓應用程式執行類似如下的作業：篩選偵錯報告以專注於特定配置類型，或是將報表傳送至使用 `_CrtDbgReport` 所未提供的目的地。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetReportHook` 的呼叫。  
  
 如需 `_CrtSetReportHook` 的更強固版本，請參閱 [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)。  
  
 `_CrtSetReportHook` 函式會安裝 `reportHook` 中指定的新用戶端定義報告函式，並傳回先前的用戶端定義攔截程序。 下列範例示範用戶端定義的報表攔截程序應如何設計原型：  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 其中 `reportType` 是偵錯報告類型 (`_CRT_WARN`、`_CRT_ERROR` 或 `_CRT_ASSERT`)，`message` 是要包含在報表中之完整組合的偵錯使用者訊息，而 `returnValue` 是用戶端定義的報告函式所指定的值，應由 `_CrtDbgReport` 傳回。 如需可用報表類型的完整說明，請參閱 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函式。  
  
 如果用戶端定義的報告函式可以完全處理偵錯訊息，而不需要進一步的報告，則函式應傳回 `TRUE`。 如果函式傳回 `FALSE`，就會呼叫 `_CrtDbgReport` 使用報表類型、模式和檔案的目前設定來產生偵錯報告。 此外，藉由在 `returnValue` 中指定 `_CrtDbgReport` 傳回值，應用程式也可以控制是否會發生偵錯中斷的情況。 如需如何設定及產生偵錯報告的完整說明，請參閱 `_CrtSetReportMode`、[_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 和 `_CrtDbgReport`。  
  
 如需使用支援攔截程序之其他執行階段函式，以及撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。  
  
> [!NOTE]
>  如果您的應用程式是以 `/clr` 編譯，而且在應用程式結束 main 之後呼叫報告函式，CLR 將會在報告函式呼叫任何 CRT 函式時擲回例外狀況。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtSetReportHook`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)