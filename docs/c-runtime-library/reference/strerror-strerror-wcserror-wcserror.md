---
title: strerror、_strerror、_wcserror、__wcserror
ms.date: 11/04/2016
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
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
ms.openlocfilehash: 0b4d70687bc2f428162d035c80d6bc8525a8fb9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958138"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror、_strerror、_wcserror、__wcserror

取得系統錯誤訊息字串（**strerror**、 **_wcserror**），或格式化使用者提供的錯誤訊息字串（ **_strerror**、 **__wcserror**）。 這些函式已有更安全的版本可用，請參閱 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

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

**Strerror**函數會將*errnum*對應至錯誤訊息字串，並傳回字串的指標。 **Strerror**或 **_strerror**都不會實際列印訊息：為此，您必須呼叫輸出函式，例如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果將*strErrMsg*傳遞為**Null**， **_strerror**會傳回字串的指標，其中包含產生錯誤之最後一個程式庫呼叫的系統錯誤訊息。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 如果*strErrMsg*不等於**Null**，則 **_strerror**會傳回字串的指標，其中包含（依序）您的字串訊息、冒號、空格、最後一次產生錯誤的程式庫呼叫的系統錯誤訊息，以及分行符號字母. 您的字串訊息最多可以是 94 個字元長度。

**_Strerror**的實際錯誤號碼會儲存在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 若要產生精確的結果，請在程式庫常式傳回但發生錯誤時立即呼叫 **_strerror** 。 否則，後續呼叫**strerror**或 **_strerror**可能會覆寫**errno**值。

**_wcserror**和 **__wcserror**分別是寬字元版本的**strerror**和 **_strerror**。

**_strerror**、 **_wcserror**和 **__wcserror**不是 ANSI 定義的一部分;它們是 Microsoft 擴充功能，我們建議您不要在需要可移植程式碼的地方使用它們。 針對 ANSI 相容性，請改用**strerror** 。

若要取得錯誤字串，建議使用**strerror**或 **_wcserror** ，而不是已被取代的宏[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和已被取代的內建函式 **__sys_errlist**和 **__sys_nerr**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**、 **__wcserror**|\<string.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
