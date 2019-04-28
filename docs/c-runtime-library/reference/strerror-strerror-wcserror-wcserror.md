---
title: strerror、_strerror、_wcserror、__wcserror
ms.date: 11/04/2016
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 4038fcc29c18e5d73024cbe5688c674e00d1409e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353855"
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror、_strerror、_wcserror、__wcserror

取得系統錯誤訊息字串 (**strerror**， **_wcserror**) 或完整格式的使用者提供的錯誤訊息字串 (**_strerror**， **__wcserror**). 這些函式已有更安全的版本可用，請參閱 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

## <a name="syntax"></a>語法

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>參數

*errnum*<br/>
錯誤號碼。

*strErrMsg*<br/>
使用者提供的訊息。

## <a name="return-value"></a>傳回值

所有這些函式會傳回錯誤訊息字串的指標。 後續呼叫可能會複寫此字串。

## <a name="remarks"></a>備註

**Strerror**函式對應*errnum*至錯誤訊息字串並傳回字串的指標。 既不**strerror**也不 **_strerror**實際上會列印訊息：為此，您必須呼叫的輸出函式，例如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果*strErrMsg*被當做**NULL**， **_strerror**字串，包含上次產生錯誤的程式庫呼叫的系統錯誤訊息中傳回的指標。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 如果*strErrMsg*不等於**NULL**，然後 **_strerror**讓指標回到包含 （依順序），您的字串訊息、 冒號、 空格、 系統錯誤字串會產生錯誤，而新行字元最後一次程式庫呼叫的訊息。 您的字串訊息最多可以是 94 個字元長度。

實際的錯誤號碼 **_strerror**儲存在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 若要產生精確的結果，呼叫 **_strerror**之後立即在程式庫常式傳回錯誤。 否則，後續呼叫**strerror**或是 **_strerror**可以覆寫**errno**值。

**_wcserror**並 **__wcserror**是寬字元版本**strerror**並 **_strerror**分別。

**_strerror**， **_wcserror**，以及 **__wcserror**不是 ANSI 定義的一部分; 它們是 Microsoft 擴充功能和我們建議您不要使用它們您想要的可攜式程式碼。 基於 ANSI 相容性，使用**strerror**改。

若要取得錯誤字串，我們建議**strerror**或是 **_wcserror**而不是已被取代的巨集[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)並[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和已被取代的內部函式 **__sys_errlist**並 **__sys_nerr**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**， **__wcserror**|\<string.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
