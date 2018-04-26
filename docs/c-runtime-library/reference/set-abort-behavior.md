---
title: _set_abort_behavior | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7ee65b603997a0be4fe9e937299eab9520c6f5b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

指定要在程式異常終止時採取的動作。

> [!NOTE]
> 請勿使用[中止](abort.md)關閉 Microsoft 市集應用程式中，除了測試或偵錯案例中的函式。 透過程式設計或 UI 兩種方式關閉市集應用程式不允許根據[Microsoft 市集原則](http://go.microsoft.com/fwlink/?LinkId=865936)。 如需詳細資訊，請參閱[UWP 應用程式生命週期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

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

*遮罩*<br/>
遮罩[中止](abort.md)加上旗標設定的位元。

## <a name="return-value"></a>傳回值

旗標的舊值。

## <a name="remarks"></a>備註

有兩個[中止](abort.md)旗標： **_WRITE_ABORT_MSG**和 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**決定是否要在程式異常終止時，列印很有幫助的文字訊息。 此訊息會說明應用程式已呼叫[中止](abort.md)函式。 預設行為是列印訊息。 **_CALL_REPORTFAULT**，如果設定，指定會產生 Watson 損毀傾印，並報告時[中止](abort.md)呼叫。 根據預設，會在非偵錯組建中啟用損毀傾印報告。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
