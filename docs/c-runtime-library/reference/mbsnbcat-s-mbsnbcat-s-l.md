---
title: _mbsnbcat_s、_mbsnbcat_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: d731c94c879d0e4334dc3b57a19b94cc0378abaf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915637"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s、_mbsnbcat_s_l

附加至多位元組字元字串，其中最多可有另一個多位元組字元字串的前**n**個位元組。 這些是 [_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*dest*<br/>
以 null 終止的多位元組字元目的字串。

*sizeInBytes*<br/>
*目的地*緩衝區的大小（以位元組為單位）。

*src*<br/>
以 null 終止的多位元組字元來源字串。

*計數*<br/>
從*src*附加至*dest*的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|**Dest**|*sizeInBytes*|*src*|傳回值|
|------------|-------------------|-----------|------------------|
|**Null**|任意|任意|**EINVAL**|
|任意|<= 0|任意|**EINVAL**|
|任意|任意|**Null**|**EINVAL**|

如果發生其中任何一種錯誤狀況，此函式會產生參數無效錯誤，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果處理錯誤，此函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Mbsnbcat_s**函式會附加至*目的地*，而最多隻會將*src*的第一個*計數*位元組附加到其中。 如果在*dest*中緊接在 null 字元之前的位元組是前導位元組，則會被*src*的初始位元組覆寫。 否則， *src*的初始位元組會覆寫*dest*的終止 null 字元。 如果在附加*計數*位元組之前， *src*中出現 null 位元組， **_mbsnbcat_s**會將所有位元組從*src*附加到 null 字元。 如果*count*大於*src*的長度，則會使用*src*的長度來取代*計數*。 此產生的字串便會由 null 字元所終止。 如果在重疊的字串之間執行複製，則行為是未定義的。

輸出值會受到地區設定之**LC_CTYPE**分類設定的影響;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 這些函式的版本完全相同，不同之處在于沒有 **_l**尾碼的函式會使用目前的地區設定，而具有 **_l**尾碼的函式則改為使用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以自動使用其較新且較安全的函式，藉此取代較舊且較不安全的函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函式的 debug 程式庫版本會先以0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s、_mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
