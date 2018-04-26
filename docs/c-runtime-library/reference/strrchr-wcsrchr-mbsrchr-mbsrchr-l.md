---
title: strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da5f430108b78c7c62a4acd1e2347cc7b689c97e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr、wcsrchr、_mbsrchr、_mbsrchr_l

掃描字串尋找最後一個字元。

> [!IMPORTANT]
> **_mbsrchr**和 **_mbsrchr_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

傳回最後一個出現的指標*c*中*str*，或**NULL**如果*c*找不到。

## <a name="remarks"></a>備註

**Strrchr**函式會尋找，最後一個出現*c* (轉換成**char**) 中*str*。 搜尋包含終止的 Null 字元。

**wcsrchr**和 **_mbsrchr**是寬字元和多位元組字元版本的**strrchr**。 引數和傳回值**wcsrchr**是寬字元字串; **_mbsrchr**是多位元組字元字串。

在 C 中，這些函數會使用 * * const * * 的第一個引數的指標。 在 C++ 中，可使用兩個多載。 取得指標的多載 * * const * * 將指標傳回至**const **; 版本採用一個指向非**const * * 將指標傳回至非**const **。巨集 **_CRT_CONST_CORRECT_OVERLOADS**如果兩個定義**const * * 和非-** const * * 這些函式的版本可供使用。如果您需要非**const * * 對於這兩個 c + + 多載中，行為會定義符號 **_CONST_RETURN**。

**_mbsrchr**會驗證其參數。 如果*str*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**和 **_mbsrchr**傳回 0。 **strrchr**和**wcsrchr**不會驗證它們的參數。 除此之外，這三個函式的行為相同。

輸出值會影響的設定**LC_CTYPE**類別目錄設定地區設定; 如需詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrchr**|**strrchr**|**_mbsrchr**|**wcsrchr**|
|**n/a**|**n/a**|**_mbsrchr_l**|**n/a**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strrchr**|\<string.h>|
|**wcsrchr**|\<string.h> 或 \<wchar.h>|
|**_mbsrchr**， **_mbsrchr_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需使用**strrchr**，請參閱[strchr](strchr-wcschr-mbschr-mbschr-l.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
