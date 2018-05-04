---
title: _set_error_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
dev_langs:
- C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 130e9fee13401c8b598a5d6eef7d1fab3ed80ae9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="seterrormode"></a>_set_error_mode

修改 **__error_mode**判斷 C 執行階段寫入可能結束程式發生錯誤的錯誤訊息的位置的非預設位置。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>參數

*mode_val*<br/>
錯誤訊息的目的地。

## <a name="return-value"></a>傳回值

如果發生錯誤，則會傳回舊設定或 -1。

## <a name="remarks"></a>備註

藉由設定的值會控制錯誤輸出接收 **__error_mode**。 例如，您可以將輸出導向至標準錯誤，或使用**MessageBox**應用程式開發介面。

*Mode_val*參數可以設定為下列值之一。

|參數|描述|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|錯誤接收由 **__app_type**。|
|**_OUT_TO_STDERR**|錯誤接收是標準錯誤。|
|**_OUT_TO_MSGBOX**|錯誤接收是訊息方塊。|
|**_REPORT_ERRMODE**|報告目前 **__error_mode**值。|

如果傳入非列出的值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若要繼續，允許執行 **_set_error_mode**設定**errno**至**EINVAL**並傳回-1。

當搭配使用[assert](assert-macro-assert-wassert.md)， **_set_error_mode**對話方塊方塊中，顯示失敗的陳述式，並且讓您選擇的選項**忽略**按鈕，讓您可以繼續執行程式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>範例

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>另請參閱

[assert 巨集、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
