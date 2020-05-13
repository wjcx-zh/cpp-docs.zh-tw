---
title: strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: be13a67d51b0296d91355c970e5e37ad227812ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919258"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

使用目前的地區設定或是已傳入的地區設定取得字串的長度。 這些是較安全的 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 版本。

> [!IMPORTANT]
> **_mbsnlen**、 **_mbsnlen_l**、 **_mbstrnlen**和 **_mbstrnlen_l**無法用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

這些函式會傳回字串中的字元數，但不包含結束的 Null 字元。 如果字串的第一個*numberOfElements*位元組內沒有 null 結束字元（或**wcsnlen**的寬字元），則會傳回*numberOfElements*來指出錯誤狀況。以 null 終止的字串長度必須小於*numberOfElements*。

**_mbstrnlen**和 **_mbstrnlen_l**如果字串包含不正確多位元組字元，則會傳回-1。

## <a name="remarks"></a>備註

> [!NOTE]
> **strnlen**不是**strlen**的替代方案;**strnlen**只能用來計算已知大小緩衝區中傳入不受信任資料的大小（例如，網路封包）。 **strnlen**會計算長度，但如果字串未結束，則不會走到緩衝區結尾。 針對其他情況，請使用**strlen**。 （同樣適用于**wcsnlen**、 **_mbsnlen**和 **_mbstrnlen**）。

所有這些函式都會傳回*str*中的字元數，不包括終止的 null 字元。 不過， **strnlen**和**strnlen_s**會將字串解讀為單一位元組字元字串，因此，即使字串包含多位元組字元，傳回值一律等於位元組數目。 **wcsnlen**和**wcsnlen_s**分別是**strnlen**和**strnlen_s**的寬字元版本;**wcsnlen**和**wcsnlen_s**的引數是寬字元字串，且字元的計數是以寬字元為單位。 否則， **wcsnlen**和**strnlen**的行為完全相同， **strnlen_s**和**wcsnlen_s**。

**strnlen**、 **wcsnlen**和 **_mbsnlen**不會驗證其參數。 如果*str*為**Null**，就會發生存取違規。

**strnlen_s**和**wcsnlen_s**驗證其參數。 如果*str*為**Null**，則函數會傳回0。

**_mbstrnlen**也會驗證其參數。 如果*str*為**Null**，或如果*numberOfElements*大於**INT_MAX**， **_mbstrnlen**會產生不正確參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **_mbstrnlen**會將**Errno**設定為**EINVAL** ，並傳回-1。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**和 **_mbstrnlen**會傳回多位元組字元字串中的多位元組字元數。 **_mbsnlen**會根據目前使用中的多位元組字碼頁或根據傳入的地區設定來辨識多位元組字元序列;它不會測試多位元組字元的有效性。 **_mbstrnlen**測試多位元組字元的有效性，並辨識多位元組字元序列。 如果傳遞至 **_mbstrnlen**的字串包含不正確多位元組字元， **errno**會設定為**EILSEQ**。

輸出值會受到地區設定之**LC_CTYPE**分類設定的影響;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 這些函式的版本完全相同，不同之處在于，沒有 **_l**尾碼的函式會針對此地區設定相關的行為使用目前的地區設定，而具有 **_l**尾碼的版本則改為使用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

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
[語言](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
