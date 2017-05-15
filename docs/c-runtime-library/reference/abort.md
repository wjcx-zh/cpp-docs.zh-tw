---
title: abort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- abort
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.assetid: a797783b-40ed-4bdb-a2cd-14ffede39e8a
caps.latest.revision: 24
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 18a683e6581f979c0383c76a3ada2a8e80316255
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="abort"></a>abort
中止目前的處理序，並傳回錯誤碼。  
  
> [!NOTE]
>  除非是測試或偵錯的狀況，否則不要使用這個方法關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式。 如需詳細資訊，請參閱[應用程式生命週期 (Windows 市集應用程式)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## <a name="syntax"></a>語法  
  
```  
void abort( void );  
```  
  
## <a name="return-value"></a>傳回值  
 `abort` 不會將控制權還給呼叫處理序。 根據預設，它會檢查是否有中止訊號處理常式；如有設定，則會引發 `SIGABRT`。 然後，`abort` 會終止目前的處理序，並將結束代碼傳回父處理序。  
  
## <a name="remarks"></a>備註  
 **Microsoft 特定的**  
  
 根據預設，當應用程式是以偵錯執行階段程式庫建置時，`abort` 常式會先顯示錯誤訊息，再引發 `SIGABRT`。 若是在主控台模式中執行的主控台應用程式，訊息會傳送至 `STDERR`。 在視窗模式中執行的 Windows 傳統型應用程式和主控台應用程式會在訊息方塊中顯示訊息。 若要隱藏訊息，請使用 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md) 清除 `_WRITE_ABORT_MSG` 旗標。 顯示的訊息取決於所使用的執行階段環境版本。 若是使用最新版 Visual C++ 建置的應用程式，訊息會類似如下：  
  
 `R6010`  
  
 `- abort() has been called`  
  
 在舊版 C 執行階段程式庫中，會顯示下列訊息：  
  
 "`This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.`"  
  
 當程式是在偵錯模式中編譯時，訊息方塊會顯示 [中止]、[重試] 或 [略過] 選項。 如果使用者選擇 [中止]，程式會立即終止，並傳回結束代碼 3。 如果使用者選擇 [重試]，則會叫用偵錯工具進行 Just-in-Time 偵錯 (如果有)。 如果使用者選擇 [略過]，`abort` 會繼續正常處理。  
  
 在零售和偵錯組建中，`abort` 會接著檢查是否已設定中止訊號處理常式。 如果設定了非預設訊號處理常式，`abort` 會呼叫 `raise(SIGABRT)`。 使用 [signal](../../c-runtime-library/reference/signal.md) 函式可建立中止訊號處理函式與 `SIGABRT` 訊號的關聯。 您可以執行自訂動作 (例如清除資源或記錄資訊)，然後終止應用程式並在處理函式中顯示您自己的錯誤碼。 如果未定義自訂訊號處理常式，`abort` 就不會引發 `SIGABRT` 訊號。  
  
 根據預設，在傳統型或主控台應用程式的非偵錯組建中，`abort` 會接著叫用 Windows 錯誤報告機制 (Dr.Watson) 向 Microsoft 報告失敗。 此行為可藉由呼叫 `_set_abort_behavior` 和設定來啟用，或藉由遮罩 `_CALL_REPORTFAULT` 旗標來停用。 設定旗標時，Windows 會顯示一個訊息方塊，其中包含類似「由於發生問題，導致程式停止正常運作」的文字。 使用者可以選擇使用 [偵錯] 按鈕叫用偵錯工具，或選擇 [關閉程式] 終止應用程式並顯示作業系統所定義的錯誤碼。  
  
 如果未叫用 Windows 錯誤報告處理常式，則 `abort` 會呼叫 [_exit](../../c-runtime-library/reference/exit-exit-exit.md) 以結束代碼 3 終止處理序，並且將控制權還給父處理序或作業系統。 `_exit` 不會排清資料流緩衝區，也不會進行 `atexit`/`_onexit` 處理。  
  
 如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`abort`|\<process.h> 或 \<stdlib.h>|  
  
## <a name="example"></a>範例  
 下列程式會嘗試開啟檔案，並在嘗試失敗時中止。  
  
```C  
// crt_abort.c  
// compile with: /TC  
// This program demonstrates the use of  
// the abort function by attempting to open a file  
// and aborts if the attempt fails.  
  
#include  <stdio.h>  
#include  <stdlib.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    errno_t err = 0;  
  
    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );  
    if ((err != 0) || (stream == NULL))  
    {  
        perror( "File could not be opened" );  
        abort();  
    }  
    else  
    {  
        fclose( stream );  
    }  
}  
```  
  
```Output  
File could not be opened: No such file or directory  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 abort](../../cpp/using-abort.md)   
 [abort 函式](../../c-language/abort-function-c.md)   
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [_DEBUG](../../c-runtime-library/debug.md)   
 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)
