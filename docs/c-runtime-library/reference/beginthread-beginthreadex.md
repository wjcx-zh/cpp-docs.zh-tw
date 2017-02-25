---
title: "_beginthread、_beginthreadex | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_beginthread"
  - "_beginthreadex"
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
  - "beginthread"
  - "_beginthread"
  - "beginthreadex"
  - "_beginthreadex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_beginthread 函式"
  - "執行緒 [c + +]，建立執行緒"
  - "beginthreadex 函式"
  - "_beginthreadex 函式"
  - "beginthread 函式"
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
caps.latest.revision: 36
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 36
---
# _beginthread、_beginthreadex
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立執行緒。  
  
## 語法  
  
```  
uintptr_t _beginthread( // NATIVE CODE  
   void( __cdecl *start_address )( void * ),  
   unsigned stack_size,  
   void *arglist   
);  
uintptr_t _beginthread( // MANAGED CODE  
   void( __clrcall *start_address )( void * ),  
   unsigned stack_size,  
   void *arglist   
);  
uintptr_t _beginthreadex( // NATIVE CODE  
   void *security,  
   unsigned stack_size,  
   unsigned ( __stdcall *start_address )( void * ),  
   void *arglist,  
   unsigned initflag,  
   unsigned *thrdaddr   
);  
uintptr_t _beginthreadex( // MANAGED CODE  
   void *security,  
   unsigned stack_size,  
   unsigned ( __clrcall *start_address )( void * ),  
   void *arglist,  
   unsigned initflag,  
   unsigned *thrdaddr   
);  
```  
  
