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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 315a86c5cf7e58219bad25f2b6633dd91275c09f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320463"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l

執行字串的不區分大小寫比較。

> [!IMPORTANT]
> **_mbsicmp**和 **_mbsicmp_l**不能在 Windows 運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*字串1*,*字串2*<br/>
以 Null 結束的待比較字串。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

返回值指示*string1*到*string2*的關係,如下所示。

|傳回值|描述|
|------------------|-----------------|
|< 0|*字串1*小於*字串2*|
|0|*字串1*與*字串2*相同|
|> 0|*字串1*大於*字串2*|

在錯誤時 **,_mbsicmp**返回 **_NLSCMPERROR**,該返回\<在\<string.h> 和 mbstring.h>中定义。

## <a name="remarks"></a>備註

**_stricmp**函數在將每個字元轉換為小寫后,將*string1*和*string2*進行二級比較,並返回指示其關係的值。 **_stricmp**不同於 **_stricoll,****因為_stricmp**比較只受LC_CTYPE的影響,而**LC_CTYPE**決定了哪些字元是大寫字母和小寫字母。 **_stricoll**函數根據區域設置**LC_CTYPE**和**LC_COLLATE**類別比較字串,其中包括大小寫和排序規則。 關於**LC_COLLATE**類別的詳細資訊,請參考[設定區域設定](setlocale-wsetlocale.md)[與區域設定類別](../../c-runtime-library/locale-categories.md)。 沒有 **_l**後綴的這些函數的版本使用當前區域設置進行與區域設置相關的行為。 具有字尾的版本也一樣，只不過它們改用傳入的地區設定。 如果尚未設定地區設定，會使用 C 地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> **_stricmp**相當於 **_strcmpi。** 它們可以互換使用,但 **_stricmp**是首選標準。

**_strcmpi**函數等效於 **_stricmp,** 並且僅針對向後相容性提供。

由於 **_stricmp**進行小寫比較,因此可能會導致意外行為。

要說明**大小寫**轉換_stricmp何時影響比較結果,假定您具有兩個字串 JOHNSTON 和JOHN_HENRY。 字串 JOHN_HENRY 會被視為少於 JOHNSTON，因為 "_" 的 ASCII 值比小寫 S 更低。事實上，所有 ASCII 值在 96 和 91 之間的任何字元都會被視為小於任何字母。

如果使用[strcmp](strcmp-wcscmp-mbscmp.md)函數而不是 **_stricmp,JOHN_HENRY**將大於約翰斯頓。

**_wcsicmp**和 **_mbsicmp**是寬字元和多位元組字元版本的 **_stricmp。** **_wcsicmp**的參數和返回值是寬字元字串;**_mbsicmp**的字串是多位元位元串。 **_mbsicmp**根據當前多位元組代碼頁識別多位元組字序列,並在錯誤時返回 **_NLSCMPERROR。** 如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。 除此之外，這三個函式的行為相同。

**_wcsicmp**和**wcscmp**行為相同,只是**wcscmp**在比較它們之前不會將其參數轉換為小寫。 **_mbsicmp**和 **_mbscmp**行為相同,只是 **_mbscmp**在比較它們之前不會將其參數轉換為小寫。

您需要呼叫[setlocale](setlocale-wsetlocale.md) **_wcsicmp**才能使用拉丁字元 1 個字元。 預設情況下,C 區域設置有效,因此,例如,_ 不會與 +進行比較。 調用**集區域設置**,在調用 **_wcsicmp**之前,除了 C 區域設置外的任何區域設置。 以下範例展示 **_wcsicmp**對區域設定的敏感性:

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

另一種方法是呼叫[_create_locale,_wcreate_locale](create-locale-wcreate-locale.md)並將傳回的區域設定物件作為參數傳遞給 **_wcsicmp_l**。

這些函式全都會驗證它們的參數。 如果*string1*或*string2*都是空指標,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**傳回_NLSCMPERROR**並將**errno**設定為**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<string.h> 或 \<wchar.h>|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

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

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp、_memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
