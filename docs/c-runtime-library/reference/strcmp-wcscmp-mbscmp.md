---
title: "strcmp、wcscmp、_mbscmp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcscmp
- _mbscmp
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
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs: C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f133027b2f1e7dfef494baeed9df6e9e56447889
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp、wcscmp、_mbscmp
比較字串。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbscmp`。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
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
```  
  
#### <a name="parameters"></a>參數  
 `string1`, `string2`  
 以 Null 結束的待比較字串。  
  
## <a name="return-value"></a>傳回值  
 每一個這些函式的傳回值均表示 `string1` 與 `string2` 的序數關聯。  
  
|值|string1 與 string2 的關係|  
|-----------|----------------------------------------|  
|< 0|`string1` 小於 `string2`|  
|0|`string1` 等於 `string2`|  
|> 0|`string1` 大於 `string2`|  
  
 發生參數驗證錯誤時，`_mbscmp` 會傳回 `_NLSCMPERROR` (定義於 \<string.h> 和 \<mbstring.h> 中)。  
  
## <a name="remarks"></a>備註  
 `strcmp` 函式會執行 `string1` 和 `string2` 的序數比較，並傳回指出其關聯性的值。 `wcscmp` 和 `_mbscmp` 分別是 `strcmp` 的寬字元版本和多位元組字元版本。 `_mbscmp` 根據目前的多位元組字碼頁來辨識多位元組字元序列，並在發生錯誤時傳回 `_NLSCMPERROR`。 如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。 此外，如果 `string1` 或 `string2` 為 null 指標，`_mbscmp` 會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`_mbscmp` 會傳回 `_NLSCMPERROR`，且 `errno` 設為 `EINVAL`。 `strcmp` 和 `wcscmp` 不會驗證其參數。 除此之外，這三個函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 
          `strcmp` 函式與 `strcoll` 函式不同之處為，`strcmp` 的比較為序數，且不會受到地區設定影響。 `strcoll` 使用目前地區設定的 `LC_COLLATE` 分類，以詞典編纂順序比較字串。 如需 `LC_COLLATE` 分類的詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與詞典編纂的字元順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂順序不同。 例如，在某些歐洲的地區設定中，字元集中的字元 'a' (值 0x61) 會在字元 'ä' (值 0xE4) 之前，但以詞典編纂而言，字元 'ä' 是在字元 'a' 之前。  
  
 在字元集和詞典編纂字元順序不同的地區設定中，您可以針對字串的詞典編纂比較使用 `strcoll`，而不是 `strcmp`。 或者，您可以在原始字串使用 `strxfrm`，然後在產生的字串使用 `strcmp`。  
  
 `strcmp` 函式會區分大小寫。 `_stricmp`、`_wcsicmp` 和 `_mbsicmp` 會先將它們轉換成其小寫的形式來比較字串。 包含 ASCII 資料表中介於 'Z' 和 'a' 之間字元 ('['、'`\`'、']'、'`^`'、'`_`' 和 '```') 的兩個字串，會根據其大小寫以不同的方式進行比較。 例如，`"ABCDE"` 和 `"ABCD^"` 這兩個字串在進行小寫比較時的比較方式 (`"abcde"` > `"abcd^"`)，與進行大寫比較時的比較方式 (`"ABCDE"` < `"ABCD^"`) 不同。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strcmp`|<string.h>|  
|`wcscmp`|<string.h> 或 <wchar.h>|  
|`_mbscmp`|\<mbstring.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp、_memicmp_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)