---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 04869412272725108911f13857585e650ad20ab9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948091"
---
# <a name="signal"></a>signal

設定插斷訊號處理。

> [!IMPORTANT]
> 請勿使用此方法來關閉 Microsoft Store 應用程式，但在測試或偵測案例中除外。 根據[Microsoft Store 的原則](/legal/windows/agreements/store-policies)，不允許以程式設計或 UI 方式關閉存放區應用程式。 如需詳細資訊，請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>參數

*sig*<br/>
訊號值。

*func*<br/>
第二個參數是要執行之函式的指標。 第一個參數是訊號值，而第二個參數是可在第一個參數是 SIGFPE 時使用的子程式碼。

## <a name="return-value"></a>傳回值

**信號**會傳回與指定信號相關聯的先前函數值。 例如，如果**SIG_IGN** *先前的值*，則傳回值也會是**SIG_IGN**。 **SIG_ERR**的傳回值表示發生錯誤;在此情況下， **errno**會設定為**EINVAL**。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**信號**函式可讓處理常式選擇數種方式的其中一種，以處理來自作業系統的插斷信號。 *Sig*引數是指**信號**回應的中斷;它必須是下列其中一個資訊清單常數，其定義為 [信號]。H.

|*sig*值|描述|
|-----------------|-----------------|
|**SIGABRT**|異常終止|
|**SIGFPE**|浮點錯誤|
|**SIGILL**|不合法的指令|
|**SIGINT**|CTRL+C 訊號|
|**SIGSEGV**|不合法的儲存體存取|
|**SIGTERM**|終止要求|

如果*sig*不是上述其中一個值，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所定義。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**SIG_ERR**。

根據預設，**信號**會以結束代碼3結束通話程式，而不論*sig*的值為何。

> [!NOTE]
> 任何 Win32 應用程式都不支援**SIGINT** 。 發生 CTRL+C 插斷時，Win32 作業系統會產生新的執行緒來專門處理該插斷。 這會讓單一執行緒應用程式 (例如 UNIX 中的應用程式) 成為多執行緒，並造成未預期的行為。

*Func*引數是您所撰寫之信號處理常式的位址，或其中一個預先定義的常數**SIG_DFL**或**SIG_IGN**，它們也會定義為「信號」。H. 如果*func*是函式，它會安裝為指定信號的信號處理常式。 信號處理常式的原型需要類型為**int**的一個正式引數（ *sig*）。當發生中斷時，作業系統會透過*sig*提供實際的引數;引數是產生中斷的信號。 因此，您可以在訊號處理常式中使用上表所列出的六個資訊清單常數，來決定發生何種插斷並採取適當動作。 例如，您可以呼叫**信號**兩次，將相同的處理常式指派給兩個不同的信號，然後測試處理常式中的*sig*引數，以根據收到的信號採取不同的動作。

如果您測試的是浮點例外狀況（**SIGFPE**）， *func*會指向接受選擇性第二個引數的函式，而這是在 FLOAT 中定義的數個資訊清單常數之一。H，格式為**FPE_xxx**。 當**SIGFPE**信號發生時，您可以測試第二個引數的值來判斷浮點例外狀況的類型，然後採取適當的動作。 此引數和其可能值是 Microsoft 延伸模組。

對於浮點例外狀況，當收到信號時，不會重設*func*的值。 若要從浮點例外狀況復原，請使用 try/except 子句來括住浮點運算。 您也可以搭配使用 [setjmp](setjmp.md) 與 [longjmp](longjmp.md) 來進行復原。 在任一情況下，呼叫處理序都會繼續執行，並且保留處理序浮點狀態的未定義狀態。

如果傳回訊號處理常式，則呼叫處理序會緊接在收到插斷訊號之後繼續執行。 這不論訊號或作業模式的類型為何都適用。

在執行指定的函式之前， *func*的值會設定為**SIG_DFL**。 下一個中斷信號會如**SIG_DFL**所述處理，除非呼叫**信號**另有指定。 您可以使用這項功能來重設所呼叫函式中的訊號。

因為插斷時通常會以非同步方式呼叫訊號處理常式，所以執行階段作業未完成且處於未知狀態時，訊號處理常式函式可能會取得控制權。 下列清單摘要說明決定可在訊號處理常式中使用之函式的限制。

- 請勿發出低層級或 STDIO.H。H i/o 常式（例如**printf**或**fread**）。

- 請勿呼叫堆積常式或任何使用堆積常式的常式（例如， **malloc**、 **_strdup**或 **_putenv**）。 如需詳細資訊，請參閱 [malloc](malloc.md)。

- 請勿使用任何會產生系統呼叫的函數（例如， **_getcwd**或**time**）。

- 除非中斷是因浮點例外狀況（也就是**SIGFPE**的*sig* ）所造成，否則請勿使用**longjmp** 。 在此情況下，請先使用 **_fpreset**的呼叫來重新初始化浮點封裝。

- 請不要使用任何重疊常式。

如果程式要使用函式來捕捉**SIGFPE**例外狀況，就必須包含浮點程式碼。 如果您的程式沒有浮點程式碼，而且需要執行階段程式庫的訊號處理程式碼，則只需要宣告違規的雙精度浮點數，並將它初始化為零︰

```C
volatile double d = 0.0f;
```

在 Windows 下不會產生**SIGILL**和**SIGTERM**信號。 它們是基於 ANSI 相容性所加入。 因此，您可以使用**信號**來設定這些信號的信號處理常式，也可以藉由呼叫[raise](raise.md)來明確產生這些信號。

信號設定不會保留在衍生的進程中，由呼叫[_exec](../../c-runtime-library/exec-wexec-functions.md)或[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函數所建立。 訊號設定會在新處理序中重設為預設值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**signal**|\<signal.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

下列範例顯示如何使用**信號**，將一些自訂行為新增至**SIGABRT**信號。 如需中止行為的其他資訊，請參閱 [_set_abort_behavior](set-abort-behavior.md)。

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
