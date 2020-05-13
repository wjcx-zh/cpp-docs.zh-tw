---
title: _beginthread、_beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: acf885c923db3fdf91119b29a78d64824384166b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913499"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread、_beginthreadex

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
開始執行新執行緒之常式的起始位址。 針對 **_beginthread**，呼叫慣例可能是[__cdecl](../../cpp/cdecl.md) （適用于機器碼）或[__clrcall](../../cpp/clrcall.md) （適用于 managed 程式碼）;針對 **_beginthreadex**，它可能是[__stdcall](../../cpp/stdcall.md) （適用于機器碼）或[__clrcall](../../cpp/clrcall.md) （適用于 managed 程式碼）。

*stack_size*<br/>
新執行緒堆疊大小或 0。

*arglist*<br/>
要傳遞至新執行緒的引數清單，或為**Null**。

*安全性*<br/>
[SECURITY ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果*Security*為**Null**，則無法繼承控制碼。 Windows 95 應用程式的必須是**Null** 。

*initflag*<br/>
控制新執行緒之初始狀態的旗標。 將*initflag*設定為0以立即執行，或**CREATE_SUSPENDED**以建立暫停狀態的執行緒;使用[ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread)來執行執行緒。 將*initflag*設定為**STACK_SIZE_PARAM_IS_A_RESER加值稅ION**旗標，以使用*stack_size*做為堆疊的初始保留大小（以位元組為單位）;如果未指定此旗標， *stack_size*會指定認可大小。

*thrdaddr*<br/>
指向接收執行緒識別項的 32 位元變數。 如果是**Null**，則不會使用它。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式都會將控制碼傳回至新建立的執行緒;不過，如果新建立的執行緒太快結束， **_beginthread**可能不會傳回有效的控制碼。 （請參閱「備註」一節中的討論）。發生錯誤時， **_Beginthread** 1L，而且如果有太多執行緒， **errno**會設定為**EAGAIN** ; 如果引數無效或堆疊大小不正確，則為**EINVAL** ，或如果資源不足（例如記憶體），則為**EACCES** 。 發生錯誤時， **_beginthreadex**會傳回0，並設定**errno**和 **_doserrno** 。

如果*start_address*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回-1。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需**uintptr_t**的詳細資訊，請參閱[標準類型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>備註

**_Beginthread**函式會建立一個在*start_address*開始執行常式的執行緒。 *Start_address*的常式必須使用 **__cdecl** （適用于機器碼）或 **__clrcall** （適用于 managed 程式碼）呼叫慣例，而且不應該有傳回值。 執行緒從該常式返回時，就會自動終止。 如需執行緒的詳細資訊，請參閱[舊版程式碼的多執行緒支援 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**類似于 Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API，比 **_beginthread**更緊密。 **_beginthreadex**不同于 **_beginthread**的方式如下：

- **_beginthreadex**有三個額外的參數： *initflag*、 *Security*和**threadaddr**。 新執行緒可以使用指定的安全性在暫停狀態下建立，而且可以透過*thrdaddr*（也就是執行緒識別碼）來存取。

- 傳遞至 **_beginthreadex**之*start_address*的常式必須使用 **__stdcall** （適用于機器碼）或 **__clrcall** （適用于 managed 程式碼）呼叫慣例，而且必須傳回執行緒結束代碼。

- **_beginthreadex**會在失敗時傳回0，而不是-1L。

- 使用 **_beginthreadex**建立的執行緒會藉由呼叫[_endthreadex](endthread-endthreadex.md)來終止。

**_Beginthreadex**函式可讓您更充分掌控執行緒的建立方式，而不是 **_beginthread**執行的工作。 **_Endthreadex**函數也更有彈性。 例如，使用 **_beginthreadex**，您可以使用安全性資訊、設定執行緒的初始狀態（執行中或已暫停），以及取得新建立執行緒的執行緒識別碼。 您也可以使用 **_beginthreadex**所傳回的執行緒控制碼搭配同步處理 api，而不能使用 **_beginthread**執行此動作。

使用 **_beginthreadex**比 **_beginthread**更安全。 如果 **_beginthread**產生的執行緒很快結束，傳回 **_beginthread**呼叫端的控制碼可能會無效，或指向另一個執行緒。 不過， **_beginthreadex**所傳回的控制碼必須由 **_beginthreadex**的呼叫端關閉，因此，如果 **_beginthreadex**未傳回錯誤，則保證會是有效的控制碼。

您可以呼叫[_endthread](endthread-endthreadex.md)或明確地 **_endthreadex**以終止執行緒;不過，當執行緒從做為參數傳遞的常式返回時，會自動呼叫 **_endthread**或 **_endthreadex** 。 使用 **_endthread**或 **_endthreadex**的呼叫來終止執行緒，有助於確保正確復原配置給執行緒的資源。

**_endthread**會自動關閉執行緒控制碼，而 **_endthreadex**則不會。 因此，當您使用 **_beginthread**和 **_endthread**時，請不要藉由呼叫 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 來明確地關閉執行緒控制碼。 這個行為與 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面不同。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 **ExitThread** API，如此就不會防止執行時間系統回收配置的資源。 **_endthread**和 **_endthreadex**回收已配置的執行緒資源，然後呼叫**ExitThread**。

當呼叫 **_beginthread**或 **_beginthreadex**時，作業系統會處理堆疊的配置;您不需要將執行緒堆疊的位址傳遞給其中一個函式。 此外， *stack_size*引數可以是0，在此情況下，作業系統會使用與為主執行緒指定的堆疊相同的值。

*arglist*是要傳遞給新建立執行緒的參數。 這通常是資料項目的位址，例如字元字串。 如果不需要， *arglist*可以是**Null** ，但 **_beginthread**和 **_beginthreadex**必須提供一些值，才能傳遞給新的執行緒。 如果任何執行緒呼叫[abort](abort.md)、 **exit**、 **_exit**或**ExitProcess**，則所有線程都會終止。

新執行緒的地區設定會使用每個進程的全域目前地區設定資訊來初始化。 如果對[_configthreadlocale](configthreadlocale.md)的呼叫（全域或僅限新的執行緒）啟用個別執行緒地區設定，則執行緒可以藉由呼叫**setlocale**或 **_wsetlocale**，獨立變更其地區設定。 未設定每個執行緒地區設定旗標的執行緒，可能會影響所有其他執行緒中也不會設定每個執行緒地區設定旗標的地區設定資訊，以及所有新建立的執行緒。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

針對 **/clr**程式碼， **_beginthread**和 **_beginthreadex**都有兩個多載。 其中一個會採用原生呼叫慣例函式指標，另一個則會接受 **__clrcall**的函式指標。 第一個多載版本不是應用程式定義域安全的，而且永遠不會是。 如果您要撰寫 **/clr**程式碼，您必須先確定新的執行緒進入正確的應用程式域，然後才會存取受控資源。 例如，您可以使用 [call_in_appdomain 函式](../../dotnet/call-in-appdomain-function.md)來達成這個目的。 第二個多載是應用程式域安全的;新建立的執行緒一律會出現在 **_beginthread**或 **_beginthreadex**呼叫端的應用程式域中。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

若要使用 **_beginthread**或 **_beginthreadex**，應用程式必須與其中一個多執行緒 C 執行時間程式庫連結。

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

下列範例程式碼示範如何使用 **_beginthreadex**所傳回的執行緒控制碼與同步處理 API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)。 主執行緒會等待第二個執行緒終止後，再繼續執行。 當第二個執行緒呼叫 **_endthreadex**時，它會使其執行緒物件移至已發出信號的狀態。 這樣可讓主執行緒繼續執行。 這無法使用 **_beginthread**和 **_endthread**來完成，因為 **_endthread**會呼叫**CloseHandle**，這會先終結執行緒物件，然後才可以將它設定為已發出信號的狀態。

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

- [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)
- [_endthread、_endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit、_Exit、_exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
