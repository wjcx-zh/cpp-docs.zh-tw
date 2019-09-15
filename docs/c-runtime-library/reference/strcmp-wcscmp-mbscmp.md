---
title: strcmp、wcscmp、_mbscmp、_mbscmp_l
ms.date: 01/22/2019
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 4bef0c61122e93bd45bc0d1238030743f1196d9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957966"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp、wcscmp、_mbscmp、_mbscmp_l

比較字串。

> [!IMPORTANT]
> **_mbscmp**和 **_mbscmp_l**不能在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
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

每個函式的傳回值表示*string1*到*string2*的序數關聯性。

|值|string1 與 string2 的關係|
|-----------|----------------------------------------|
|< 0|*string1*小於*string2*|
|0|*string1*等同于*string2*|
|> 0|*string1*大於*string2*|

在參數驗證錯誤上， **_mbscmp**和 **_mbscmp_l**會傳回 **_NLSCMPERROR**，其定義于\<string. h > 和\<g. >。

## <a name="remarks"></a>備註

**Strcmp**函數會執行*string1*和*string2*的序數比較，並傳回指出其關聯性的值。 **wcscmp**和 **_mbscmp**分別是寬字元和多位元組字元版本的**strcmp**。 **_mbscmp**會根據目前的多位元組字碼頁來辨識多位元組字元序列，並在發生錯誤時傳回 **_NLSCMPERROR** 。 **_mbscmp_l**具有相同的行為，但會使用傳入的地區設定參數，而不是目前的地區設定。 如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。 此外，如果*string1*或*string2*是 null 指標， **_mbscmp**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **_mbscmp**和 **_Mbscmp_l**會傳回 **_NLSCMPERROR** ，並將**errno**設定為**EINVAL**。 **strcmp**和**wcscmp**不會驗證它們的參數。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp**函數與**strcoll**函數不同之處在于， **strcmp**比較是序數，而且不會受到地區設定的影響。 **strcoll**會使用目前地區設定的**LC_COLLATE**類別目錄來比較字串詞典編纂。 如需**LC_COLLATE**類別的詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md)。

在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與詞典編纂的字元順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂順序不同。 例如，在某些歐洲的地區設定中，字元集中的字元 'a' (值 0x61) 會在字元 'ä' (值 0xE4) 之前，但以詞典編纂而言，字元 'ä' 是在字元 'a' 之前。

在字元集和詞典編纂字元順序不同的地區設定中，您可以使用**strcoll**而不是**strcmp**來比較字串的詞典編纂。 或者，您可以在原始字串上使用**strxfrm** ，然後在產生的字串上使用**strcmp** 。

**Strcmp**函數會區分大小寫。 stricmp、 **wcsicmp和\_**  **mbsicmp會先將字串轉換成\_** 小寫形式，來比較它們。 **\_** 包含 ASCII 資料表中 ' Z ' 和 ' a ' 之間字元（' ['、'\\'、'] '、' ^ '、' _ ' 和 '\`'）的兩個字串，會根據其大小寫進行不同的比較。 例如，如果比較為大寫，則兩個字串 "ABCDE" 和 "ABCD ^" 比較一種方法（"ABCDE" > "abcd ^"），另一種方式則是（"ABCDE" < "ABCD ^"）。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> 或 \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_strcmp.c

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
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
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
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
