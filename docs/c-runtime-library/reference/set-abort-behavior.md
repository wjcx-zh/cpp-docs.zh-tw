---
title: _set_abort_behavior | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 965ff160fd8098c60f53f639cb95aedf890edd86
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

指定要在程式異常終止時採取的動作。

> [!NOTE]
> 請勿使用`abort`關閉 Microsoft 市集應用程式中，除了測試或偵錯案例中的函式。 透過程式設計或 UI 兩種方式關閉市集應用程式不允許根據[Microsoft 市集原則](http://go.microsoft.com/fwlink/?LinkId=865936)。 如需詳細資訊，請參閱[UWP 應用程式生命週期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>語法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>參數

[in]_旗標_  
`abort` 旗標的新值。

[in]_遮罩_  
要設定之 `abort` 旗標位元的遮罩。

## <a name="return-value"></a>傳回值

旗標的舊值。

## <a name="remarks"></a>備註

有兩個 `abort` 旗標：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。 `_WRITE_ABORT_MSG` 決定是否要在程式異常終止時列印有用的文字訊息。 此訊息說明應用程式已呼叫 `abort` 函式。 預設行為是列印訊息。 `_CALL_REPORTFAULT` 若設定，可指定在呼叫 `abort` 時產生並回報 Watson 損毀傾印。 根據預設，會在非偵錯組建中啟用損毀傾印報告。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_set_abort_behavior`|\<stdlib.h>|

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

[abort](../../c-runtime-library/reference/abort.md)  
