---
title: "signal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "signal"
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
  - "signal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "signal 函式"
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# signal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定中斷信號處理。  
  
> [!IMPORTANT]
>  除非是測試或偵錯的狀況，否則不要使用這個方法關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)的章節 3.6，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  如需詳細資訊，請參閱[應用程式週期 \(Windows 市集應用程式\)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 語法  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### 參數  
 `sig`  
 訊號值。  
  
 `func`  
 要執行的函式。  第一個參數是一個訊號值，第二個參數是一個當第一個參數為 SIGFPE 時使用的次代碼。  
  
## 傳回值  
 `signal` 回傳 `func` 先前與給定信號相關聯的值。  例如，若 `func` 之前的值為 `SIG_IGN` ，回傳的值也會是 `SIG_IGN` 。   `SIG_ERR` 的回傳值表示發生錯誤，這種情況下 `errno` 會被設置為 `EINVAL` 。  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `signal` 函式允許處理程序從多種由作業系統處理中斷訊號的方式中選擇其一。  `sig` 參數是 `signal` 所回應的中斷，它必須是下列定義於 SIGNAL.H 的表示常值中之一。  
  
|`sig` 值|描述|  
|-------------|--------|  
|`SIGABRT`|異常終止|  
|`SIGFPE`|浮點數錯誤|  
|`SIGILL`|不合法的指令|  
|`SIGINT`|CTRL\+C 訊號|  
|`SIGSEGV`|不合法的儲存體存取|  
|`SIGTERM`|終止要求|  
  
 如果 `sig` 不是上列裏的一個值，無效參數處理常式會被調用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `SIG_ERR` 。  
  
 根據預設， `signal` 以終止碼 3 結束呼叫程式，不論 `sig` 的值為何。  
  
> [!NOTE]
>  `SIGINT` 不支援任何 Win32 應用程式。  當發生 CTRL\+C 中斷時， Win32 作業系統產生一個特別為處理該中斷的新執行緒。  這可能會導致單執行緒程式\(如 UNIX 中的一個\)變成多執行緒，進而造成無法預期的行為。  
  
 `func` 參數是您寫入的訊號處理常式的位置，或是同樣定義於 SIGNAL.H 的預定義常數 `SIG_DFL` 或 `SIG_IGN` 的位置。  如果 `func` 是一個函式，它會被設置為給定訊號的訊號處理常式。  訊號處理常式的函式原型須要一個形式引數，是為 `int` 型別的 `sig` 。  作業系統在中斷發生時透過 `sig` 提供實際引數。引數是產生中斷的訊號。  如此您可以使用六個表示常值 \(如前表所列\) 於您的訊號處理常式，來決定發生哪一種中斷並採取適當的動作。  例如，您可以呼叫 `signal` 兩次來對兩個不同訊號指定相同的處理常式，並在處理常式裡利用 `sig` 參數來判斷收到的訊號以採取不同的動作。  
  
 如果您要測試浮點數例外狀況 \(`SIGFPE`\) ， `func` 指向一個接受以 `FPE_xxx` 的形式定義於 FLOAT.H 的數個表示常值之一做為為選擇性的第二參數的函式。  當發生 `SIGFPE` 訊號的時後，您可以檢查第二參數的值來得知浮點數例外狀況的種類並採取適當動作。  此參數以及其可能值是 Microsoft 的擴充。  
  
 對於浮點數例外狀況， `func` 的值在收到訊號時不會被重設。  若要從浮點數例外狀況中回復，請使用 try\/except 子句包覆於浮點數運算。  也可以透過與 [longjmp](../../c-runtime-library/reference/longjmp.md) 一起使用 [setjmp](../../c-runtime-library/reference/setjmp.md) 來回復。  在這兩個情況下，呼叫處理程序在保持浮點狀態未定義之下繼續執行。  
  
 如果訊號處理常式結束回傳，呼叫處理程序立刻繼續從收到中斷訊號的地方繼續執行。  不論在何種訊號類別或運算模式下均是如此。  
  
 在指定的函式開始執行前， `func` 的值會被設置為 `SIG_DFL` 。  下一個中斷訊號的處理方式會如 `SIG_DFL` 中所述，除非 `signal` 的干擾呼叫另行指定。  您可以使用這個功能在呼叫的函式中重設信號。  
  
 由於訊號處理常式通常被非同步的呼叫，您的訊號處理常式可能在執行階段未完成或在未知的狀態下得到控制權。  下列清單總結關於您的訊號處理常式裡可以使用的函式之限制。  
  
-   請勿發行低階或 STDIO.H I\/O 常式 \(例如， `printf` 或 `fread`\)。  
  
-   請勿呼叫堆積常式或使用任何會使用堆積常式的常式 \(例如， `malloc`、 `_strdup`或 `_putenv`\)。  如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
-   請勿使用任何會引起系統呼叫的函式 \(例如， `_getcwd` 或 `time`\)。  
  
-   請勿使用 `longjmp` ，除非中斷是由浮點數例外狀況所導致的 \(也就是`sig` `SIGFPE 為` \) 。  在此情況下，請先呼叫 `_fpreset` 以重新初始化浮點封包。  
  
-   請不要使用任何重疊的常式。  
  
 應用程式必定是因為包含了浮點運算的程式碼，才會困於函式所用的 `SIGFPE` 例外狀況中。  如果您的程式碼沒有浮點數運算程式碼，並需要執行階段程式庫的訊號處理代碼，請直接宣告一個 volatile double 並初始化為零：  
  
```  
volatile double d = 0.0f;   
```  
  
 `SIGILL` 和 `SIGTERM` 信號不會在 Windows 系統中產生。  它們是為了 ANSI 相容性而被包含。  因此，您可以使用 `signal`來設定這些信號的訊號處理常式，您也可以呼叫 [raise](../../c-runtime-library/reference/raise.md)來明確產生這些信號。  
  
 在呼叫 `_exec`函式 或 `_spawn` 函式時所建立的衍生處理程序中將不會保留訊號設定。  在新處理程序中訊號設定會重設為預設值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`signal`|\<signal.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 下列範例顯示如何使用 `signal` 加入一些自訂行為至 `SIGABRT` 信號。  如需abort 行為的詳細資訊，請參閱 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md) 。  
  
```cpp  
// crt_signal.c  
// compile with: /EHsc /W4  
// Use signal to attach a signal handler to the abort routine  
#include <stdlib.h>  
#include <signal.h>  
#include <tchar.h>  
  
void SignalHandler(int signal)  
{  
    if (signal == SIGABRT) {  
        // abort signal handler code  
    } else {  
        // ...  
    }  
}  
  
int main()  
{  
    typedef void (*SignalHandlerPointer)(int);  
  
    SignalHandlerPointer previousHandler;  
    previousHandler = signal(SIGABRT, SignalHandler);  
  
    abort();  
}  
  
```  
  
  **This application has requested the Runtime to terminate it in an unusual way.**  
**Please contact the application's support team for more information.**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_fpreset](../../c-runtime-library/reference/fpreset.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)