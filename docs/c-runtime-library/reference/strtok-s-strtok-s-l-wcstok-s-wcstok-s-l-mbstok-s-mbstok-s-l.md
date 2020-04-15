---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 9fe89fb897a5459b16c49060359b4bb40bc062a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365226"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

使用目前的地區設定或傳入的地區設定，在字串中尋找下一個 Token。 這些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbstok_s**和 **_mbstok_s_l**不能在 Windows 運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*Str*<br/>
包含要查找的權杖或權杖的字串。

*分隔符*<br/>
要使用的分隔符集。

*內容*<br/>
用於在調用函數之間存儲位置資訊。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回指向 str 中找到的下一個權*杖 的指標*。 當找不到更多權杖時傳回**NULL。** 每個呼叫透過 null 字元替換在返回的權杖之後發生的第一個分隔符來修改*str。*

### <a name="error-conditions"></a>錯誤狀況

|*Str*|*分隔符*|*內容*|傳回值|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**空**|任意|Null 指標的指標|**空**|**埃因瓦爾**|
|任意|**空**|任意|**空**|**埃因瓦爾**|
|任意|任意|**空**|**空**|**埃因瓦爾**|

如果*str*為**NULL,** 但*上下文*是指向有效上下文指標的指標,則沒有錯誤。

## <a name="remarks"></a>備註

**函數的strtok_s**系列在*str*中找到下一個權杖。 *分隔符*中的字元集指定在當前呼叫的*str*中找到的權杖的可能分隔符。 **wcstok_s**和 **_mbstok_s**是**strtok_s**的寬字元和多位元組位元版本。 **wcstok_s**和 **_wcstok_s_l**的參數和返回值是寬字元字串;**_mbstok_s**和 **_mbstok_s_l**的字串是多位元位元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 當發生錯誤條件時(如錯誤條件表中)中,將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**NULL**。

在第一個調用**strtok_s**時,函數跳過前導分隔符,並返回指向*str*中的第一個令牌的指標,用空字元終止令牌。 通過一系列對**strtok_s**調用,可以在*str*的其餘部分中分解更多令牌。 對**strtok_s**的每個調用通過在該調用返回的權杖後插入一個空字元來修改*str。* *上下文*指標追蹤正在讀取的字串以及要讀取下一個權杖的位置。 要從*str*讀取下一個標記,請呼叫具有*str*參數的**NULL**值**strtok_s,** 並傳遞相同的*上下文*參數。 **NULL** *str*參數導致**strtok_s**在修改後的*str*中搜索下一個權杖。 *分隔符*參數可以從一個調用到下一個調用獲取任何值,以便分隔符集可能會有所不同。

由於*上下文*參數取代了**strtok**和 **_strtok_l**中使用的靜態緩衝區,因此可以在同一線程中同時解析兩個字串。

輸出值受區域設置**LC_CTYPE**類別設置的影響。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。

沒有 **_l**後綴的這些函數的版本使用此與區域設置相關的行為的當前線程區域設置。 具有 **_l**後綴的版本是相同的,只是它們使用*區域設置*參數指定的區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|\_未定義\_& MBCS 的 UNICODE|\_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>範例

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
