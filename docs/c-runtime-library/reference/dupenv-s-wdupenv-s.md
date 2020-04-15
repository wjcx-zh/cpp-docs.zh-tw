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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348064"
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

*元素數*<br/>
*緩衝區*的大小 。

*瓦爾名稱*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

若成功，就是零；若失敗，則為錯誤碼。

這些函數驗證其參數;如果*緩衝區*或*varname*為**NULL,** 則無效參數處理程式將調用參數[驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

如果這些函數無法分配足夠的記憶體,它們會將*緩衝區*設定為**NULL,** 將*元素數*設定為 0,並傳回**ENOMEM**。

## <a name="remarks"></a>備註

**_dupenv_s**函數搜索*變數*的環境變數清單。 如果找到該變數 **,_dupenv_s**分配緩衝區並將變數的值複製到緩衝區中。 緩衝區的位址和長度以*緩衝區*和*元素數量*返回。 通過分配緩衝區本身 **,_dupenv_s**提供了一個更方便的getenv_s替代[,_wgetenv_s](getenv-s-wgetenv-s.md)。

> [!NOTE]
> 呼叫程式會負責呼叫 [free](free.md) 以釋放記憶體。

如果未找到變數,則*緩衝區*設置為**NULL,***數位元素*設置為 0,返回值為 0,因為這種情況不被視為錯誤條件。

如果您對緩衝區的大小不感興趣,則可以傳遞**NULL** *以表示元素數量*。

**_dupenv_s**在 Windows 作業系統中不區分大小寫。 **_dupenv_s**使用全域變數 **_environ**指向的環境的副本來訪問環境。 _wgetenv_sgetenv_s見備[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)言,討論 **_environ。**

*緩衝區*中的值是環境變數值的副本;修改它對環境沒有影響。 使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函式修改環境變數的值。

**_wdupenv_s**是 **_dupenv_s**的寬字元版本;**_wdupenv_s**的參數是寬字元字串。 **_wenviron**全域變數是 **_environ**的寬字元版本。 請參閱[getenv_s,_wgetenv_s](getenv-s-wgetenv-s.md)有關 **_wenviron**的更多。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
