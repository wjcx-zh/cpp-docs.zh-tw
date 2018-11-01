---
title: _dupenv_s、_wdupenv_s
ms.date: 11/04/2016
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: bc8af3282b57c9fa411aac97f5fa4d414bc3305b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646489"
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s、_wdupenv_s

從目前的環境取得值。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*buffer*<br/>
要儲存變數的值的緩衝區。

*numberOfElements*<br/>
大小*緩衝區*。

*varname*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

若成功，就是零；若失敗，則為錯誤碼。

這些函式會驗證其參數;如果*緩衝區*或是*varname*是**NULL**，如中所述，會叫用無效參數處理常式[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

如果這些函式無法配置足夠的記憶體，它們將*緩衝區*要**NULL**並*numberOfElements*為 0，並傳回**ENOMEM**。

## <a name="remarks"></a>備註

**_Dupenv_s**函式會搜尋的環境變數清單*varname*。 如果找到變數，則 **_dupenv_s**會配置緩衝區，並將變數的值複製到緩衝區。 傳回緩衝區的位址和長度*緩衝區*並*numberOfElements*。 透過配置緩衝區本身 **_dupenv_s**提供更方便的替代方法，來[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)。

> [!NOTE]
> 呼叫程式會負責呼叫 [free](free.md) 以釋放記憶體。

如果找不到變數，然後*緩衝區*設為**NULL**， *numberOfElements*設為 0，並傳回值為 0，因為這種情況下不被視為錯誤條件。

如果您不感興趣的緩衝區大小可以傳遞**NULL** for *numberOfElements*。

**_dupenv_s**不區分大小寫在 Windows 作業系統中。 **_dupenv_s**會使用全域變數所指向的環境複製 **_environ**本來存取環境。 請參閱中的備註[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)的討論 **_environ**。

中的值*緩衝區*是一份該環境變數的值，修改已在環境上的沒有作用。 使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函式修改環境變數的值。

**_wdupenv_s**是寬字元版本的 **_dupenv_s**; 的引數 **_wdupenv_s**是寬字元字串。 **_Wenviron**全域變數是寬字元版本的 **_environ**。 請參閱中的備註[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)如需詳細資訊 **_wenviron**。

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

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg、_wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
