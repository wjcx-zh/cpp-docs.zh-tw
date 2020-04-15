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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364463"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

使用目前的地區設定或是已傳入的地區設定取得字串的長度。 這些是較安全的 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 版本。

> [!IMPORTANT]
> ** **_mbsnlen、_mbsnlen_l、_mbstrnlen和 **_mbstrnlen_l**不能在 Windows 運行時中執行的應用程式中使用。 **_mbsnlen_l** **_mbstrnlen** 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*Str*<br/>
以 Null 結束的字串。

*元素數*<br/>
字串緩衝區的大小。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

這些函式會傳回字串中的字元數，但不包含結束的 Null 字元。 如果字串的第一*個數量元素*位元組(**或 wcsnlen**的寬字元)中沒有空終止符,則返回*數量到元素*以指示錯誤條件;null 結束字串的長度的大小會變於*元素的數量*。

如果字串包含無效的多位元組字元,**則_mbstrnlen****和_mbstrnlen_l**返回 -1。

## <a name="remarks"></a>備註

> [!NOTE]
> **斯特倫**不是**斯特林**的替代品;**strnlen**僅用於計算已知大小的緩衝區(例如網路數據包)中傳入不受信任的數據的大小。 **strnlen**計算長度,但如果字串未終止,則不會遍歷緩衝區的末尾。 對於其他情況,請使用**strlen**。 (同樣適用於**wcsnlen、_mbsnlen**和 **_mbsnlen****_mbstrnlen**。

每個函數都返回*str*中的字元數,不包括終止空字元。 但是 **,strnlen**和**strnlen_s**將字串解釋為單位元位元串,因此,即使字串包含多位元元元,返回值始終等於位元數。 **wcsnlen**和**wcsnlen_s**分別是**斯特林**和**strnlen_s**的寬字元版本;**wcsnlen**和**wcsnlen_s**的參數是寬字元字串,字元計數以寬字元單位表示。 否則 **,wcsnlen**和**strnlen**行為相同 **,strnlen_s**和**wcsnlen_s。**

**斯特倫****、wcsnlen**和 **_mbsnlen**不驗證它們的參數。 如果*str*為**NULL,** 則發生訪問衝突。

**strnlen_s**和**wcsnlen_s**驗證其參數。 如果*str*為**NULL,** 則函數傳回 0。

**_mbstrnlen**也驗證其參數。 如果*str*為**NULL,** 或者元素*數*大於**INT_MAX,_mbstrnlen**將生成無效參數異常,**_mbstrnlen**如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,_mbstrnlen**將**errno**設置到**EINVAL**並返回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**和 **_mbstrnlen**返回多位元位元串中的多位元組位元數。 **_mbsnlen**根據當前正在使用的多位元節代碼頁或傳入區域設置識別多位元組位元序列;它不測試多位元組位字元的有效性。 **_mbstrnlen**多位元組位元元有效性測試,並識別多位元組位元序列。 如果傳送**到 _mbstrnlen**的字串包含無效的多位元位元,**則 errno**設定為**EILSEQ**。

輸出值受區域設置**LC_CTYPE**類別設置的影響;有關詳細資訊[,請參閱集本地設置_wsetlocale。](setlocale-wsetlocale.md) 這些函數的版本相同,只不過沒有 **_l**後綴的版本使用此區域設置來執行與區域設置相關的行為,並且具有 **_l**後綴的版本則使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**斯特倫**, **strnlen_s**|\<string.h>|
|**wcsnlen_s** **wcsnlen_s**|\<string.h> 或 \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

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

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
