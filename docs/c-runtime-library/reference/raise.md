---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 81b92404603820948a384b6ad33421251a27c13c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919554"
---
# <a name="raise"></a>raise

將訊號傳送到執行中的程式。

> [!NOTE]
> 請勿使用此方法來關閉 Microsoft Store 應用程式，但在測試或偵測案例中除外。 根據[Microsoft Store 的原則](/legal/windows/agreements/store-policies)，不允許以程式設計或 UI 方式關閉存放區應用程式。 如需詳細資訊，請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>參數

*sig*<br/>
要產生的訊號。

## <a name="return-value"></a>傳回值

如果成功，**raise** 會傳回 0。 否則，它會傳回非零值。

## <a name="remarks"></a>備註

**raise** 函式傳送 *sig* 給執行中的程式。 如果先前的 **signal** 呼叫已安裝 *sig* 的訊號處理函式，則 **raise** 會執行該函式。 如果尚未安裝任何處理常式函式，會採取與訊號值 *sig* 相關聯的預設動作，如下所示。

|訊號|意義|預設值|
|------------|-------------|-------------|
|**SIGABRT**|異常終止|結束呼叫程式，結束代碼 3|
|**SIGFPE**|浮點錯誤|結束呼叫程式|
|**SIGILL**|不合法的指令|結束呼叫程式|
|**SIGINT**|CTRL+C 中斷|結束呼叫程式|
|**SIGSEGV**|不合法的儲存體存取|結束呼叫程式|
|**SIGTERM**|終止傳送給程式的要求|忽略訊號|

如果引數不是有效的訊號，如上述所指定，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果未處理，函式會將**errno**設定為**EINVAL** ，並傳回非零值。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**raise**|\<signal.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
