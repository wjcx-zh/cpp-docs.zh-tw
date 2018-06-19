---
title: signal | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- signal function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a87978ec3b0840be6ab1779af86765208c80832c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416816"
---
# <a name="signal"></a>signal

設定插斷訊號處理。

> [!IMPORTANT]
> 請勿使用這個方法關閉 Microsoft 市集應用程式中，除了測試或偵錯案例。 透過程式設計或 UI 兩種方式關閉市集應用程式不允許根據[Microsoft 市集原則](http://go.microsoft.com/fwlink/?LinkId=865936)。 如需詳細資訊，請參閱[UWP 應用程式生命週期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>語法

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>參數

*sig*<br/>
訊號值。

*func*<br/>
第二個參數是要執行函式的指標。 第一個參數是訊號值，而第二個參數是可在第一個參數是 SIGFPE 時使用的子程式碼。

## <a name="return-value"></a>傳回值

**訊號**傳回具有相關聯的特定訊號的 func 的舊值。 例如，如果先前的值*func*已**SIG_IGN**，傳回值也是**SIG_IGN**。 傳回值為**SIG_ERR**表示發生錯誤; 在此情況下， **errno**設**EINVAL**。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**訊號**函式可以讓選擇數種方式來處理從作業系統的插斷訊號的其中一個程序。 *Sig*引數是要插斷**訊號**回應; 它必須是下列訊號中定義的資訊清單常數之一。H.

|*sig*值|描述|
|-----------------|-----------------|
|**SIGABRT**|異常終止|
|**SIGFPE**|浮點錯誤|
|**SIGILL**|不合法的指令|
|**SIGINT**|CTRL+C 訊號|
|**SIGSEGV**|不合法的儲存體存取|
|**SIGTERM**|終止要求|

如果*sig*不是其中一個上述值的無效參數處理常式會叫用，如中所定義[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**SIG_ERR**。

根據預設，**訊號**結束呼叫程式，結束代碼為 3 的值為何*sig*。

> [!NOTE]
> **SIGINT**不支援任何的 Win32 應用程式。 發生 CTRL+C 插斷時，Win32 作業系統會產生新的執行緒來專門處理該插斷。 這會讓單一執行緒應用程式 (例如 UNIX 中的應用程式) 成為多執行緒，並造成未預期的行為。

*Func*引數是您撰寫，訊號處理常式或其中一個預先定義的常數的位址**SIG_DFL**或**SIG_IGN**，也會定義訊號。H. 如果*func*是函式，則會安裝為特定訊號的訊號處理常式。 訊號處理常式的原型需要一個型式引數， *sig*，型別**int**。作業系統會提供實際的引數，透過*sig*引數時中斷，就會發生; 是產生插斷的訊號。 因此，您可以在訊號處理常式中使用上表所列出的六個資訊清單常數，來決定發生何種插斷並採取適當動作。 例如，您可以呼叫**訊號**兩次，將相同的處理常式指派給兩個不同的訊號，然後再測試*sig*採取不同的動作處理常式中的引數會根據收到的訊號。

如果您要測試的浮點例外狀況 (**SIGFPE**)， *func*指向接受選擇性的第二個引數的函式是數個資訊清單常數，定義浮點數的其中一個。H、 表單的**FPE_xxx**。 當**SIGFPE**訊號發生時，您可以測試判斷的浮點例外狀況類型，然後再採取適當動作的第二個引數的值。 此引數和其可能值是 Microsoft 延伸模組。

對於浮點例外狀況，值*func*收到信號時不會重設。 若要從浮點例外狀況復原，請使用 try/except 子句來括住浮點運算。 您也可以搭配使用 [setjmp](setjmp.md) 與 [longjmp](longjmp.md) 來進行復原。 在任一情況下，呼叫處理序都會繼續執行，並且保留處理序浮點狀態的未定義狀態。

如果傳回訊號處理常式，則呼叫處理序會緊接在收到插斷訊號之後繼續執行。 這不論訊號或作業模式的類型為何都適用。

指定的函式執行之前，值*func*設**SIG_DFL**。 下一步的插斷訊號會被視為所述，對**SIG_DFL**，除非您有中間呼叫**訊號**另外指定。 您可以使用這項功能來重設所呼叫函式中的訊號。

因為插斷時通常會以非同步方式呼叫訊號處理常式，所以執行階段作業未完成且處於未知狀態時，訊號處理常式函式可能會取得控制權。 下列清單摘要說明決定可在訊號處理常式中使用之函式的限制。

- 不問題低層級或 STDIO 執行動作。H I/O 常式 (例如， **printf**或**fread**)。

- 請勿呼叫堆積常式或堆積常式所使用的任何常式 (例如， **malloc**， **_strdup**，或 **_putenv**)。 如需詳細資訊，請參閱 [malloc](malloc.md)。

- 不使用任何會產生系統呼叫的函式 (例如， **_getcwd**或**時間**)。

- 請勿使用**longjmp**除非插斷的起因是浮點例外狀況 (也就是*sig*是**SIGFPE**)。 在此情況下，第一次使用重新初始化浮點封裝呼叫 **_fpreset**。

- 請不要使用任何重疊常式。

設陷時，程式必須包含浮點程式碼**SIGFPE**使用函式的例外狀況。 如果您的程式沒有浮點程式碼，而且需要執行階段程式庫的訊號處理程式碼，則只需要宣告違規的雙精度浮點數，並將它初始化為零︰

```C
volatile double d = 0.0f;
```

**SIGILL**和**SIGTERM** windows 不會產生信號。 它們是基於 ANSI 相容性所加入。 因此，您可以設定這些訊號的訊號處理常式使用**訊號**，而且可以藉由呼叫也會明確產生這些訊號[引發](raise.md)。

訊號設定不會保留在繁衍的處理序的呼叫所建立的[_exec](../../c-runtime-library/exec-wexec-functions.md)或[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函式。 訊號設定會在新處理序中重設為預設值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**signal**|\<signal.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

下列範例示範如何使用**訊號**新增一些自訂表現方式以**SIGABRT**訊號。 如需中止行為的其他資訊，請參閱 [_set_abort_behavior](set-abort-behavior.md)。

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
