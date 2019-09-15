---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
ms.date: 03/25/2019
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
ms.openlocfilehash: 1bbc5910e6242a0df262cc43b58815ea80ff9681
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946450"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

使用目前的地區設定或傳入的地區設定，在字串中尋找下一個 Token。 這些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbstok_s**和 **_mbstok_s_l**不能在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*str*<br/>
字串，包含要尋找的 token 或標記。

*限定詞*<br/>
要使用的分隔符號組。

*context*<br/>
用來儲存對函式的呼叫之間的位置資訊。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回在*str*中找到的下一個 token 的指標。 當找不到其他標記時，會傳回**Null** 。 每個呼叫都會以 null 字元取代傳回標記之後發生的第一個分隔符號來修改*str* 。

### <a name="error-conditions"></a>錯誤狀況

|*str*|*限定詞*|*context*|傳回值|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|any|Null 指標的指標|**NULL**|**EINVAL**|
|any|**NULL**|any|**NULL**|**EINVAL**|
|any|any|**NULL**|**NULL**|**EINVAL**|

如果*str*為**Null** ，但*內容*是指向有效內容指標的指標，則不會發生錯誤。

## <a name="remarks"></a>備註

**Strtok_s**系列的函數會尋找*str*中的下一個 token。 *分隔符號*中的一組字元會指定要在目前呼叫上的*str*中找到的 token 可能分隔符號。 **wcstok_s**和 **_mbstok_s**是**strtok_s**的寬字元和多位元組字元版本。 **Wcstok_s**和 **_wcstok_s_l**的引數和傳回值是寬字元字串; **_mbstok_s**和 **_mbstok_s_l**的是多位元組字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 發生錯誤狀況時，如錯誤狀況資料表所示，會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回**Null**。

在第一次呼叫**strtok_s**時，函式會略過前置分隔符號，並將指標傳回至*str*中的第一個 token，並以 null 字元終止 token。 對於**strtok_s**的一系列呼叫，可以將更多的 token 細分成*str*的其餘部分。 **Strtok_s**的每個呼叫都會在該呼叫傳回的權杖之後插入一個 null 字元，藉此修改*str* 。 *內容*指標會持續追蹤正在讀取的字串，以及在字串中要讀取的下一個 token。 若要讀取*str*中的下一個 token，請以*str*引數的**Null**值呼叫**strtok_s** ，並傳遞相同的*內容*參數。 **Null** *str*引數會讓**strtok_s**搜尋已修改的*str*中的下一個 token。 *分隔符號*引數可接受來自下一個呼叫的任何值，如此一來，分隔符號集合可能會有所不同。

由於*內容*參數會取代**strtok**和 **_strtok_l**中使用的靜態緩衝區，因此可以在同一個執行緒中同時剖析兩個字串。

輸出值會受到地區設定的**LC_CTYPE**分類設定影響。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。

這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前的執行緒地區設定。 具有 **_l**後置字元的版本相同，不同之處在于它們會改用*locale*參數所指定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**，<br />**_wcstok_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbstok_s**，<br />**_mbstok_s_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|\_未定義\_UNICODE & MBCS|\_定義的 MBCS|_UNICODE 已定義|
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

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