#### 參數  
 `start_address`  
 開始執行新執行緒之常式的起始位址。 對於 `_beginthread`，呼叫慣例是 [\_\_cdecl](../../cpp/cdecl.md) \(若為機器碼\) 或 [\_\_clrcall](../../cpp/clrcall.md) \(若為 Managed 程式碼\)；對於 `_beginthreadex`，則是 [\_\_stdcall](../../cpp/stdcall.md) \(若為機器碼\) 或 [\_\_clrcall](../../cpp/clrcall.md) \(若為 Managed 程式碼\)。  
  
 `stack_size`  
 新執行緒堆疊大小或 0。  
  
 `arglist`  
 要傳遞給新執行緒的引數清單或 NULL。  
  
 `Security`  
 [SECURITY ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果 `Security` 為 NULL，則無法繼承控制代碼。 對於 Windows 95 應用程式必須是 NULL。  
  
 `initflag`  
 控制新執行緒之初始狀態的旗標。 將 `initflag` 設定為 `0` 以立即執行，或是設定為 `CREATE_SUSPENDED` 以建立暫停狀態的執行緒；請使用 [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) 執行執行緒。 將 `initflag` 設定為 `STACK_SIZE_PARAM_IS_A_RESERVATION` 旗標以使用 `stack_size` 做為堆疊的初始預留大小 \(以位元組為單位\)；如果未指定這個旗標，`stack_size` 會指定基本配置大小。  
  
 `thrdaddr`  
 指向接收執行緒識別項的 32 位元變數。 如果為 NULL，則不使用它。  
  
## 傳回值  
 如果成功，則上述每個函式都會將控制代碼傳回至新建立的執行緒；然而，如果新建立的執行緒太快結束，`_beginthread` 可能無法傳回有效的控制代碼 \(請參閱＜備註＞一節中的討論\)。 發生錯誤時，`_beginthread` 會傳回 \-1L；此時 `errno` 會在有太多執行緒時設定為 `EAGAIN`、在引數無效或堆疊大小不正確時設定為 `EINVAL`，或在資源 \(例如記憶體\) 不足時設定為 `EACCES`。 發生錯誤時，`_beginthreadex` 會傳回 0，並設定 `errno` 和 `_doserrno`。  
  
 如果 `startaddress` 為 NULL，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL`，並傳回 \-1。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需 `uintptr_t` 的詳細資訊，請參閱[標準類型](../../c-runtime-library/standard-types.md)。  
  
## 備註  
 `_beginthread` 函式會建立一個從 `start_address` 開始執行常式的執行緒。 在 `start_address` 的常式必須使用 `__cdecl` \(若為機器碼\) 或 `__clrcall` \(若為 Managed 程式碼\) 呼叫慣例，而且不應該有傳回值。 執行緒從該常式返回時，就會自動終止。 如需執行緒的詳細資訊，請參閱[舊版程式碼的多執行緒支援 \(Visual C\+\+\)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 `_beginthreadex` 很像 Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) 應用程式開發介面，更甚於 `_beginthread` 與之相似的程度。`_beginthreadex` 與 `_beginthread` 在下列各方面不同：  
  
-   `_beginthreadex` 有三個額外的參數：`initflag`、`security` 和 `threadaddr`。 新執行緒可以在指定安全性的暫停狀態下建立，並且可以使用執行緒識別項 `thrdaddr` 來加以存取。  
  
-   位於傳遞至 `_beginthreadex` 之 `start_address` 的常式必須使用 `__stdcall` \(若為機器碼\) 或 `__clrcall` \(若為 Managed 程式碼\) 呼叫慣例，而且必須傳回執行緒結束代碼。  
  
-   `_beginthreadex` 會在失敗時回傳 0，而非 \-1L。  
  
-   使用 `_beginthreadex` 建立的執行緒，是藉由對 [\_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md) 的呼叫來結束。  
  
 比起 `_beginthreadex`，`_beginthread` 函式給予您更多掌控執行緒建立方式的能力。`_endthreadex` 函式也更有彈性。 例如，您可以透過 `_beginthreadex`，使用安全性資訊、設定執行緒初始狀態 \(執行或暫停\)，以及取得新建立執行緒的執行緒識別項。 您也可以搭配同步處理應用程式開發介面來使用 `_beginthreadex` 傳回的執行緒控制代碼，這在 `_beginthread` 中是辦不到的。  
  
 使用 `_beginthreadex` 會比使用 `_beginthread` 來得安全。 如果 `_beginthread` 產生的執行緒結束得過快，傳回給 `_beginthread` 呼叫端的控制代碼可能會無效，或指向其他執行緒。 然而，`_beginthreadex` 傳回的控制代碼必須由 `_beginthreadex` 的呼叫端關閉，這樣才能保證只要 `_beginthreadex` 沒有傳回錯誤，控制代碼就是有效的。  
  
 您可以明確地呼叫 [\_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) 或 `_endthreadex` 來終止執行緒。不過，當執行緒從做為參數傳遞的常式返回時，也會自動呼叫 `_endthread` 或 `_endthreadex`。 透過呼叫 `_endthread` 或 `_endthreadex` 終止執行緒有助於確保正確復原配置給執行緒的資源。  
  
 `_endthread` 會自動關閉執行緒控制代碼，而 `_endthreadex` 則不會。 因此，當您使用 `_beginthread` 和 `_endthread` 時，不要藉由呼叫 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) 應用程式開發介面，明確地關閉執行緒控制代碼。 這個行為與 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) 應用程式開發介面不同。  
  
> [!NOTE]
>  對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 `ExitThread` 應用程式開發介面，這樣才不會阻止執行階段系統回收配置的資源。`_endthread` 和 `_endthreadex` 會回收配置的執行緒資源，然後呼叫 `ExitThread`。  
  
 呼叫 `_beginthread` 或 `_beginthreadex` 時，作業系統會處理堆疊的配置，您不必將執行緒堆疊的位址傳遞給這兩個函式。 此外，`stack_size` 引數也可以是 0，此時作業系統會使用與指定給主執行緒的堆疊相同的值。  
  
 `arglist` 是要傳遞給新建立執行緒的參數。 這通常是資料項目的位址，例如字元字串。`arglist` 在不需要時可以為 NULL，但是 `_beginthread` 和 `_beginthreadex` 必須有某個指定的值，才能傳遞給新的執行緒。 如果有任何執行緒呼叫 `abort`、`exit`、`_exit` 或 `ExitProcess`，就會結束所有的執行緒。  
  
 新執行緒的地區設定是從父執行緒繼承而來。 如果透過呼叫 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) \(以全域方式或只針對新執行緒\) 啟用個別執行緒地區設定，則執行緒可以呼叫 `setlocale` 或 `_wsetlocale`，在父執行緒之外獨立變更其地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 對於混合程式碼或純程式碼，`_beginthread` 和 `_beginthreadex` 各有兩種多載版本，一個接受原生呼叫慣例函式指標，另一個接受 `__clrcall` 函式指標。 第一個多載版本不是應用程式定義域安全的，而且永遠不會是。 如果您要撰寫混合程式碼或純程式碼，就必須確保新的執行緒會在存取 Managed 資源前進入正確的應用程式定義域。 例如，您可以使用 [call\_in\_appdomain 函式](../../dotnet/call-in-appdomain-function.md) 來達成這個目的。 第二個多載版本是應用程式定義域安全的；新建立的執行緒永遠都會在 `_beginthread` 或 `_beginthreadex` 呼叫端的應用程式定義域中結束。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_beginthread`|\<process.h\>|  
|`_beginthreadex`|\<process.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的多執行緒版本。  
  
 若要使用 `_beginthread` 或 `_beginthreadex`，應用程式必須連結其中一個多執行緒 C 執行階段程式庫。  
  
## 範例  
 下列範例會使用 `_beginthread` 和 `_endthread`。  
  
```  
// crt_BEGTHRD.C  
// compile with: /MT /D "_X86_" /c  
// processor: x86  
#include <windows.h>  
#include <process.h>    /* _beginthread, _endthread */  
#include <stddef.h>  
#include <stdlib.h>  
#include <conio.h>  
  
void Bounce( void * );  
void CheckKey( void * );  
  
// GetRandom returns a random integer between min and max.  
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))  
// GetGlyph returns a printable ASCII character value  
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))  
  
BOOL repeat = TRUE;                 // Global repeat flag   
HANDLE hStdOut;                     // Handle for console window  
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure  
  
int main()  
{  
    int param = 0;  
    int * pparam = &param;  
  
    // Get display screen's text row and column information.  
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );  
    GetConsoleScreenBufferInfo( hStdOut, &csbi );  
  
    // Launch CheckKey thread to check for terminating keystroke.  
    _beginthread( CheckKey, 0, NULL );  
  
    // Loop until CheckKey terminates program or 1000 threads created.   
    while( repeat && param < 1000 )  
    {  
        // launch another character thread.  
        _beginthread( Bounce, 0, (void *) pparam );  
  
        // increment the thread parameter  
        param++;  
  
        // Wait one second between loops.  
        Sleep( 1000L );  
    }  
}  
  
// CheckKey - Thread to wait for a keystroke, then clear repeat flag.  
void CheckKey( void * ignored )  
{  
    _getch();  
    repeat = 0;    // _endthread implied  
}  
  
// Bounce - Thread to create and and control a colored letter that moves  
// around on the screen.  
//  
// Params: parg - the value to create the character from  
void Bounce( void * parg )  
{  
    char       blankcell = 0x20;  
    CHAR_INFO  ci;  
    COORD      oldcoord, cellsize, origin;  
    DWORD      result;  
    SMALL_RECT region;  
  
    cellsize.X = cellsize.Y = 1;  
    origin.X = origin.Y = 0;  
  
    // Generate location, letter and color attribute from thread argument.  
    srand( _threadid );  
    oldcoord.X = region.Left = region.Right =   
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);  
    oldcoord.Y = region.Top = region.Bottom =   
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);  
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));  
    ci.Attributes = GetRandom(1, 15);  
  
    while (repeat)  
    {  
        // Pause between loops.  
        Sleep( 100L );  
  
        // Blank out our old position on the screen, and draw new letter.  
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);  
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);  
  
        // Increment the coordinate for next placement of the block.  
        oldcoord.X = region.Left;  
        oldcoord.Y = region.Top;  
        region.Left = region.Right += GetRandom(-1, 1);  
        region.Top = region.Bottom += GetRandom(-1, 1);  
  
        // Correct placement (and beep) if about to go off the screen.  
        if (region.Left < csbi.srWindow.Left)  
            region.Left = region.Right = csbi.srWindow.Left + 1;  
        else if (region.Right >= csbi.srWindow.Right)  
            region.Left = region.Right = csbi.srWindow.Right - 2;  
        else if (region.Top < csbi.srWindow.Top)  
            region.Top = region.Bottom = csbi.srWindow.Top + 1;  
        else if (region.Bottom >= csbi.srWindow.Bottom)  
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;  
  
        // If not at a screen border, continue, otherwise beep.  
        else  
            continue;  
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);  
    }  
    // _endthread given to terminate  
    _endthread();  
}  
```  
  
 按下任意鍵結束範例應用程式。  
  
## 範例  
 下列範例程式碼示範如何搭配同步處理應用程式開發介面 [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) 來使用 `_beginthreadex` 傳回的執行緒控制代碼。 主執行緒會等待第二個執行緒終止後，再繼續執行。 第二個執行緒呼叫 `_endthreadex` 時，會使其執行緒物件移至已收到信號的狀態。 這樣可讓主執行緒繼續執行。 但要是使用 `_beginthread` 和 `_endthread`，就辦不到了。因為 `_endthread` 會呼叫 `CloseHandle`，執行緒物件在設為收到信號狀態之前即已遭終結。  
  
```  
// crt_begthrdex.cpp  
// compile with: /MT  
#include <windows.h>  
#include <stdio.h>  
#include <process.h>  
  
unsigned Counter;   
unsigned __stdcall SecondThreadFunc( void* pArguments )  
{  
    printf( "In second thread...\n" );  
  
    while ( Counter < 1000000 )  
        Counter++;  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
int main()  
{   
    HANDLE hThread;  
    unsigned threadID;  
  
    printf( "Creating second thread...\n" );  
  
    // Create the second thread.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );  
  
    // Wait until second thread terminates. If you comment out the line  
    // below, Counter will not be correct because the thread has not  
    // terminated, and Counter most likely has not been incremented to  
    // 1000000 yet.  
    WaitForSingleObject( hThread, INFINITE );  
    printf( "Counter should be 1000000; it is-> %d\n", Counter );  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
```Output  
正在建立第二個執行緒...在第二個執行緒中...Counter should be 1000000; it is-> 1000000  
```  
  
## .NET Framework 對等用法  
 [System::Threading::Thread::Start](https://msdn.microsoft.com/en-us/library/system.threading.thread.start.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_endthread、\_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)