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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348667"
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
開始執行新執行緒之常式的起始位址。 對於 **_beginthread**,調用[約定__cdecl(](../../cpp/cdecl.md)對於本機代碼)或[__clrcall(](../../cpp/clrcall.md)對於託管代碼);對於 **_beginthreadex,**[它__stdcall(](../../cpp/stdcall.md)對於本機代碼)或[__clrcall(](../../cpp/clrcall.md)對於託管代碼)。

*stack_size*<br/>
新執行緒堆疊大小或 0。

*阿格列斯*<br/>
要傳遞給新緒的參數清單或**NULL**。

*安全性*<br/>
[SECURITY ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果*安全*為**NULL,** 則無法繼承該句柄。 對於 Windows 95 應用程式,必須**為 NULL。**

*initflag*<br/>
控制新執行緒之初始狀態的旗標。 將*initflag*設置為 0 以立即運行,或**CREATE_SUSPENDED**以在掛起狀態下建立線程;使用[ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread)執行線程。 將*initflag*設置為**STACK_SIZE_PARAM_IS_A_RESERVATION**標誌,以使用*stack_size*作為堆疊的初始保留大小(以位元組為單位);如果未指定此標誌 *,stack_size*指定提交大小。

*地addr*<br/>
指向接收執行緒識別項的 32 位元變數。 如果是**NULL,** 則不使用。

## <a name="return-value"></a>傳回值

如果成功,這些函數中的每一個都會返回一個句柄到新創建的線程;如果成功,則每個函數都會向新創建的線程返回一個句柄。但是,如果新創建的線程退出速度過快 **,_beginthread**可能不會返回有效的句柄。 (請參閱備註部分的討論。在錯誤時 **,_beginthread**返回 -1L,如果線程太多,**則將 errno**設置為**EAGAIN;** 如果參數無效或堆疊大小不正確,則將錯誤設置為**EAGAIN;** 如果資源不足(如記憶體),則將錯誤設置為**EAGAIN。** 錯誤時 **,_beginthreadex**返回 0,並設置**errno**和 **_doserrno。**

如果*start_address*為**NULL,** 則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設置為**EINVAL**並返回 -1。

有關這些代碼和其他返回代碼的詳細資訊,請參閱[errno、_doserrno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有關**uintptr_t**的詳細資訊,請參閱[標準類型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>備註

**_beginthread**函數創建一個線程,該線程開始在*start_address*處執行例程。 *start_address*的例程必須使用 **__cdecl(** 對於本機代碼)或 **__clrcall(** 對於託管代碼)調用約定,並且不應具有返回值。 執行緒從該常式返回時，就會自動終止。 如需執行緒的詳細資訊，請參閱[舊版程式碼的多執行緒支援 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**與 Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API 更類似於 **_beginthread。** **_beginthreadex**在以下方面不同於 **_beginthread:**

- **_beginthreadex**有三個額外的參數 *:initflag,**安全和***執行緒 。** 新線程可以在具有指定安全性的掛起狀態下創建,並且可以使用*thrdaddr*(線程標識符)進行訪問。

- 傳遞給 *_beginthreadexstart_address*的例程必須使用 **__stdcall(** 對於本 **_beginthreadex**機代碼)或 **__clrcall(** 對於託管代碼)調用約定,並且必須返回線程退出代碼。

- **_beginthreadex**在故障時返回 0,而不是 -1L。

- 使用 **_beginthreadex**創建的線程由對[_endthreadex](endthread-endthreadex.md)的調用終止。

與 **_beginthread**相比 **,_beginthreadex**函數使您能夠對線程的創建方式進行更多的控制。 **_endthreadex**功能也更加靈活。 例如,使用 **_beginthreadex**,可以使用安全資訊、設置線程的初始狀態(運行或掛起),並獲取新創建的線程的線程標識符。 您還可以使用 **_beginthreadex**返回的線程句柄與同步 API 一起,而_beginthread無法執行該**操作。**

使用 **_beginthreadex**比 **_beginthread**更安全。 如果 **_beginthread**生成的線程快速退出,則返回給 **_beginthread**調用方的句柄可能無效或指向另一個線程。 但是 **,_beginthreadex**返回的句柄必須由 **_beginthreadex**的調用方關閉,因此,如果 **_beginthreadex**未返回錯誤,則保證該句柄是有效的句柄。

您可以顯式調用[_endthread](endthread-endthreadex.md)或 **_endthreadex**以終止線程;否則,您可以顯式調用線程。但是,當線程從作為參數傳遞的例程返回時,將自動調用 **_endthread**或 **_endthreadex。** 終止調用 **_endthread**或 **_endthreadex**的線程有助於確保正確恢復分配給該線程的資源。

**_endthread**自動關閉線程句柄,而 **_endthreadex**則不關閉線程句柄。 因此,當您使用 **_beginthread**和 **_endthread**時,不要通過調用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 顯式關閉線程句柄。 這個行為與 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面不同。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔,不要調用 Win32 **ExitThread** API,以免阻止運行時系統回收已分配的資源。 **_endthread****和_endthreadex**回收分配的線程資源,然後呼叫**ExitThread**。

調用 **_beginthread**或 **_beginthreadex**時,操作系統處理堆疊的分配;您不必將線程堆疊的位址傳遞給這些函數中的任何一個。 此外 *,stack_size*參數可以是 0,在這種情況下,操作系統使用的值與為主線程指定的堆疊相同的值。

*arglist*是要傳遞給新創建的線程的參數。 這通常是資料項目的位址，例如字元字串。 如果不需要 *,arglist*可以是**NULL,****但必須**_beginthread和 **_beginthreadex**才能傳遞給新線程。 如果任何線程呼叫[中止](abort.md)、**退出****、_exit**或**退出進程**,則所有線程都終止。

使用每個進程全域當前區域設置資訊初始化新線程區域設置。 如果每個線程區域設置透過呼叫[_configthreadlocale(](configthreadlocale.md)全域或僅針對新線程)啟用,則執行緒可以透過調用**setlocale**或 **_wsetlocale**獨立於其他執行緒更改其區域設定。 沒有每個線程區域設置標誌集的線程可能會影響所有其他線程中區域設置資訊,這些線程也沒有設置每個線程區域設置標誌集,以及所有新創建的線程。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

對於 **/clr**代碼 **,_beginthread**和 **_beginthreadex**各有兩個重載。 一個採用本機調用約定函數指標,另一個採用 **__clrcall**函數指標。 第一個多載版本不是應用程式定義域安全的，而且永遠不會是。 如果要編寫 **/clr**代碼,必須確保新線程在訪問託管資源之前輸入正確的應用程式域。 例如，您可以使用 [call_in_appdomain 函式](../../dotnet/call-in-appdomain-function.md)來達成這個目的。 第二個重載是應用程序域安全;新創建的線程將始終位於 **_beginthread**或 **_beginthreadex**調用方的應用程式域中。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

要使用 **_beginthread**或 **_beginthreadex,** 應用程式必須與其中一個多線程 C 運行時庫連結。

## <a name="example"></a>範例

下面的示例使用 **_beginthread**和 **_endthread。**

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

以下範例代碼展示如何使用 **_beginthreadex**與同步API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)一起返回的線程句柄。 主執行緒會等待第二個執行緒終止後，再繼續執行。 當第二個線程調用 **_endthreadex**,它會導致其線程對象進入信號狀態。 這樣可讓主執行緒繼續執行。 這不能用 **_beginthread**和 **_endthread,** 因為 **_endthread**調用**CloseHandle,** 這將線上程物件設置為信號狀態之前銷毀它。

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
