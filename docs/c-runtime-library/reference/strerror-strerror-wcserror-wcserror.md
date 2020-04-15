---
title: strerror、_strerror、_wcserror、__wcserror
description: 描述 Microsoft C 執行時庫 (CRT) 功能,_strerror、_wcserror和__wcserror。
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337322"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror、_strerror、_wcserror、__wcserror

取得系統錯誤訊息字串 **(strerror、_wcserror)** 或設定使用者提供的錯誤訊息字串 **(_strerror,__wcserror)****__wcserror**的 **_wcserror**格式 。 這些函式已有更安全的版本可用，請參閱 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

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

*厄勒納姆*\
錯誤號碼。

*斯特雷姆斯格*\
使用者提供的訊息。

## <a name="return-value"></a>傳回值

所有這些函數都返回指向錯誤消息字串的指標,該指標位於運行時擁有的線程本地存儲緩衝區中。 以後對同一線程的調用可以覆蓋此字串。

## <a name="remarks"></a>備註

**strerror**函數將*errnum*映射到錯誤消息字串,並返回指向該字串的指標。 **strerror**和 **_strerror**函數實際上不會列印消息。 要列印,請呼叫輸出函數,如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果*strErrMsg*作為**NULL**傳遞 **,_strerror**傳回指向字串的指標。 它包含生成錯誤的最後一個庫調用的系統錯誤消息。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 當*strErrMsg*不是**NULL**時,字串按順序包含 *:strErrMsg*字串、冒號、空格、系統錯誤訊息和一個 newline 字元。 您的字串消息最多可以是 94 個字元,以窄 (**_strerror**) 或寬 (**__wcserror**) 字元。

**_strerror**的實際錯誤編號存儲在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 要生成準確的結果,請立即在庫例程返回錯誤后調用 **_strerror。** 否則,以後對庫例程的調用可能會覆蓋**errno**值。

**_wcserror**和 **__wcserror**分別是大字元版本的**strerror**和 **_strerror。**

**_strerror、_wcserror**和 **__wcserror**是特定於 Microsoft 的,而不是標準 **_wcserror**C 庫的一部分。 我們不建議您在需要便攜式代碼的地方使用它們。 對於標準 C 相容性,請使用**strerror。**

要取得錯誤字串,我們建議 **_wcserror****而不是棄**用的巨集[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)與[_sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)棄用的內部函數 **__sys_errlist**和 **__sys_nerr**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>通用文字例程對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)\
[更清晰](clearerr.md)\
[費雷爾](ferror.md)\
[perror、_wperror](perror-wperror.md)
