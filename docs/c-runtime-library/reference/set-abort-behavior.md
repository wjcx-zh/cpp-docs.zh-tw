---
title: _set_abort_behavior
ms.date: 01/02/2018
apiname:
- _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: b72a485287684fc85f1e232e89774e07a5e3f42b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927482"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

指定要在程式異常終止時採取的動作。

> [!NOTE]
> 請勿使用[abort](abort.md)函式來關閉 Microsoft Store 應用程式，但不包括測試或偵測案例。 根據[Microsoft Store 的原則](/legal/windows/agreements/store-policies)，不允許以程式設計或 UI 方式關閉存放區應用程式。 如需詳細資訊，請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>參數

*flags*<br/>
[Abort](abort.md)旗標的新值。

*mask*<br/>
要設定之[中止](abort.md)旗標位的遮罩。

## <a name="return-value"></a>傳回值

旗標的舊值。

## <a name="remarks"></a>備註

有兩個[中止](abort.md)旗標： **_WRITE_ABORT_MSG**和 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**決定當程式異常終止時，是否要列印有用的文字訊息。 訊息指出應用程式已呼叫[abort](abort.md)函數。 預設行為是列印訊息。 如果設定， **_CALL_REPORTFAULT**會指定在呼叫[Abort](abort.md)時產生 Watson 損毀傾印並回報。 根據預設，會在非偵錯組建中啟用損毀傾印報告。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>另請參閱

[abort](abort.md)<br/>
