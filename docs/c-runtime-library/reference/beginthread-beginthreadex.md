---
title: _beginthread、_beginthreadex | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _beginthread
- _beginthreadex
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
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d56bcc5ec779b077305d9d80e4a4e6b5e511df5e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704655"
---
# <a name="beginthread-beginthreadex"></a>_beginthread、_beginthreadex

建立執行緒。

## <a name="syntax"></a>語法

```cpp
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

### <a name="parameters"></a>參數

*start_address*<br/>
開始執行新執行緒之常式的起始位址。 如 **_beginthread**，呼叫慣例是[__cdecl](../../cpp/cdecl.md) （若為機器碼） 或[__clrcall](../../cpp/clrcall.md) （適用於 managed 程式碼）; 對於 **_beginthreadex**，它可能是[__stdcall](../../cpp/stdcall.md) （若為機器碼） 或[__clrcall](../../cpp/clrcall.md) （適用於 managed 程式碼）。

*stack_size*<br/>
新執行緒堆疊大小或 0。

*引數清單*<br/>
要傳遞給新執行緒的引數清單或**NULL**。

*安全性*<br/>
[SECURITY ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果*安全性*是**NULL**，無法繼承控制代碼。 必須是**NULL** Windows 95 應用程式。

*initflag*<br/>
控制新執行緒之初始狀態的旗標。 設定*initflag*為 0 即可立即執行、 或**CREATE_SUSPENDED**建立執行緒處於暫停狀態; 使用[ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx)執行執行緒。 設定*initflag*至**STACK_SIZE_PARAM_IS_A_RESERVATION**旗標以使用*stack_size*初始保留大小，以位元組為單位的堆疊; 如果這個旗標是未指定，因此， *stack_size*指定基本配置大小。

*thrdaddr*<br/>
指向接收執行緒識別項的 32 位元變數。 如果是**NULL**，不會使用它。

## <a name="return-value"></a>傳回值

所有這些函式如果成功，傳回的控制代碼，新建立的執行緒，不過，如果新建立的執行緒太快結束， **_beginthread**可能不會傳回有效的控制代碼。 (請參閱＜備註＞一節中的討論)。發生錯誤時， **_beginthread**傳回-1l; 此時和**errno**設**EAGAIN**有太多執行緒時，為**EINVAL**如果引數無效或堆疊大小不正確，或**EACCES**是否有資源不足 （例如記憶體）。 發生錯誤時， **_beginthreadex**傳回 0，和**errno**和 **_doserrno**設定。

如果*start_address*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回-1。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需有關**uintptr_t**，請參閱[標準類型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>備註

**_Beginthread**函式會建立執行緒開始執行常式的*start_address*。 在常式*start_address*必須使用 **__cdecl** （若為機器碼） 或 **__clrcall** （適用於 managed 程式碼） 呼叫慣例，而且應該有傳回值。 執行緒從該常式返回時，就會自動終止。 如需執行緒的詳細資訊，請參閱[舊版程式碼的多執行緒支援 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**類似 Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) API 詳細甚於 **_beginthread**沒有。 **_beginthreadex**不同於 **_beginthread**如下：

- **_beginthreadex**有三個額外的參數： *initflag*，*安全性*，和**threadaddr**。 新執行緒可以建立在暫停狀態，以指定的安全性，並且可以使用來存取*thrdaddr*，執行緒識別項。

- 在常式*start_address*傳遞至 **_beginthreadex**必須使用 **__stdcall** （若為機器碼） 或 **__clrcall** （適用於managed 程式碼) 呼叫慣例，而且必須傳回執行緒結束代碼。

- **_beginthreadex**失敗，而非-1l; 此時會傳回 0。

- 建立使用的執行緒， **_beginthreadex**終止呼叫[_endthreadex](endthread-endthreadex.md)。

**_Beginthreadex**函式給予您更充分掌控執行緒建立比如何 **_beginthread**沒有。 **_Endthreadex**函式也是更有彈性。 例如，與 **_beginthreadex**，您可以使用安全性資訊、 設定執行緒初始狀態的 （執行或暫停），並取得新建立執行緒的執行緒識別項。 您也可以使用所傳回的執行緒控制代碼 **_beginthreadex**同步處理的 Api，您無法使用執行 **_beginthread**。

若要使用更安全 **_beginthreadex**比 **_beginthread**。 如果由所產生的執行緒 **_beginthread**快結束，傳回的呼叫端的控制代碼 **_beginthread**可能會無效，或指向其他執行緒。 不過，所傳回的控制代碼 **_beginthreadex**關閉的呼叫端所 **_beginthreadex**，因此它一定會有效的控制代碼，如果 **_beginthreadex**未傳回錯誤。

您可以呼叫[_endthread](endthread-endthreadex.md)或 **_endthreadex**明確來終止執行緒; 然而， **_endthread**或 **_endthreadex**稱為自動當執行緒從傳回做為參數傳遞的常式。 終止執行緒呼叫 **_endthread**或 **_endthreadex**有助於確保正確復原配置給執行緒的資源。

**_endthread**會自動關閉執行緒控制代碼，而 **_endthreadex**則否。 因此，當您使用 **_beginthread**和 **_endthread**，請勿明確地關閉執行緒控制代碼藉由呼叫 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx)應用程式開發介面。 這個行為與 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) 應用程式開發介面不同。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 **ExitThread** API 讓您不會阻止執行階段系統回收配置的資源。 **_endthread**和 **_endthreadex**回收配置的執行緒資源，然後呼叫**ExitThread**。

作業系統會處理堆疊的配置時任一 **_beginthread**或 **_beginthreadex**呼叫; 您不必將執行緒堆疊的位址傳遞給其中一個函數。 此外， *stack_size*引數可以是的 0，在其中此時作業系統會使用相同的值會指定堆疊主執行緒。

*引數清單*是要傳遞給新建立執行緒的參數。 這通常是資料項目的位址，例如字元字串。 *引數清單*可以**NULL**如果不需要但是 **_beginthread**和 **_beginthreadex**必須指定要傳遞給新執行緒的某些值。 如果有任何執行緒呼叫，則會結束所有的執行緒[中止](abort.md)，**結束**， **_exit**，或**ExitProcess**。

初始化新執行緒的地區設定使用的處理序專屬全域目前地區設定資訊。 每個執行緒的地區設定是否已啟用呼叫[_configthreadlocale](configthreadlocale.md) （以全域方式或新執行緒的僅限），執行緒可以變更其地區設定獨立來自其他執行緒呼叫**setlocale**或 **_wsetlocale**。 不需要設定每個執行緒的地區設定旗標的執行緒可能會影響所有其他的執行緒，也不需要在個別執行緒地區設定旗標設定，以及所有新建立執行緒的地區設定資訊。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如 **/clr**程式碼中， **_beginthread**和 **_beginthreadex**各有兩個多載。 其中一個接受原生呼叫慣例函式指標，和另一個採用 **__clrcall**函式指標。 第一個多載版本不是應用程式定義域安全的，而且永遠不會是。 如果您要撰寫 **/clr**程式碼，您必須確定新的執行緒會進入正確的應用程式網域，才能存取 managed 資源。 例如，您可以使用 [call_in_appdomain 函式](../../dotnet/call-in-appdomain-function.md)來達成這個目的。 第二個多載是應用程式定義域安全;新建立的執行緒最後一定會在呼叫端的應用程式定義域中 **_beginthread**或 **_beginthreadex**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

若要使用 **_beginthread**或 **_beginthreadex**，應用程式必須連結其中一個多執行緒 C 執行階段程式庫。

## <a name="example"></a>範例

下列範例會使用 **_beginthread**和 **_endthread**。

```C
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

## <a name="example"></a>範例

下列程式碼範例會示範如何使用所傳回的執行緒控制代碼 **_beginthreadex**在同步處理應用程式開發介面[WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx)。 主執行緒會等待第二個執行緒終止後，再繼續執行。 當第二個執行緒呼叫 **_endthreadex**，它使其執行緒物件移至已收到信號的狀態。 這樣可讓主執行緒繼續執行。 無法完成與 **_beginthread**和 **_endthread**，因為 **_endthread**呼叫**CloseHandle**，即已遭終結執行緒它可以設定為收到信號狀態之前的物件。

```cpp
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
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>另請參閱

- [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)
- [_endthread、_endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit、_Exit、_exit](exit-exit-exit.md)
- [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)
