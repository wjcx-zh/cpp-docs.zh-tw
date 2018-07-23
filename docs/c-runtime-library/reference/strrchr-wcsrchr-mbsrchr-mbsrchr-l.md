---
title: strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
dev_langs:
- C++
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03b0ce2c9bd205f9065c783a4ff4d7e50d0ff803
ms.sourcegitcommit: 04d327940787df1297b72d534f388a035d472af0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39181155"
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr、wcsrchr、_mbsrchr、_mbsrchr_l

掃描字串尋找最後一個字元。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中無法使用 `_mbsrchr` 和 `_mbsrchr_l`。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*str*<br/>
以 Null 終止的待搜尋字串。

*C*<br/>
待找出的字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

讓指標回到最後一次出現*c*中*str*，則為 NULL 如果*c*找不到。

## <a name="remarks"></a>備註

`strrchr`函式會尋找最後一個出現*c* (轉換成**char**) 中*str*。 搜尋包含終止的 Null 字元。

`wcsrchr` 和 `_mbsrchr` 是寬字元和多位元組字元版本的 `strrchr`。 `wcsrchr` 的引數和傳回值是寬字元字串；`_mbsrchr` 的引數則是多位元組字元字串。

在 C 中，這些函式接受**const**第一個引數的指標。 在 C++ 中，可使用兩個多載。 取得指標的多載**const**傳回的指標**const**; 版本，採用的指標，非**const**將指標傳回至非**const**. 如果兩個使用者定義巨集 _CRT_CONST_CORRECT_OVERLOADS **const**和非位**const**這些函式的版本可供使用。 如果您需要非**const**兩個 c + + 多載，行為定義符號 _CONST_RETURN。

`_mbsrchr` 會驗證其參數。 如果*str*是 NULL 時，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行`errno`設為 EINVAL 和`_mbsrchr`會傳回 0。 `strrchr` 和 `wcsrchr` 不會驗證其參數。 除此之外，這三個函式的行為相同。

輸出值會受到地區設定; LC_CTYPE 分類設定的設定如需詳細資訊，請參閱 < [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**n/a**|**不適用**|`_mbsrchr_l`|**n/a**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> 或 \<wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需使用 `strrchr` 的範例，請參閱 [strchr](strchr-wcschr-mbschr-mbschr-l.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
