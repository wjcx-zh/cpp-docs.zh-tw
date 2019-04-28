---
title: signal
ms.date: 04/12/2018
apiname:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 351bdbe1d787fc5e5d741460adfe415df7fda756
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356286"
---
# <a name="signal"></a>signal

設定插斷訊號處理。

> [!IMPORTANT]
> 請勿使用這個方法關閉 Microsoft Store 應用程式中，除了測試或偵錯案例。 以程式設計或 UI 方式關閉對市集應用程式不允許根據[Microsoft Store 原則](/legal/windows/agreements/store-policies)。 如需詳細資訊，請參閱 < [UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>參數

*sig*<br/>
訊號值。

*func*<br/>
第二個參數是要執行的函式的指標。 第一個參數是訊號值，而第二個參數是可在第一個參數是 SIGFPE 時使用的子程式碼。

## <a name="return-value"></a>傳回值

**訊號**傳回與指定訊號相關聯的函式的舊值。 比方說，如果先前的值*func*已**SIG_IGN**，則傳回值也是**SIG_IGN**。 傳回值**SIG_ERR**表示錯誤; 在此情況下， **errno**設定為**EINVAL**。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**訊號**函式可讓選擇數種方式可處理來自作業系統的插斷訊號的其中一個程序。 *Sig*引數是插斷**訊號**回應; 它必須是下列訊號中定義的資訊清單常數之一。H.

|*sig*值|描述|
|-----------------|-----------------|
|**SIGABRT**|異常終止|
|**SIGFPE**|浮點錯誤|
|**SIGILL**|不合法的指令|
|**SIGINT**|CTRL+C 訊號|
|**SIGSEGV**|不合法的儲存體存取|
|**SIGTERM**|終止要求|

如果*sig*不是其中一個以上的值，無效參數處理常式會叫用，如中所定義[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**SIG_ERR**。

根據預設，**訊號**終止呼叫程式，結束代碼為 3 的值為何*sig*。

> [!NOTE]
> **SIGINT**不支援任何 Win32 應用程式。 發生 CTRL+C 插斷時，Win32 作業系統會產生新的執行緒來專門處理該插斷。 這會讓單一執行緒應用程式 (例如 UNIX 中的應用程式) 成為多執行緒，並造成未預期的行為。

*Func*引數是您所撰寫訊號處理常式或其中一個預先定義的常數的位址**SIG_DFL**或是**SIG_IGN**，也會定義在訊號。H. 如果*func*是函式，則會安裝為指定訊號的訊號處理常式。 訊號處理常式的原型需要一個型式引數*sig*，型別的**int**。作業系統會提供透過實際的引數*sig*引數時中斷，就會發生; 是產生插斷的訊號。 因此，您可以在訊號處理常式中使用上表所列出的六個資訊清單常數，來決定發生何種插斷並採取適當動作。 例如，您可以呼叫**訊號**兩次，以便將相同的處理常式指派給兩個不同的訊號，然後測試*sig*來採取不同的動作處理常式中的引數會根據收到的訊號。

如果您要測試浮點例外狀況 (**SIGFPE**)， *func*指向接受選擇性的第二個引數的函式是其中一個數個資訊清單常數定義於浮點數。H、 的表單**FPE_xxx**。 當**SIGFPE**訊號時，您可以測試第二個引數，決定哪些類型的浮點例外狀況並採取適當的動作的值。 此引數和其可能值是 Microsoft 延伸模組。

針對浮點例外狀況，值*func*收到訊號時不會重設。 若要從浮點例外狀況復原，請使用 try/except 子句來括住浮點運算。 您也可以搭配使用 [setjmp](setjmp.md) 與 [longjmp](longjmp.md) 來進行復原。 在任一情況下，呼叫處理序都會繼續執行，並且保留處理序浮點狀態的未定義狀態。

如果傳回訊號處理常式，則呼叫處理序會緊接在收到插斷訊號之後繼續執行。 這不論訊號或作業模式的類型為何都適用。

指定的函式執行之前的值*func*設為**SIG_DFL**。 如所述處理下一個插斷訊號**SIG_DFL**，除非您的介入呼叫**訊號**指定不同的情況。 您可以使用這項功能來重設所呼叫函式中的訊號。

因為插斷時通常會以非同步方式呼叫訊號處理常式，所以執行階段作業未完成且處於未知狀態時，訊號處理常式函式可能會取得控制權。 下列清單摘要說明決定可在訊號處理常式中使用之函式的限制。

- 不發出低層級或 STDIO 執行動作。H I/O 常式 (例如**printf**或是**fread**)。

- 不要呼叫堆積常式或任何使用堆積常式 (例如**malloc**， **_strdup**，或 **_putenv**)。 如需詳細資訊，請參閱 [malloc](malloc.md)。

- 請勿使用任何產生系統呼叫的函式 (例如 **_getcwd**或是**時間**)。

- 請勿使用**longjmp**除非插斷浮點例外狀況所造成 (亦即*sig*會**SIGFPE**)。 在此情況下，第一次重新初始化浮點套件使用的呼叫來 **_fpreset**。

- 請不要使用任何重疊常式。

程式必須包含浮點程式碼，如果要捕捉**SIGFPE**使用函式的例外狀況。 如果您的程式沒有浮點程式碼，而且需要執行階段程式庫的訊號處理程式碼，則只需要宣告違規的雙精度浮點數，並將它初始化為零︰

```C
volatile double d = 0.0f;
```

**SIGILL**並**SIGTERM** Windows 下不會產生信號。 它們是基於 ANSI 相容性所加入。 因此，您可以透過設定這些訊號的訊號處理常式**訊號**，並呼叫，您可以明確地產生這些訊號[引發](raise.md)。

訊號設定不會保留在繁衍的處理序，藉由呼叫[_exec](../../c-runtime-library/exec-wexec-functions.md)或是[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函式。 訊號設定會在新處理序中重設為預設值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**signal**|\<signal.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

下列範例示範如何使用**訊號**來加入一些自訂行為來**SIGABRT**訊號。 如需中止行為的其他資訊，請參閱 [_set_abort_behavior](set-abort-behavior.md)。

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
