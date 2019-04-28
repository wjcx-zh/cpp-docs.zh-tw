---
title: _set_abort_behavior
ms.date: 1/02/2018
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
ms.openlocfilehash: 8b36a771a3694c6d01573d619990743c7ddc0f3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356682"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

指定要在程式異常終止時採取的動作。

> [!NOTE]
> 請勿使用[中止](abort.md)函式來關閉 Microsoft Store 應用程式中，除了測試或偵錯案例。 以程式設計或 UI 方式關閉對市集應用程式不允許根據[Microsoft Store 原則](/legal/windows/agreements/store-policies)。 如需詳細資訊，請參閱 < [UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>參數

*flags*<br/>
新值[中止](abort.md)旗標。

*mask*<br/>
遮罩[中止](abort.md)旗標設定的位元。

## <a name="return-value"></a>傳回值

旗標的舊值。

## <a name="remarks"></a>備註

有兩個[中止](abort.md)旗標： **_WRITE_ABORT_MSG**並 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**決定是否要在程式異常終止時，列印有用的文字訊息。 此訊息說明應用程式已呼叫[中止](abort.md)函式。 預設行為是列印訊息。 **_CALL_REPORTFAULT**，如果設定，可指定 Watson 損毀傾印產生，並回報的時機[中止](abort.md)呼叫。 根據預設，會在非偵錯組建中啟用損毀傾印報告。

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
