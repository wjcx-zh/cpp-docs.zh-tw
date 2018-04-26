---
title: strstr、wcsstr、_mbsstr、_mbsstr_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
caps.latest.revision: 32
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a85bf579dd5146e9f18627d9335f2fae408a7bb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="strstr-wcsstr-mbsstr-mbsstrl"></a>strstr、wcsstr、_mbsstr、_mbsstr_l
傳回字串中第一次出現的搜尋字串指標。

> [!IMPORTANT]
> **_mbsstr**和 **_mbsstr_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*str*<br/>
以 Null 終止的待搜尋字串。

*strSearch*<br/>
以 Null 終止的待搜尋字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

讓指標回到第一個出現*strSearch*中*str*，或**NULL**如果*strSearch*不會顯示在*str*. 如果*strSearch*指向函式會傳回長度為零的字串*str*。

## <a name="remarks"></a>備註

**Strstr**函式會傳回第一個出現的指標*strSearch*中*str*。 搜尋不包含終止的 Null 字元。 **wcsstr**是寬字元版本的**strstr**和 **_mbsstr**是多位元組字元版本。 引數和傳回值**wcsstr**是寬字元字串; **_mbsstr**是多位元組字元字串。 **_mbsstr**會驗證其參數。 如果*str*或*strSearch*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行 **_mbsstr**設定**errno**至**EINVAL**並傳回 0。 **strstr**和**wcsstr**不會驗證它們的參數。 除此之外，這三個函式的行為相同。

> [!IMPORTANT]
> 這些函式可能帶來因緩衝區滿溢問題引發的威脅。 緩衝區滿溢問題可用來攻擊系統，因為它們允許執行任意程式碼，這會造成非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

在 C 中，這些函數會使用 * * const * * 的第一個引數的指標。 在 C++ 中，可使用兩個多載。 接受的指標的多載 * * const * * 將指標傳回至**const **; 版本採用一個指向非**const * * 將指標傳回至非**const **。巨集 **_CRT_CONST_CORRECT_OVERLOADS**如果兩個定義**const * * 和非-** const * * 這些函式的版本可供使用。如果您需要非**const * * 對於這兩個 c + + 多載中，行為會定義符號 **_CONST_RETURN**。

輸出值會受到地區設定分類設定**LC_CTYPE**; 如需詳細資訊，請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md)。 不需要這些函式的版本 **_l**後置詞使用針對此與地區設定相關行為使用目前地區設定; 具有 **_l**尾碼是一樣的只不過它們改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsstr**|**strstr**|**_mbsstr**|**wcsstr**|
|**n/a**|**n/a**|**_mbsstr_l**|**n/a**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strstr**|\<string.h>|
|**wcsstr**|\<string.h> 或 \<wchar.h>|
|**_mbsstr**， **_mbsstr_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::find](../../standard-library/basic-string-class.md#find)<br/>
