---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337360"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

獲取系統錯誤消息 **(strerror_s,_wcserror_s)** 或列印使用者提供的錯誤消息 **(_strerror_s** **,__wcserror_s)。** **_wcserror_s** 這些是 [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

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

*緩衝區*<br/>
要保存錯誤字串的緩衝區。

*元素數*<br/>
緩衝區的大小。

*厄勒納姆*<br/>
錯誤號碼。

*斯特雷姆斯格*<br/>
使用者提供的訊息。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

### <a name="error-condtions"></a>錯誤狀況

|*緩衝區*|*元素數*|*斯特雷姆斯格*|*緩衝區*的內容|
|--------------|------------------------|-----------------|--------------------------|
|**空**|任意|任意|n/a|
|任意|0|任意|未修改|

## <a name="remarks"></a>備註

**strerror_s**函數將*errnum*映射到錯誤訊息字串,傳*回緩衝區*中的字串 。 **_strerror_s**不採用錯誤編號;因此,_strerror_s不會採用錯誤編號。它使用**errno**的當前值來確定適當的消息。 **strerror_s_strerror_s**實際上**都沒有**列印訊息:為此,您需要呼叫輸出函數,如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*為**NULL,_strerror_s**返回*緩衝區*中的字串,其中包含生成錯誤的最後一個庫調用的 **_strerror_s**系統錯誤訊息。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 如果*strErrMsg*不等於**NULL,** 則 **_strerror_s**傳回*緩衝區*中的字串,其中包含(順序)字串消息、冒號、空格、最後一個生成錯誤的庫調用的系統錯誤訊息以及換行符。 您的字串訊息最多可以是 94 個字元長度。

如果錯誤消息的長度超過*元素數*-1,則這些函數會截截錯誤消息。 *緩衝區*中生成的字串始終為空終止。

**_strerror_s**的實際誤差號存儲在變數[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 **_strerror_s**使用**errno**值作為變數 **_sys_errlist**的索引來存取相應的錯誤消息。 變數[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的值定義為 **_sys_errlist**數位中元素的最大數量。 要生成準確的結果,請立即在庫例程返回錯誤后調用 **_strerror_s。** 否則,對**strerror_s**或 **_strerror_s**的後續調用可能會覆蓋**errno**值。

**_wcserror_s**和 **__wcserror_s**分別是**strerror_s**和 **_strerror_s**的寬字元版本。

這些函式會驗證它們的參數。 如果緩衝區為**NULL**或大小參數為 0,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回**EINVAL**並將**errno**設定為**EINVAL**。

**_strerror_s、_wcserror_s**和 **__wcserror_s**不是 ANSI 定義的一部分,而是 **_wcserror_s**微軟對它擴展。 請勿在需要便攜性的地方使用它們;對於 ANSI 相容性,請使用**strerror_s。**

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s**, **__wcserror_s**|\<string.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [perror](perror-wperror.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
