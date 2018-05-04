---
title: _mbsnbcat_s、_mbsnbcat_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cead47b21a066d7e55c22d6bc8fba63cb73a0224
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s、_mbsnbcat_s_l

將附加至多位元組字元字串，最多第一個**n**另一個多位元組字元字串位元組。 這些是 [_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

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
大小*目的地*以位元組為單位的緩衝區。

*src*<br/>
以 null 終止的多位元組字元來源字串。

*count*<br/>
從位元組數目*src*要附加至*目的地*。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|**目的地**|*sizeInBytes*|*src*|傳回值|
|------------|-------------------|-----------|------------------|
|**NULL**|任何|任何|**EINVAL**|
|任何|<= 0|任何|**EINVAL**|
|任何|任何|**NULL**|**EINVAL**|

如果發生其中任何一種錯誤狀況，此函式會產生參數無效錯誤，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果處理此錯誤，則此函數會傳回**EINVAL**並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

**_Mbsnbcat_s**函式會將附加至*目的地*的最多第一個*計數*位元組*src*。如果位元組，前面中的 null 字元*目的地*是前導位元組，則會覆寫的初始位元組*src*。否則的初始位元組*src*結束的 null 字元會覆寫*目的地*。 如果中出現 null 位元組*src*之前*計數*會附加位元組， **_mbsnbcat_s**附加所有位元組*src*，最多 null字元。 如果*計數*大於的長度*src*，長度*src*用來取代*計數*。 此產生的字串便會由 null 字元所終止。 如果在重疊的字串之間執行複製，則行為是未定義的。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 這些函式版本是相同的不同之處在於，不是有 **_l**後置詞使用目前的地區設定而沒有 **_l**尾碼改為使用的地區設定參數的傳入。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以自動使用其較新且較安全的函式，藉此取代較舊且較不安全的函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s、_mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
