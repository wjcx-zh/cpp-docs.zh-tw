---
title: strerror、_strerror、_wcserror、__wcserror
description: 描述 Microsoft C 執行時間程式庫（CRT）函數 strerror、_strerror、_wcserror 和 __wcserror。
ms.date: 01/07/2020
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
ms.openlocfilehash: 8c9c6850d6620407897b2a3a1dbf32e61f6719c0
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755035"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror、_strerror、_wcserror、__wcserror

取得系統錯誤訊息字串（**strerror**， **_wcserror**），或格式化使用者提供的錯誤訊息字串（ **_strerror**， **__wcserror**）。 這些函式已有更安全的版本可用，請參閱 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

## <a name="syntax"></a>語法

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>參數

*errnum*\
錯誤號碼。

*strErrMsg*\
使用者提供的訊息。

## <a name="return-value"></a>傳回值

所有這些函式都會在執行時間所擁有的執行緒區域儲存緩衝區中，傳回錯誤訊息字串的指標。 之後在相同執行緒上的呼叫可能會覆寫這個字串。

## <a name="remarks"></a>備註

**Strerror**函數會將*errnum*對應至錯誤訊息字串，並傳回字串的指標。 **Strerror**和 **_strerror**函數實際上不會列印訊息。 若要列印，請呼叫輸出函數，例如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果將*strErrMsg*傳遞為**Null**， **_strerror**會傳回字串的指標。 它包含產生錯誤之最後一個程式庫呼叫的系統錯誤訊息。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 當*strErrMsg*不是**Null**時，字串會依序包含： *strErrMsg*字串、冒號、空格、系統錯誤訊息和分行符號。 您的字串訊息最多可以是94個字元，長度為窄（ **_strerror**）或寬（ **__wcserror**）字元。

**_Strerror**的實際錯誤號碼會儲存在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 若要產生精確的結果，請在程式庫常式傳回錯誤之後立即呼叫 **_strerror** 。 否則，稍後呼叫程式庫常式可能會覆寫**errno**值。

**_wcserror**和 **__wcserror**分別是寬字元版本的**strerror**和 **_strerror**。

**_strerror**、 **_wcserror**和 **__wcserror**是 Microsoft 特有的，而不是標準 C 程式庫的一部分。 我們不建議您在想要可攜的程式碼的地方使用它們。 針對標準 C 相容性，請改用**strerror** 。

若要取得錯誤字串，建議使用**strerror**或 **_wcserror** ，而不是已被取代的宏[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)以及已被取代的內建函式 **__sys_errlist**和 **__sys_nerr**。

### <a name="generic-text-routine-mappings"></a>泛型文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**， **__wcserror**|\<string.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)\
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror、_wperror](perror-wperror.md)
