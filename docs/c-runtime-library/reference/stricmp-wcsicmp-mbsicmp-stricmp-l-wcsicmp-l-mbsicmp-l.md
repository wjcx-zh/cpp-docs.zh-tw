---
title: _stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 786c2bd2738bb82b3edac5c811ccfd3f9f8bc854
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920001"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l

執行字串的不區分大小寫比較。

> [!IMPORTANT]
> **_mbsicmp**和 **_mbsicmp_l**無法用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*、 *string2*<br/>
以 Null 結束的待比較字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回值表示*string1*到*string2*的關聯，如下所示。

|傳回值|描述|
|------------------|-----------------|
|< 0|*string1*小於*string2*|
|0|*string1*與*string2*相同|
|> 0|*string1*大於*string2*|

發生錯誤時， **_mbsicmp**會傳回 **_NLSCMPERROR**，其定義在\<string. h> 和\<g.> 中。

## <a name="remarks"></a>備註

**_Stricmp**函數序數會在將每個字元轉換成小寫之後，比較*string1*和*string2* ，並傳回表示其關聯性的值。 **_stricmp**不同于 **_stricoll** ， **_stricmp**的比較只會受到**LC_CTYPE**的影響，這會決定哪些字元是大寫和小寫。 **_Stricoll**函式會根據地區設定的**LC_CTYPE**和**LC_COLLATE**分類來比較字串，其中包括大小寫和定序順序。 如需**LC_COLLATE**類別目錄的詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)和[地區設定分類](../../c-runtime-library/locale-categories.md)。 這些沒有 **_l**尾碼的函式版本，會針對地區設定相關的行為使用目前的地區設定。 具有字尾的版本也一樣，只不過它們改用傳入的地區設定。 如果尚未設定地區設定，會使用 C 地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> **_stricmp**相當於 **_strcmpi**。 它們可以交換使用，但 **_stricmp**是慣用的標準。

**_Strcmpi**函式相當於 **_stricmp** ，而且僅為回溯相容性而提供。

因為 **_stricmp**會進行小寫比較，所以可能會導致非預期的行為。

為了說明 **_stricmp**的大小寫轉換會如何影響比較的結果，假設您有兩個字串為約翰，並 JOHN_HENRY。 字串 JOHN_HENRY 會被視為少於 JOHNSTON，因為 "_" 的 ASCII 值比小寫 S 更低。事實上，所有 ASCII 值在 96 和 91 之間的任何字元都會被視為小於任何字母。

如果使用[strcmp](strcmp-wcscmp-mbscmp.md)函式而不是 **_stricmp**，JOHN_HENRY 會大於約翰，

**_wcsicmp**和 **_mbsicmp**是 **_stricmp**的寬字元和多位元組字元版本。 **_Wcsicmp**的引數和傳回值是寬字元字串;**_mbsicmp**的是多位元組字元字串。 **_mbsicmp**會根據目前的多位元組字碼頁來辨識多位元組字元序列，並在發生錯誤時傳回 **_NLSCMPERROR** 。 如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。 除此之外，這三個函式的行為相同。

**_wcsicmp**和**wcscmp**的行為相同，不同之處在于**wcscmp**不會先將其引數轉換成小寫，再進行比較。 **_mbsicmp**和 **_mbscmp**的行為相同，不同之處在于 **_mbscmp**不會先將其引數轉換成小寫，再進行比較。

您必須呼叫[setlocale](setlocale-wsetlocale.md) ， **_Wcsicmp**才能使用拉丁的1個字元。 根據預設，C 地區設定會生效，因此，ä不會比較等於Ä。 在 **_wcsicmp**的呼叫之前，使用 C 地區設定以外的任何地區設定來呼叫**setlocale** 。 下列範例示範 **_wcsicmp**如何區分地區設定：

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

替代方法是呼叫[_create_locale、_wcreate_locale，](create-locale-wcreate-locale.md)並將傳回的地區設定物件當做參數傳遞至 **_wcsicmp_l**。

這些函式全都會驗證它們的參數。 如果*string1*或*string2*是 null 指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 **_NLSCMPERROR** ，並將**Errno**設定為**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_stricmp**， **_stricmp_l**|\<string.h>|
|**_wcsicmp**， **_wcsicmp_l**|\<string.h> 或 \<wchar.h>|
|**_mbsicmp**， **_mbsicmp_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_stricmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp、_memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
