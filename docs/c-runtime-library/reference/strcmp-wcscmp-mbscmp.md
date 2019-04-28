---
title: strcmp、 wcscmp、 _mbscmp、 _mbscmp_l
ms.date: 01/22/2019
apiname:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: dae5e04809ac7312097cb418ab5ffd561fdbd1d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354219"
---
# <a name="strcmp-wcscmp-mbscmp-mbscmpl"></a>strcmp、 wcscmp、 _mbscmp、 _mbscmp_l

比較字串。

> [!IMPORTANT]
> **_mbscmp**並 **_mbscmp_l**不能在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*string1*， *string2*<br/>
以 Null 結束的待比較字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式的傳回值表示的序數關聯*string1*要*string2*。

|值|string1 與 string2 的關係|
|-----------|----------------------------------------|
|< 0|*string1*是小於*string2*|
|0|*string1*等同於*string2*|
|> 0|*string1*大於*string2*|

參數驗證錯誤時， **_mbscmp**並 **_mbscmp_l**傳回 **_NLSCMPERROR**，其定義於\<h > 和\<m >。

## <a name="remarks"></a>備註

**Strcmp**函式會執行序數比較*string1*並*string2*和傳回值，這個值指出其關聯性。 **wcscmp**並 **_mbscmp**分別是寬字元和多位元組字元版本**strcmp**。 **_mbscmp**辨識多位元組字元序列，根據目前的多位元組字碼頁，並傳回 **_NLSCMPERROR**在發生錯誤。 **_mbscmp_l**具有相同的行為，但會使用傳入的地區設定參數，而不是目前的地區設定。 如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。 此外，如果*string1*或是*string2*為 null 指標， **_mbscmp**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md). 如果允許繼續，請執行 **_mbscmp**並 **_mbscmp_l**傳回 **_NLSCMPERROR** ，並設定**errno**到**EINVAL**. **strcmp**並**wcscmp**不會驗證其參數。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp**函式與差異**strcoll**中的函式**strcmp**比較為序數，且不會受到地區設定。 **strcoll**使用，依辭典編纂順序比較字串**LC_COLLATE**目前地區設定的類別。 如需詳細資訊**LC_COLLATE**分類中，請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md)。

在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與詞典編纂的字元順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂順序不同。 例如，在某些歐洲的地區設定中，字元集中的字元 'a' (值 0x61) 會在字元 'ä' (值 0xE4) 之前，但以詞典編纂而言，字元 'ä' 是在字元 'a' 之前。

在地區設定中的字元集和詞典編纂字元順序不同，您可以使用**strcoll**而不是**strcmp**為字串的詞典編纂的比較。 或者，您可以使用**strxfrm**原始字串，然後再使用**strcmp**產生的字串。

**Strcmp**函式會區分大小寫。 **\_stricmp**，  **\_wcsicmp**，並 **\_mbsicmp**第一次將它們轉換成其小寫的形式來比較字串。 包含位於 'Z' 之間字元的兩個字串和 'a' ASCII 資料表中 ('['、'\\'，']'，' ^'、 '_' 和 '\`') 比較以不同的方式，根據其大小寫。 例如，兩個字串"ABCDE"和"ABCD ^"比較其中一個方法，如果該比較為小寫 ("abcde">"abcd ^") 以及的其他方式 ("ABCDE"<"ABCD ^") 如果比較為大寫。

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
