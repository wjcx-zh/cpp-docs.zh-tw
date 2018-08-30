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
ms.openlocfilehash: e4bdae31c3a2f84dd959baf49fae7e43a6cc9eb0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206393"
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
開始執行新執行緒之常式的起始位址。 針對 **_beginthread**，呼叫慣例是[__cdecl](../../cpp/cdecl.md) （適用於原生程式碼） 或[__clrcall](../../cpp/clrcall.md) （適用於 managed 程式碼）; 如 **_beginthreadex**，它可能是[__stdcall](../../cpp/stdcall.md) （適用於原生程式碼） 或[__clrcall](../../cpp/clrcall.md) （適用於 managed 程式碼）。

*stack_size*<br/>
新執行緒堆疊大小或 0。

*arglist*<br/>
引數清單傳遞至新的執行緒，或是**NULL**。

*安全性*<br/>
[SECURITY ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果*安全性*是**NULL**，無法繼承控制代碼。 必須是**NULL** Windows 95 應用程式。

*initflag*<br/>
控制新執行緒之初始狀態的旗標。 設定*initflag*為 0，以立即執行，或是**CREATE_SUSPENDED**若要建立的執行緒處於暫停狀態; 使用[ResumeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-resumethread)執行執行緒。 設定*initflag*要**STACK_SIZE_PARAM_IS_A_RESERVATION**若要使用的旗標*stack_size*初始保留大小，以位元組為單位的堆疊，這個旗標是否未指定， *stack_size*指定基本配置大小。

*thrdaddr*<br/>
指向接收執行緒識別項的 32 位元變數。 如果它是**NULL**，不會使用它。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式都會將控制代碼傳回新建立的執行緒;不過，如果新建立的執行緒太快，結束 **_beginthread**可能不會傳回有效的控制代碼。 (請參閱＜備註＞一節中的討論)。發生錯誤時， **_beginthread**會傳回-1l 並**errno**設定為**EAGAIN**有太多的執行緒則為**EINVAL**如果引數無效或堆疊大小不正確，或**EACCES**如果有資源不足 （例如記憶體）。 發生錯誤時， **_beginthreadex**會傳回 0，並**errno**並 **_doserrno**設定。

如果*start_address*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**要**EINVAL**並傳回-1。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需詳細資訊**uintptr_t**，請參閱[標準類型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>備註

**_Beginthread**函式會建立開始執行常式的執行緒*start_address*。 在常式*start_address*必須使用 **__cdecl** （適用於原生程式碼） 或 **__clrcall** （適用於 managed 程式碼） 呼叫慣例，而且應該沒有傳回值。 執行緒從該常式返回時，就會自動終止。 如需執行緒的詳細資訊，請參閱[舊版程式碼的多執行緒支援 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**類似於 Win32 [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)介面，更甚於 **_beginthread**沒有。 **_beginthreadex**有別 **_beginthread**如下：

- **_beginthreadex**有三個額外的參數： *initflag*，*安全性*，和**threadaddr**。 新執行緒可以建立在暫停狀態，使用指定的安全性，並且可以使用來存取*thrdaddr*，執行緒識別項。

- 在常式*start_address*傳遞至 **_beginthreadex**必須使用 **__stdcall** （適用於原生程式碼） 或 **__clrcall** （適用於managed 程式碼) 呼叫慣例，而且必須傳回執行緒結束代碼。

- **_beginthreadex**上失敗，而非-1l 會傳回 0。

- 建立使用的執行緒 **_beginthreadex**終止呼叫[_endthreadex](endthread-endthreadex.md)。

**_Beginthreadex**函式可讓您更充分掌控如何比建立執行緒 **_beginthread**沒有。 **_Endthreadex**函式也會更有彈性。 例如，使用 **_beginthreadex**，您可以使用安全性資訊、 設定初始狀態的執行緒 （執行或暫停），並取得新建立的執行緒的執行緒識別碼。 您也可以使用所傳回的執行緒控制代碼 **_beginthreadex**同步處理 Api，您無法透過執行 **_beginthread**。

若要使用更安全 **_beginthreadex**比 **_beginthread**。 如果由所產生的執行緒 **_beginthread**結束，傳回給呼叫端的控制代碼 **_beginthread**可能無效，或指向另一個執行緒。 不過，所傳回的控制代碼 **_beginthreadex**的呼叫端必須關閉 **_beginthreadex**，因此一定會是有效的控制代碼，如果 **_beginthreadex**未傳回錯誤。

您可以呼叫[_endthread](endthread-endthreadex.md)或 **_endthreadex**明確地終止執行緒; 不過， **_endthread**或是 **_endthreadex**稱為自動當執行緒從傳回做為參數傳遞的常式。 結束藉由呼叫執行緒 **_endthread**或是 **_endthreadex**有助於確保正確復原配置給執行緒的資源。

**_endthread**會自動關閉執行緒控制代碼，而 **_endthreadex**則否。 因此，當您使用 **_beginthread**並 **_endthread**，不要明確地關閉執行緒控制代碼藉由呼叫 Win32 [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API。 這個行為與 Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面不同。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 **ExitThread** API，讓您不會阻止執行階段系統回收配置的資源。 **_endthread**並 **_endthreadex**回收配置的執行緒資源，然後呼叫**ExitThread**。

作業系統會處理堆疊的配置時任一 **_beginthread**或 **_beginthreadex**呼叫; 您不必將執行緒堆疊的位址傳遞給其中一個函式。 颾魤 ㄛ *stack_size*引數可以是的 0，在其中此時作業系統會使用相同的值為指定的堆疊主執行緒。

*arglist*為參數傳遞給新建立的執行緒。 這通常是資料項目的位址，例如字元字串。 *arglist*可以是**NULL**如果不需要但 **_beginthread**並 **_beginthreadex**必須指定要傳遞給新的執行緒的某些值。 如果有任何執行緒呼叫，則會結束所有的執行緒[中止](abort.md)，**結束**， **_exit**，或**ExitProcess**。

初始化新的執行緒的地區設定使用同處理序全域目前地區設定資訊。 每個執行緒的地區設定是否已啟用的呼叫所[_configthreadlocale](configthreadlocale.md) （以全域方式或針對新執行緒僅限），執行緒可以變更其地區設定獨立來自其他執行緒呼叫**setlocale**或 **_wsetlocale**。 不需要設定個別執行緒地區設定旗標的執行緒可能會影響所有其他執行緒也不需要在個別執行緒地區設定旗標設定，以及所有新建立的執行緒地區設定資訊。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

針對 **/clr**程式碼 **_beginthread**並 **_beginthreadex**各有兩個多載。 另一個則採用原生呼叫慣例函式指標，另一個採用 **__clrcall**函式指標。 第一個多載版本不是應用程式定義域安全的，而且永遠不會是。 如果您正在撰寫 **/clr**程式碼，您必須確定新的執行緒進入正確的應用程式網域，才能存取 managed 資源。 例如，您可以使用 [call_in_appdomain 函式](../../dotnet/call-in-appdomain-function.md)來達成這個目的。 第二個多載是應用程式網域的安全，新建立的執行緒最後一定會在呼叫端的應用程式定義域 **_beginthread**或是 **_beginthreadex**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

若要使用 **_beginthread**或是 **_beginthreadex**，應用程式必須連結其中一個多執行緒 C 執行階段程式庫。

## <a name="example"></a>範例

下列範例會使用 **_beginthread**並 **_endthread**。

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

// Bounce - Thread to create and control a colored letter that moves
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

下列程式碼範例會示範如何使用所傳回的執行緒控制代碼 **_beginthreadex**同步處理 API [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)。 主執行緒會等待第二個執行緒終止後，再繼續執行。 當第二個執行緒呼叫 **_endthreadex**，它會導致其執行緒物件移至收到信號的狀態。 這樣可讓主執行緒繼續執行。 這無法透過 **_beginthread**並 **_endthread**，因為 **_endthread**呼叫**CloseHandle**，即已遭終結執行緒設定為信號狀態之前的物件。

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
- [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
