---
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350921"
---
# <a name="abort"></a>abort

中止目前的處理序，並傳回錯誤碼。

> [!NOTE]
> 除非在測試或調試方案中,否則不要使用此方法關閉 Microsoft 應用商店應用或通用 Windows 平臺 (UWP) 應用。 根據[Microsoft 應用商店策略](/legal/windows/agreements/store-policies),不允許以程式設計或 UI 方式關閉應用商店應用。 有關詳細資訊,請參閱[UWP 應用生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
void abort( void );
```

## <a name="return-value"></a>傳回值

**中止**不會將控制權返回到調用進程。 根據預設，它會檢查是否有中止訊號處理常式；如有設定，則會引發 `SIGABRT`。 然後**中止**終止當前進程,並將退出代碼返回給父進程。

## <a name="remarks"></a>備註

**Microsoft 特定的**

預設情況下,當使用除錯執行時庫生成應用時,**中止**例程會在引發`SIGABRT`之前 顯示錯誤訊息。 若是在主控台模式中執行的主控台應用程式，訊息會傳送至 `STDERR`。 在視窗模式中執行的 Windows 傳統型應用程式和主控台應用程式會在訊息方塊中顯示訊息。 若要隱藏訊息，請使用 [_set_abort_behavior](set-abort-behavior.md) 清除 `_WRITE_ABORT_MSG` 旗標。 顯示的訊息取決於所使用的執行階段環境版本。 對於使用最新版本的 Visual C++構建的應用程式,該消息類似於:

> R6010 - 中止()已呼叫

在舊版 C 執行階段程式庫中，會顯示下列訊息：

> 此應用程式已要求執行階段以異常方式終止它。 如需詳細資訊，請連絡應用程式支援小組。

當程式是在偵錯模式中編譯時，訊息方塊會顯示 [中止]****、[重試]**** 或 [略過]**** 選項。 如果使用者選擇 [中止]****，程式會立即終止，並傳回結束代碼 3。 如果使用者選擇 [重試]****，則會叫用偵錯工具進行 Just-in-Time 偵錯 (如果有)。 如果使用者選擇 **「忽略」****中止**將繼續正常處理。

在零售和調試版本中,**中止**然後檢查是否設置了中止信號處理程式。 如果設定非預設信號處理程式,**請中止**呼叫`raise(SIGABRT)`。 使用 [signal](signal.md) 函式可建立中止訊號處理函式與 `SIGABRT` 訊號的關聯。 您可以執行自訂動作 (例如清除資源或記錄資訊)，然後終止應用程式並在處理函式中顯示您自己的錯誤碼。 如果未定義自訂訊號處理程式,**則中止**不會引發`SIGABRT`訊號。

預設情況下,在桌面或控制台應用的非調試版本中,**中止**然後調用 Windows 錯誤報告服務機制(以前稱為 Watson 博士)向 Microsoft 報告故障。 此行為可藉由呼叫 `_set_abort_behavior` 和設定來啟用，或藉由遮罩 `_CALL_REPORTFAULT` 旗標來停用。 設定旗標時，Windows 會顯示一個訊息方塊，其中包含類似「由於發生問題，導致程式停止正常運作」的文字。 使用者可以選擇使用 [偵錯]**** 按鈕叫用偵錯工具，或選擇 [關閉程式]**** 終止應用程式並顯示作業系統所定義的錯誤碼。

如果未呼叫 Windows 錯誤報告處理程式,則**中止**[呼叫_exit](exit-exit-exit.md)終止使用退出代碼 3 的進程,並將控制權返回到父進程或作業系統。 `_exit` 不會排清資料流緩衝區，也不會進行 `atexit`/`_onexit` 處理。

如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

**結束 Microsoft 專有**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**abort**|\<process.h> 或 \<stdlib.h>|

## <a name="example"></a>範例

下列程式會嘗試開啟檔案，並在嘗試失敗時中止。

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>另請參閱

[使用 abort](../../cpp/using-abort.md)<br/>
[中止函數](../../c-language/abort-function-c.md)<br/>
[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[信號](signal.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
