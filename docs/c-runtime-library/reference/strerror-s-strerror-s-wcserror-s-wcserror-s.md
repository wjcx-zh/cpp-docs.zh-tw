---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 11/04/2016
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 00ff9d0df1a78d07eaa509201fb998b30396cc4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353816"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

取得系統錯誤訊息 (**strerror_s**， **_wcserror_s**) 或列印使用者提供的錯誤訊息 (**_strerror_s**， **__wcserror_s**). 這些是 [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
要保存錯誤字串的緩衝區。

*numberOfElements*<br/>
緩衝區的大小。

*errnum*<br/>
錯誤號碼。

*strErrMsg*<br/>
使用者提供的訊息。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

### <a name="error-condtions"></a>錯誤狀況

|*buffer*|*numberOfElements*|*strErrMsg*|內容*緩衝區*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|any|any|N/A|
|any|0|any|未修改|

## <a name="remarks"></a>備註

**Strerror_s**函式對應*errnum*為錯誤訊息字串，傳回的字串*緩衝區*。 **_strerror_s**不接受錯誤號碼; 它會使用目前的值**errno**來判斷適當的訊息。 既不**strerror_s**也不 **_strerror_s**實際上會列印訊息：為此，您需要這類呼叫的輸出函式[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*是**NULL**， **_strerror_s**傳回的字串*緩衝區*包含最後一次程式庫呼叫的系統錯誤訊息產生錯誤。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 如果*strErrMsg*不等於**NULL**，然後 **_strerror_s**傳回的字串*緩衝區*（依順序），其中包含您的字串訊息冒號、 空格、 最後一次產生錯誤，而新行字元的程式庫呼叫的系統錯誤訊息。 您的字串訊息最多可以是 94 個字元長度。

這些函式會截斷錯誤訊息，如果其長度超過*numberOfElements* -1。 在產生的字串*緩衝區*是一律以 null 終止。

實際的錯誤號碼 **_strerror_s**儲存在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 **_strerror_s**藉由使用會存取適當的錯誤訊息**errno**值為變數的索引 **_sys_errlist**。 變數的值[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中的項目數目上限指 **_sys_errlist**陣列。 若要產生精確的結果，呼叫 **_strerror_s**之後立即在程式庫常式傳回錯誤。 否則，後續呼叫**strerror_s**或是 **_strerror_s**可以覆寫**errno**值。

**_wcserror_s**並 **__wcserror_s**是寬字元版本**strerror_s**並 **_strerror_s**分別。

這些函式會驗證它們的參數。 如果緩衝區**NULL**或大小參數為 0，如果無效的參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會傳回**EINVAL**並設定**errno**來**EINVAL**。

**_strerror_s**， **_wcserror_s**，以及 **__wcserror_s**不屬於 ANSI 定義，而是 Microsoft 擴充功能。 請勿使用它們的可攜性想要的地方;基於 ANSI 相容性，使用**strerror_s**改。

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror_s**， **_strerror_s**|\<string.h>|
|**_wcserror_s**， **__wcserror_s**|\<string.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
