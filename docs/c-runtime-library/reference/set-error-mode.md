---
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: c1bb617e0f3792f2ac41d59df13d184423d56a9e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562034"
---
# <a name="_set_error_mode"></a>_set_error_mode

修改 **__error_mode** 來判斷非預設位置，其中 C 執行時間會針對可能結束程式的錯誤寫入錯誤訊息。

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

藉由設定 **__error_mode**的值來控制錯誤輸出接收。 例如，您可以將輸出導向至標準錯誤，或使用 **MessageBox** API。

*Mode_val*參數可以設定為下列其中一個值。

|值|描述|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|錯誤接收器取決於 **__app_type**。|
|**_OUT_TO_STDERR**|錯誤接收是標準錯誤。|
|**_OUT_TO_MSGBOX**|錯誤接收是訊息方塊。|
|**_REPORT_ERRMODE**|報告目前的 **__error_mode** 值。|

如果傳入非列出的值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **_set_error_mode** 會將 **Errno** 設定為 **EINVAL** ，並傳回-1。

搭配判斷提示使用時， **_set_error_mode**會在[對話方塊中顯示](assert-macro-assert-wassert.md)失敗的語句，並提供選項讓您選擇 [**略**過] 按鈕，讓您可以繼續執行程式。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
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

[assert 宏、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
