---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: fd3a3c2f99d1702cdccf68328c2122b965b2d078
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337875"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

指定要在程式異常終止時採取的動作。

> [!NOTE]
> 請勿使用[中止](abort.md)函數關閉 Microsoft 應用商店應用,除非在測試或調試方案中。 根據[Microsoft 應用商店策略](/legal/windows/agreements/store-policies),不允許以程式設計或 UI 方式關閉應用商店應用。 有關詳細資訊,請參閱[UWP 應用生命週期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>語法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>參數

*標誌*<br/>
[中止](abort.md)標誌的新值。

*遮罩*<br/>
[要設置的中止](abort.md)標誌位的掩碼。

## <a name="return-value"></a>傳回值

旗標的舊值。

## <a name="remarks"></a>備註

有兩個[中止](abort.md)旗標 **:_WRITE_ABORT_MSG**與 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**確定在程式異常終止時是否列印有用的文本消息。 消息指出應用程式已調用[中止](abort.md)函數。 預設行為是列印訊息。 **_CALL_REPORTFAULT**(如果已設定)指定在調用[中止](abort.md)時生成並報告 Watson 崩潰轉儲。 根據預設，會在非偵錯組建中啟用損毀傾印報告。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
