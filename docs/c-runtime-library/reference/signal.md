---
title: signal | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: signal
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
f1_keywords: signal
dev_langs: C++
helpviewer_keywords: signal function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 337bc5e222ee7fcb313d0b7ea0722dbb5cacea75
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="signal"></a>signal

設定插斷訊號處理。

> [!IMPORTANT]
> 請勿使用這個方法關閉 Microsoft 市集應用程式中，除了測試或偵錯案例。 透過程式設計或 UI 兩種方式關閉市集應用程式不允許根據[Microsoft 市集原則](http://go.microsoft.com/fwlink/?LinkId=865936)。 如需詳細資訊，請參閱[UWP 應用程式生命週期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>語法

```C
void (__cdecl *signal(
   int sig,
   void (__cdecl *func ) (int [, int ] )))(int);
```

### <a name="parameters"></a>參數
_sig_  
訊號值。

_函式_  
要執行的函式。 第一個參數是訊號值，而第二個參數是可在第一個參數是 SIGFPE 時使用的子程式碼。

## <a name="return-value"></a>傳回值

`signal`傳回先前的值_func_ ，具有相關聯的特定的訊號。 例如，如果先前的值_func_已`SIG_IGN`，傳回值也是`SIG_IGN`。 傳回值 `SIG_ERR` 表示錯誤；在該情況下，`errno` 會設為 `EINVAL`。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

`signal` 函式可讓處理序選擇數種方式中的其中一種來處理來自作業系統的插斷訊號。 _Sig_引數是要插斷`signal`回應; 它必須是下列訊號中定義的資訊清單常數之一。H.

|_sig_值|描述|
|-----------------|-----------------|
|`SIGABRT`|異常終止|
|`SIGFPE`|浮點錯誤|
|`SIGILL`|不合法的指令|
|`SIGINT`|CTRL+C 訊號|
|`SIGSEGV`|不合法的儲存體存取|
|`SIGTERM`|終止要求|

如果_sig_不是其中一個上述值的無效參數處理常式會叫用，如中所定義[參數驗證](../../c-runtime-library/parameter-validation.md)。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `SIG_ERR`。

根據預設，`signal`結束呼叫程式，結束代碼為 3 的值為何_sig_。

> [!NOTE]
> 任何 Win32 應用程式都不支援 `SIGINT`。 發生 CTRL+C 插斷時，Win32 作業系統會產生新的執行緒來專門處理該插斷。 這會讓單一執行緒應用程式 (例如 UNIX 中的應用程式) 成為多執行緒，並造成未預期的行為。

_Func_引數是您撰寫，訊號處理常式或其中一個預先定義的常數的位址`SIG_DFL`或`SIG_IGN`，也會定義訊號。H. 如果_func_是函式，則會安裝為特定訊號的訊號處理常式。 訊號處理常式的原型需要一個型式引數， _sig_，型別`int`。 作業系統會提供實際的引數，透過_sig_引數時中斷，就會發生; 是產生插斷的訊號。 因此，您可以在訊號處理常式中使用上表所列出的六個資訊清單常數，來決定發生何種插斷並採取適當動作。 例如，您可以呼叫`signal`兩次，將相同的處理常式指派給兩個不同的訊號，然後再測試_sig_採取不同的動作處理常式中的引數會根據收到的訊號。

如果您要測試的浮點例外狀況 (`SIGFPE`)， _func_指向接受選擇性的第二個引數的數個資訊清單常數之一的函式-定義浮點數。H-表單的`FPE_xxx`。 發出 `SIGFPE` 訊號時，您可以測試第二個引數的值來決定浮點例外狀況的類型，然後採取適當的動作。 此引數和其可能值是 Microsoft 延伸模組。

對於浮點例外狀況，值_func_收到信號時不會重設。 若要從浮點例外狀況復原，請使用 try/except 子句來括住浮點運算。 您也可以搭配使用 [setjmp](../../c-runtime-library/reference/setjmp.md) 與 [longjmp](../../c-runtime-library/reference/longjmp.md) 來進行復原。 在任一情況下，呼叫處理序都會繼續執行，並且保留處理序浮點狀態的未定義狀態。

如果傳回訊號處理常式，則呼叫處理序會緊接在收到插斷訊號之後繼續執行。 這不論訊號或作業模式的類型為何都適用。

指定的函式執行之前，值_func_設`SIG_DFL`。 除非指定 `signal` 的介入呼叫，否則會針對 `SIG_DFL` 所述處理下一個插斷訊號。 您可以使用這項功能來重設所呼叫函式中的訊號。

因為插斷時通常會以非同步方式呼叫訊號處理常式，所以執行階段作業未完成且處於未知狀態時，訊號處理常式函式可能會取得控制權。 下列清單摘要說明決定可在訊號處理常式中使用之函式的限制。

- 請不要發出低層級或 STDIO.H I/O 常式 (例如，`printf` 或 `fread`)。

- 請不要呼叫堆積常式或任何使用堆積常式的常式 (例如，`malloc`、`_strdup` 或 `_putenv`)。 如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。

- 請不要使用任何產生系統呼叫的函式 (例如，`_getcwd` 或 `time`)。

- 請勿使用`longjmp`除非插斷的起因是浮點例外狀況 (也就是_sig_是`SIGFPE`)。 在此情況下，請先使用 `_fpreset` 呼叫來重新初始化浮點套件。

- 請不要使用任何重疊常式。

如果程式是要使用此函式來設陷 `SIGFPE` 例外狀況，則必須包含浮點程式碼。 如果您的程式沒有浮點程式碼，而且需要執行階段程式庫的訊號處理程式碼，則只需要宣告違規的雙精度浮點數，並將它初始化為零︰

`volatile double d = 0.0f;`

在 Windows 下不會產生 `SIGILL` 和 `SIGTERM` 訊號。 它們是基於 ANSI 相容性所加入。 因此，您可以使用 `signal` 來設定這些訊號的訊號處理常式，也可以呼叫 [raise](../../c-runtime-library/reference/raise.md) 來明確地產生這些訊號。

訊號設定不會保留在透過呼叫 `_exec` 或 `_spawn` 函式所建立的繁衍處理序中。 訊號設定會在新處理序中重設為預設值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`signal`|\<signal.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

下列範例示範如何使用 `signal`，將一些自訂行為新增至 `SIGABRT` 訊號。 如需中止行為的其他資訊，請參閱 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)。

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

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)  
[exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[_fpreset](../../c-runtime-library/reference/fpreset.md)  
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)  
