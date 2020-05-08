---
title: _mbsnbcat、_mbsnbcat_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_l
- _mbsnbcat
- _o__mbsnbcat
- _o__mbsnbcat_l
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
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
ms.openlocfilehash: 25df567525fc190be94529fba3b7de131122e6b5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915662"
---
# <a name="_mbsnbcat-_mbsnbcat_l"></a>_mbsnbcat、_mbsnbcat_l

最多隻會將一個多位元組字元字串的前**n**個位元組附加到另一個。 這些函式已有更安全的版本可用，請參閱 [_mbsnbcat_s、_mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*dest*<br/>
以 null 終止的多位元組字元目的字串。

*src*<br/>
以 null 終止的多位元組字元來源字串。

*計數*<br/>
從*src*附加至*dest*的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsnbcat**會傳回目的地字串的指標。 未保留表示錯誤的傳回值。

## <a name="remarks"></a>備註

**_Mbsnbcat**函式最多會將*src*的第一個*計數*位元組附加至*目的地*。 如果在*dest*中的 null 字元之前的位元組是前導位元組，則*src*的初始位元組會覆寫這個前導位元組。 否則， *src*的初始位元組會覆寫*dest*的終止 null 字元。 如果在附加*計數*位元組之前， *src*中出現 null 位元組， **_mbsnbcat**會將所有位元組從*src*附加到 null 字元。 如果*count*大於*src*的長度，則會使用*src*的長度來取代*計數*。 此產生的字串會以 Null 字元結束。 如果在重疊的字串之間執行複製，則行為是未定義的。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 函式的 **_mbsnbcat**版本會針對此與地區設定相關的行為使用目前的地區設定;**_mbsnbcat_l**版本相同，不同之處在于它們會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**安全性提示**：使用以 Null 結束的字串。 以 Null 結束的字串不得超過目的緩衝區的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

如果*dest*或*src*是**Null**，此函式會產生不正確參數錯誤，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果處理錯誤，此函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbcat**|\<mbstring.h>|
|**_mbsnbcat_l**|\<mbstring.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s、_mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
