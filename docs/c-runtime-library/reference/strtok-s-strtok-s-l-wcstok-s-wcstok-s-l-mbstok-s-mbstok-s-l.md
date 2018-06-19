---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
apitype: DLLExport
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 467184acd7ef78ee52f1605d23f2d3b80e6adb83
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451962"
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

使用目前的地區設定或傳入的地區設定，在字串中尋找下一個 Token。 這些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbstok_s**和 **_mbstok_s_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*str*<br/>
包含的語彙基元或語彙基元，若要尋找的字串。

*分隔符號*<br/>
若要使用的分隔符號字元組。

*context*<br/>
用來儲存呼叫函式之間的位置資訊。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回下一步中找到的語彙基元的指標*str*。 傳回**NULL**找到沒有 token 時。 每個呼叫會修改*str*所得到的 null 字元的第一個傳回的語彙基元後，就會發生的分隔符號。

### <a name="error-conditions"></a>錯誤狀況

|*str*|*分隔符號*|*context*|傳回值|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|任何|Null 指標的指標|**NULL**|**EINVAL**|
|任何|**NULL**|任何|**NULL**|**EINVAL**|
|任何|任何|**NULL**|**NULL**|**EINVAL**|

如果*str*是**NULL**但*內容*是指標，以有效的內容指標，沒有任何錯誤。

## <a name="remarks"></a>備註

**Strtok_s**系列的函式會尋找下一個語彙基元*str*。 中的字元組*分隔符號*指定可能要在中找到的語彙基元的分隔符號*str*上目前的呼叫。 **wcstok_s**和 **_mbstok_s**是寬字元和多位元組字元版本的**strtok_s**。 引數和傳回值**wcstok_s**和 **_wcstok_s_l**是寬字元字串; **_mbstok_s**和 **_mbstok_s_l**是多位元組字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果發生錯誤條件表中的錯誤，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回**NULL**。

在第一個呼叫**strtok_s**函式會略過前置分隔符號，並傳回在第一個語彙基元的指標*str*，終止具有 null 字元的語彙基元。 多個權杖可以中斷的其餘部分超出*str*一連串的呼叫**strtok_s**。 每次呼叫**strtok_s**修改*str*該呼叫所傳回的語彙基元後插入 null 字元。 *內容*正在讀取的字串，其中字串中的下一個語彙基元是要讀取追蹤的指標。 若要讀取下一個語彙基元，從*str*，呼叫**strtok_s**與**NULL**值*str*引數，並傳遞相同*內容*參數。 **NULL** *str*引數會**strtok_s**搜尋下一個語彙基元，在修改後*str*。 *分隔符號*引數可以讀取到下一個呼叫的任何值，如此分隔符號集可能會不同。

因為*內容*參數會取代中使用的靜態緩衝區**strtok**和 **_strtok_l**，便可剖析同時在同一執行緒中的兩個字串。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些功能，但不包含新版 **_l**尾碼針對此與地區設定相關行為使用目前的執行緒地區設定。 與版本 **_l**尾碼是一樣的只不過它們改用*地區設定*參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**，<br />**_wcstok_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbstok_s**，<br />**_mbstok_s_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|\_UNICODE （& s) \_MBCS 未定義|\_定義 MBCS|_UNICODE 已定義|
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
