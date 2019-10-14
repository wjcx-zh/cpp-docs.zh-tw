---
title: _mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l
ms.date: 11/04/2016
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 72c435060a6ac62213a50ba1d9fb9ef7d83fcb33
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952285"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l

使用多位元組字碼頁資訊，比較兩個多位元組字元字串的*n*個位元組。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*、 *string2*<br/>
要比較的字串。

*計數*<br/>
要比較的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回值表示*string1*和*string2*的子字串關聯性。

|傳回值|描述|
|------------------|-----------------|
|< 0|小於*string2*子字串的*string1*子字串。|
|0|*string1*子字串與*string2*子字串相同。|
|> 0|大於*string2*子字串的*string1*子字串。|

如果*string1*或*string2*是**Null** ，或*count*大於**INT_MAX**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 **_NLSCMPERROR** ，並將**Errno**設定為**EINVAL**。 若要使用 **_NLSCMPERROR**，請包含字串 .H 或 g。

## <a name="remarks"></a>備註

這些函式中的每一個最多格值定序都是*string1*和*string2*中的第一個*計數*位元組，並傳回值，指出*string1*和*string2*產生的子字串之間的關聯性。 如果*string1*或*string2*之子字串中的最後一個位元組是前導位元組，則不會包含在比較中。這些函數只會比較子字串中的完整字元。 **_mbsnbicoll**是不區分大小寫的 **_mbsnbcoll**版本。 如同[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)和[_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md)， **_mbsnbcoll**和 **_mbsnbicoll**會根據目前使用中的多位元組[字碼頁](../../c-runtime-library/code-pages.md)所指定的詞典編纂順序，將兩個多位元組字元字串自動分頁。

針對某些字碼頁和對應的字元集，字元集中的字元順序可能與詞典編纂的字元順序不同。 在 "C" 地區設定中則不然：ASCII 字元集中的字元順序會與詞典編纂的字元順序相同。 不過，某些歐洲字碼頁中的字元順序卻不同，例如，字元 'a' (值 0x61) 在字元集中排在字元 'ä' (值 0xE4) 之前，但在詞典編纂上，字元 'a' 卻排在字元 'ä' 之後。 若要在這類實例中依位元組執行字串的詞典編纂比較，請使用 **_mbsnbcoll**而非 **_mbsnbcmp**;若只要檢查字串是否相等，請使用 **_mbsnbcmp**。

因為**序 coll**函式會將字串詞典編纂為進行比較，而**cmp**函數只會測試字串是否相等，所以**序 coll**函數的速度會比對應的**cmp**版本慢很多。 因此，只有在字元集順序與目前字碼頁中的詞典編纂字元順序有所差異，且此差異與比較相關時，才應該使用**序 coll**函數。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
