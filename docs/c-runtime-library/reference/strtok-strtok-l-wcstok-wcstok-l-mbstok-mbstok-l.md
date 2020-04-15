---
title: strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
ms.date: 4/2/2020
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
- _o__mbstok
- _o__mbstok_l
- _o_strtok
- _o_wcstok
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: d228d9824c534a21e4a22797e4b070e6d8d0b179
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365189"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l

使用目前的地區設定或傳入的指定地區設定，在字串中尋找下一個 Token。 這些函式已有更安全的版本可供使用，請參閱 [strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)。

> [!IMPORTANT]
> **_mbstok**和 **_mbstok_l**不能在 Windows 執行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*斯特權杖*<br/>
包含一或多個 Token 的字串。

*斯特德限制*<br/>
分隔符號字元集。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回指向 strToken 中找到的下一個權*杖 的指標*。 當找不到更多的權杖時,函數將傳回**NULL。** 每個調用都通過替換返回權杖後發生的第一個分隔符的 null 字元來修改*strToken。*

## <a name="remarks"></a>備註

**strtok**函數在*strToken*中尋找下一個令牌。 *strDelimit*中的字元集指定在當前調用的*strToken*中找到的權杖的可能分隔符。 **wcstok**與 **_mbstok**是寬字元和多位元組位元版本的**斯特托克**。 **wcstok**的參數和返回值是寬字元字串;**_mbstok**字串是多位元位元串。 除此之外，這三個函式的行為相同。

> [!IMPORTANT]
> 這些函式可能會帶來因緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

在第一個調用**strtok**時,函數跳過前導分隔元,並返回指向*strToken*中的第一個令牌的指標,用空字元終止權杖。 通過一系列對**strtok**的調用,可以在*strToken*的其餘部分中分解更多的權杖。 對**strtok**的每個調用通過在該調用返回的**令牌**後插入一個空字元來修改*strToken。* 要從*strToken*讀取下一個標記,請呼叫**strtok,** 該值為*strToken*參數具有**NULL**值。 **NULL** *strToken*參數導致**strtok**在修改後的*strToken*中搜索下一個權杖。 *strDelimit*參數可以從一個調用到下一個調用獲取任何值,以便分隔符集可能會有所不同。

輸出值受區域設置**LC_CTYPE**類別設置的影響。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。

沒有 **_l**後綴的這些函數的版本使用此與區域設置相關的行為的當前區域設置。 具有 **_l**後綴的版本是相同的,只是它們使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> 每個函式都會使用執行緒區域靜態變數將字串剖析為 Token。 因此，多個執行緒可以同時呼叫這些函式，卻不會有意外作用。 但在單一執行緒內，交錯呼叫這些函式的其中之一，非常有可能產生資料損毀或不正確的結果。 剖析不同的字串時，請先完成一個字串的剖析再開始剖析下一個。 亦請注意，從呼叫另一個函式的迴圈內呼叫這些函式的其中之一時，會有潛在的危險。 如果其他函式在使用這些函式的其中之一時結束，就會導致交錯的呼叫順序，觸發資料損毀。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> 或 \<wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
