---
title: _dupenv_s、_wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: 39184eff5db511dfb920782c3e29bf2b0cc9340e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915186"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s、_wdupenv_s

從目前的環境取得值。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
要儲存變數的值的緩衝區。

*numberOfElements*<br/>
*緩衝區*的大小。

*varname*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

若成功，就是零；若失敗，則為錯誤碼。

這些函式會驗證其參數;如果*buffer*或*varname*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

如果這些函式無法配置足夠的記憶體，則會將*buffer*設定為**Null**並*numberOfElements*為0，然後傳回**ENOMEM**。

## <a name="remarks"></a>備註

**_Dupenv_s**函式會在環境變數清單中搜尋*varname*。 如果找到變數， **_dupenv_s**會配置緩衝區，並將變數的值複製到緩衝區。 緩衝區的位址和長度會在*buffer*和*numberOfElements*中傳回。 藉由配置緩衝區本身， **_dupenv_s**提供更方便的替代方式來[getenv_s _wgetenv_s](getenv-s-wgetenv-s.md)。

> [!NOTE]
> 呼叫程式會負責呼叫 [free](free.md) 以釋放記憶體。

如果找不到變數，則*buffer*會設定為**Null**， *numberOfElements*會設為0，且傳回值為0，因為這種情況不會被視為錯誤狀況。

如果您對緩衝區的大小不感興趣，您可以針對*numberOfElements*傳遞**Null** 。

**_dupenv_s**在 Windows 作業系統中不區分大小寫。 **_dupenv_s**會使用全域變數所指向的環境複本， **_environ**來存取環境。 如需 **_environ**的討論，請參閱[Getenv_s 中的備註，_wgetenv_s](getenv-s-wgetenv-s.md) 。

*Buffer*中的值是環境變數值的複本。修改它對環境不會有任何影響。 使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函式修改環境變數的值。

**_wdupenv_s**是寬字元版本的 **_dupenv_s**;**_wdupenv_s**的引數是寬字元字串。 **_Wenviron**全域變數是寬字元版本的 **_environ**。 如需 **_wenviron**的詳細資訊[_wgetenv_s，](getenv-s-wgetenv-s.md)請參閱 getenv_s 中的備註。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg、_wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
