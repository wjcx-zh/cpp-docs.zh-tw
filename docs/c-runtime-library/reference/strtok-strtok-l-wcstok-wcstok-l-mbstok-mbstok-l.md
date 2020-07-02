---
title: strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
ms.date: 6/24/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: bf59d34c17165f9f5165a5a4bdb82ad5a82c737e
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737525"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l

使用目前的地區設定或傳入的指定地區設定，在字串中尋找下一個 Token。 這些函式已有更安全的版本可供使用，請參閱 [strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)。

> [!IMPORTANT]
> **_mbstok**和 **_mbstok_l**無法用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   wchar_t **context
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

*strToken*<br/>
包含一或多個 Token 的字串。

*strDelimit*<br/>
分隔符號字元集。

*locale*<br/>
要使用的地區設定。

*內容*<br/>
指向用來儲存剖析器內部狀態的記憶體，讓剖析器可以在下一次呼叫**wcstok**時，從停止的位置繼續。

## <a name="return-value"></a>傳回值

傳回在*strToken*中找到的下一個 token 的指標。 當找不到其他標記時，函數會傳回**Null** 。 每個呼叫都會藉由將 null 字元取代為傳回標記之後的第一個分隔符號來修改*strToken* 。

## <a name="remarks"></a>備註

**Strtok**函數會在*strToken*中尋找下一個 token。 *StrDelimit*中的一組字元會指定要在目前呼叫的*strToken*中找到的 token 可能分隔符號。 **wcstok**和 **_mbstok**是**strtok**的寬字元和多位元組字元版本。 **Wcstok**的引數和傳回值是寬字元字串;**_mbstok**的是多位元組字元字串。 除此之外，這三個函式的行為相同。

**Wcstok**的兩個引數版本不是標準。 如果您需要使用該版本，您必須在 `_CRT_NON_CONFORMING_WCSTOK` 之前定義 `#include <wchar.h>` （或 `#include <string.h>` ）。

> [!IMPORTANT]
> 這些函式可能會帶來因緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

在第一次呼叫**strtok**時，函式會略過前置分隔符號，並傳回*strToken*中第一個 token 的指標，並以 null 字元終止標記。 透過一系列對**strtok**的呼叫，可以將更多的 token 細分掉*strToken*的其餘部分。 **Strtok**的每個呼叫都會在該呼叫傳回的**權杖**之後插入一個 null 字元，藉此修改*strToken* 。 若要從*strToken*讀取下一個 token，請使用*strToken*引數的**Null**值呼叫**strtok** 。 **Null** *strToken*引數會導致**Strtok**在已修改的*strToken*中搜尋下一個 token。 *StrDelimit*引數可接受來自下一個呼叫的任何值，如此一來，分隔符號集合可能會有所不同。

輸出值會受到地區設定的 [ **LC_CTYPE** ] 分類設定所影響。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。

這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定。 具有 **_l**尾碼的版本相同，不同之處在于它們會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> 每個函式都會使用執行緒區域靜態變數將字串剖析為 Token。 因此，多個執行緒可以同時呼叫這些函式，卻不會有意外作用。 但在單一執行緒內，交錯呼叫這些函式的其中之一，非常有可能產生資料損毀或不正確的結果。 剖析不同的字串時，請先完成一個字串的剖析再開始剖析下一個。 亦請注意，從呼叫另一個函式的迴圈內呼叫這些函式的其中之一時，會有潛在的危險。 如果其他函式在使用這些函式的其中之一時結束，就會導致交錯的呼叫順序，觸發資料損毀。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
|**_wcstok_l**|<tchar.h>|
|**_mbstok**， **_mbstok_l**|\<mbstring.h>|

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

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[語言](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的轉譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
