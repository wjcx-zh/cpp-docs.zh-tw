---
title: _strinc、_wcsinc、_mbsinc、_mbsinc_l
ms.date: 4/2/2020
api_name:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
- _o__mbsinc
- _o__mbsinc_l
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
ms.openlocfilehash: a53102f991ec7467fd74e1997f8d5b7419b15aa1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919975"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc、_wcsinc、_mbsinc、_mbsinc_l

使字串指標前進一個字元。

> [!IMPORTANT]
> **_mbsinc**和 **_mbsinc_l**無法用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *_strinc(
   const char *current,
   _locale_t locale
);
wchar_t *_wcsinc(
   const wchar_t *current,
   _locale_t locale
);
unsigned char *_mbsinc(
   const unsigned char *current
);
unsigned char *_mbsinc_l(
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*目前*<br/>
字元指標。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

這些常式都會傳回緊接在*目前*後面之字元的指標。

## <a name="remarks"></a>備註

**_Mbsinc**函式會傳回緊接在*current*後面之多位元組字元的第一個位元組指標。 **_mbsinc**會根據目前使用中的[多位元組字碼頁](../../c-runtime-library/code-pages.md)，辨識多位元組字元序列。**_mbsinc_l**是相同的，不同之處在于它會改為使用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果已定義 **_MBCS** ，則 **_Tcsinc**定義于 Tchar 中的泛型文字函式會對應至 **_mbsinc** ，如果已定義 **_UNICODE**則為 **_wcsinc** 。 否則， **_tcsinc**對應至 **_strinc**。 **_strinc**和 **_wcsinc**是 **_mbsinc**的單一位元組字元和寬字元版本。 僅針對此對應提供 **_strinc**和 **_wcsinc** ，否則不應使用。 如需詳細資訊，請參閱[使用泛型文字對應](../../c-runtime-library/using-generic-text-mappings.md)以及[泛型文字對應](../../c-runtime-library/generic-text-mappings.md)。

如果*current*是**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

> [!IMPORTANT]
> 這些函式可能容易受到緩衝區滿溢的威脅。 緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h>|
|**_wcsinc**|\<tchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec、_wcsdec、_mbsdec、_mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc、_wcsninc、_mbsninc、_mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
