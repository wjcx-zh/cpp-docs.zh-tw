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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0cfbe857ec8bbcdec887d4594cee0bf2b66de380
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362901"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc、_wcsinc、_mbsinc、_mbsinc_l

使字串指標前進一個字元。

> [!IMPORTANT]
> **_mbsinc****和_mbsinc_l**不能在Windows運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個例程返回一個指向緊鄰*當前*的字元的指標。

## <a name="remarks"></a>備註

**_mbsinc**函數返回指向多位元位元元的第一個字節的指標,該位元組緊隨*當前*之後。 **_mbsinc**根據當前正在使用的[多位元節代碼頁](../../c-runtime-library/code-pages.md)識別多位元組位元序列;**_mbsinc_l**是相同的,只是它使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

_tcsinc在 Tchar.h 中定義的泛**文字函數將**映射到**已**定義 **_MBCS_mbsinc,** 或者如果定義了 **_UNICODE,** 則映射到 **_wcsinc。** 否則 **,_tcsinc**映射到 **_strinc**。 **_strinc**與 **_wcsinc**是單位元位元與寬字元版本的 **_mbsinc**。 **_strinc**和 **_wcsinc**僅為此映射提供,否則不應使用。 如需詳細資訊，請參閱[使用泛型文字對應](../../c-runtime-library/using-generic-text-mappings.md)以及[泛型文字對應](../../c-runtime-library/generic-text-mappings.md)。

如果*電流*為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,則此函數將傳回**EINVAL**並將**errno**設定到**EINVAL**。

> [!IMPORTANT]
> 這些函式可能容易受到緩衝區滿溢的威脅。 緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h>|
|**_wcsinc**|\<tchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec、_wcsdec、_mbsdec、_mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc、_wcsninc、_mbsninc、_mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
