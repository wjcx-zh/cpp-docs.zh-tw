---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 06/09/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 91be8803a0695670e7afe673b25b54fccde40a9c
ms.sourcegitcommit: 8167c67d76de58a7c2df3b4dcbf3d53e3b151b77
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84664322"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

取得系統錯誤訊息（**strerror_s**、 **_wcserror_s**），或列印使用者提供的錯誤訊息（**_strerror_s**、 **__wcserror_s**）。 這些是 [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t strerror_s(
   char *buffer,
   size_t sizeInBytes,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t sizeInBytes,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
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

*緩衝區*<br/>
要保存錯誤字串的緩衝區。

*sizeInBytes*<br/>
緩衝區中的位元組數目。

*sizeInWords*<br/>
緩衝區中的單字數目。

*errnum*<br/>
錯誤號碼。

*strErrMsg*<br/>
使用者提供的訊息。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

### <a name="error-condtions"></a>錯誤狀況

|*緩衝區*|*sizeInBytes/sizeInWords*|*strErrMsg*|*緩衝區*的內容|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|任意|任意|n/a|
|任意|0|任意|未修改|

## <a name="remarks"></a>備註

**Strerror_s**函式會將*errnum*對應至錯誤訊息字串，並傳回*buffer*中的字串。 **_strerror_s**不會採用錯誤號碼;它會使用**errno**的目前值來判斷適當的訊息。 **Strerror_s**或 **_strerror_s**實際上都不會列印訊息：為此，您必須呼叫輸出函數，例如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*為**Null**， **_strerror_s**會在*buffer*中傳回一個字串，其中包含產生錯誤之最後一個程式庫呼叫的系統錯誤訊息。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 如果*strErrMsg*不等於**Null**，則 **_strerror_s**會傳回*緩衝區*中的字串，其中包含（依序）您的字串訊息、冒號、空格、最後一個程式庫呼叫產生錯誤的系統錯誤訊息，以及一個分行符號。 您的字串訊息最多可以是 94 個字元長度。

如果錯誤訊息的長度超過緩衝區的大小-1，這些函式就會截斷它。 *緩衝區*中產生的字串一律會以 null 結束。

**_Strerror_s**的實際錯誤號碼會儲存在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 **_strerror_s**使用**errno**值做為變數 **_sys_errlist**的索引，來存取適當的錯誤訊息。 變數[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的值會定義為 **_sys_errlist**陣列中元素的最大數目。 若要產生精確的結果，請在程式庫常式傳回時立即呼叫 **_strerror_s**並傳回錯誤。 否則， **strerror_s**或 **_strerror_s**的後續呼叫可能會覆寫**errno**值。

**_wcserror_s**和 **__wcserror_s**分別是**strerror_s**和 **_strerror_s**的寬字元版本。

這些函式會驗證它們的參數。 如果 buffer 為**Null** ，或 size 參數為0，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

**_strerror_s**、 **_wcserror_s**和 **__wcserror_s**不是 ANSI 定義的一部分，而是 Microsoft 的延伸模組。 請勿在需要可攜性的情況下使用它們;若為 ANSI 相容性，請改用**strerror_s** 。

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函式的 debug 程式庫版本會先以0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
