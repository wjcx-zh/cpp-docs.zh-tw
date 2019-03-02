---
title: strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
ms.date: 11/04/2016
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: 960d57ed8c2b1d1dbc6843932b8c76fef35c34a0
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210662"
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

使用目前的地區設定或是已傳入的地區設定取得字串的長度。 這些是較安全的 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 版本。

> [!IMPORTANT]
> **_mbsnlen**， **_mbsnlen_l**， **_mbstrnlen**，和 **_mbstrnlen_l**不能在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*str*<br/>
以 Null 結束的字串。

*numberOfElements*<br/>
字串緩衝區的大小。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

這些函式會傳回字串中的字元數，但不包含結束的 Null 字元。 如果在第一個沒有 null 結束字元*numberOfElements*個位元組的字串 (或寬字元**wcsnlen**)，然後*numberOfElements*會傳回到指出錯誤情況;null 終止的字串具有絕對的長度小於*numberOfElements*。

**_mbstrnlen**並 **_mbstrnlen_l**傳回-1，如果字串包含無效的多位元組字元。

## <a name="remarks"></a>備註

> [!NOTE]
> **strnlen**不是用來取代**strlen**;**strnlen**旨在只能用於計算已知大小的緩衝區不受信任的連入資料的大小，例如，網路封包。 **strnlen**計算長度，但不會經過緩衝區結尾的字串是否未結束。 針對其他情況下，使用**strlen**。 (同樣適用於**wcsnlen**， **_mbsnlen**，並 **_mbstrnlen**。)

所有這些函式傳回的字元數*str*，但不包含結束的 null 字元。 不過， **strnlen**並**strnlen_s**解譯為單一位元組字元字串的字串，因此，傳回的值會一律等於位元組數，即使字串包含多位元組字元。 **wcsnlen**並**wcsnlen_s**是寬字元版本**strnlen**並**strnlen_s**分別; 的引數**wcsnlen**並**wcsnlen_s**是寬字元字串和字元計數會以寬字元為單位。 否則為**wcsnlen**並**strnlen**行為相同，像是**strnlen_s**並**wcsnlen_s**。

**strnlen**， **wcsnlen**，以及 **_mbsnlen**不會驗證其參數。 如果*str*是**NULL**，就會發生存取違規。

**strnlen_s**並**wcsnlen_s**驗證其參數。 如果*str*是**NULL**，函式會傳回 0。

**_mbstrnlen**也會驗證其參數。 如果*str*是**NULL**，或如果*numberOfElements*大於**INT_MAX**， **_mbstrnlen**會產生無效參數例外狀況，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行 **_mbstrnlen**設定**errno**來**EINVAL**並傳回-1。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**並 **_mbstrnlen**傳回多位元組字元字串中的多位元組字元數。 **_mbsnlen**辨識多位元組字元序列，根據多位元組字碼頁，正在使用中] 或 [根據傳入的地區設定; 它不會測試多位元組字元的有效性。 **_mbstrnlen**測試多位元組字元的有效性，並辨識多位元組字元序列。 如果字串傳遞給 **_mbstrnlen**包含無效的多位元組字元， **errno**設定為**EILSEQ**。

輸出值的設定會影響**LC_CTYPE**地區設定分類設定; 請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 這些函式的版本完全相同，只不過沒有具有 **_l**後置詞使用目前的地區設定，此地區設定相關的行為和擁有的版本 **_l**後置詞改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strnlen**， **strnlen_s**|\<string.h>|
|**wcsnlen**， **wcsnlen_s**|\<string.h> 或 \<wchar.h>|
|**_mbsnlen**， **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**， **_mbstrnlen_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
