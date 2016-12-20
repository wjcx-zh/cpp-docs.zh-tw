---
title: "abort | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "abort"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "abort 函式"
  - "中止目前處理序"
  - "處理序, 中止"
ms.assetid: a797783b-40ed-4bdb-a2cd-14ffede39e8a
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# abort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

中止目前的處理序並傳回錯誤碼。  
  
> [!NOTE]
>  除非是測試或偵錯的狀況，否則不要使用這個方法關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  如需詳細資訊，請參閱[應用程式週期 \(Windows 市集應用程式\)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 語法  
  
```  
void abort( void );  
```  
  
## 傳回值  
 `abort` 不會將控制權歸還給呼叫處理序。  根據預設，它會檢查終止訊號處理常式並引發 `SIGABRT` \(如果有的話\)。  `abort` 結束目前的處理序並傳回結束代碼至父處理序。  
  
## 備註  
 **Microsoft 專有的**  
  
 根據預設，使用偵錯執行階段程式庫建置應用程式時， `abort` 常式會在引發 `SIGABRT` 之前顯示錯誤訊息。  針對以主控台模式執行的主控台應用程式，訊息會傳送至 `STDERR`。  Windows 桌面應用程式以及以視窗型模式執行的主控台應用程式會在訊息方塊中顯示此訊息。  若要隱藏訊息，請使用 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md) 清除 `_WRITE_ABORT_MSG` 旗標。  顯示的訊息取決於使用的執行階段環境版本。  針對使用最新版 Visual C\+\+ 建置的應用程式，訊息會像這樣：  
  
 `R6010`  
  
 `- abort() has been called`  
  
 在舊版 C 執行階段程式庫中，會顯示這個訊息：  
  
 「`This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.`」  
  
 當程式以偵錯模式編譯時，訊息方塊會顯示 \[**中止**\]、\[**重試**\] 和 \[**忽略**\] 選項。  如果使用者選擇 \[**中止**\]，程式會立即終止並傳回結束代碼 3。  如果使用者選擇 \[**重試**\]，則會叫用偵錯工具進行 Just\-In\-Time 偵錯 \(如有的話\)。  如果使用者選擇 \[**忽略**\]，`abort` 會繼續正常處理。  
  
 在零售和偵錯組建中，都會`abort`， 然後檢查中止訊號處理常式是否已設定。  如果設定了非預設訊號處理常式，則 `abort` 會呼叫 `raise(SIGABRT)`。  使用 [signal](../../c-runtime-library/reference/signal.md) 函式，使中止訊號處理函式與 `SIGABRT` 信號關聯。  您可以執行自訂動作 \(例如，清除資源或記錄資訊\) 和以處理函式中您的錯誤碼終止應用程式。  如果未定義自訂訊號處理常式，`abort` 就不會引發 `SIGABRT` 訊號。  
  
 根據預設，在非偵錯組建的桌面或主控台應用程式中， `abort` 會接著叫用 Windows 錯誤報告機制 \(Dr.  Watson\)，向 Microsoft 回報失敗。  可以透過呼叫 `_set_abort_behavior` 和設定或遮罩 `_CALL_REPORTFAULT` 旗標，啟用或停用這個行為。  當旗標設定時，Windows 會顯示類似於「由於發生問題，導致程式停止正常運作」文字的訊息方塊。使用者可以選擇使用 \[**偵錯**\] 按鈕叫用偵錯工具，或選擇 \[**關閉程式**\] 按鈕以結束有作業系統定義之錯誤碼的應用程式。  
  
 如果未叫用 Windows 錯誤報告處理常式，則 `abort` 會呼叫 [\_exit](../../c-runtime-library/reference/exit-exit-exit.md) 終止處理序且產生結束代碼 3，並且將控制項傳回至父處理序或作業系統。  `_exit` 不清除資料流緩衝區也不做 `atexit`\/`_onexit` 處理。  
  
 如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](../Topic/CRT%20Debugging%20Techniques.md)。  
  
 **結束 Microsoft 專有**  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`abort`|\<process.h\> 或 \<stdlib.h\>|  
  
## 範例  
 下列程式會嘗試開啟檔案，如果嘗試失敗則中止。  
  
```c  
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
  
  **無法開啟檔案：沒有這類檔案或目錄**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [使用 abort](../../cpp/using-abort.md)   
 [abort 函式](../../c-language/abort-function-c.md)   
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)   
 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md)