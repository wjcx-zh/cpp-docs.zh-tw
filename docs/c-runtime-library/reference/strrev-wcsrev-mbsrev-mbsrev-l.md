---
title: "_strrev、_wcsrev、_mbsrev、_mbsrev_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsrev"
  - "_mbsrev"
  - "_strrev"
  - "_mbsrev_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strrev"
  - "_ftcsrev"
  - "_tcsrev"
  - "mbsrev"
  - "mbsrev_l"
  - "_wcsrev_fstrrev"
  - "_mbsrev"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsrev 函式"
  - "_mbsrev 函式"
  - "_mbsrev_l 函式"
  - "_strrev 函式"
  - "_tcsrev 函式"
  - "_wcsrev 函式"
  - "字元 [C++], 反轉順序"
  - "字元 [C++], 切換"
  - "ftcsrev 函式"
  - "mbsrev 函式"
  - "mbsrev_l 函式"
  - "反轉字串中的字元"
  - "字串 [C++], 反向"
  - "strrev 函式"
  - "tcsrev 函式"
  - "wcsrev 函式"
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strrev、_wcsrev、_mbsrev、_mbsrev_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

反轉字串的字元。  
  
> [!IMPORTANT]
>  `_mbsrev` 與`_mbsrev_l`不能用於[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_strrev(  
   char *str   
);  
wchar_t *_wcsrev(  
   wchar_t *str   
);  
unsigned char *_mbsrev(  
   unsigned char *str   
);  
unsigned char *_mbsrev_l(  
   unsigned char *str,  
   _locale_t locale   
);  
```  
  
#### 參數  
 `str`  
 要反轉的以 Null 結束的字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回變更後字串的指標。  未保留表示錯誤的傳回值。  
  
## 備註  
 `_strrev` 函式會反轉 `string` 中的字元順序。  結束的 null 字元就地保留。  `_wcsrev` 和 `_mbsrev` 是 `_strrev` 的寬字元和多位元組字元版本。  `_wcsrev` 的引數和傳回值是寬字元字串，而 `_mbsrev` 的引數和傳回值則是多位元組字元字串。  對於 `_mbsrev`，在 `string` 不變更位元組在每個多位元組字元的順序。  這三個函式其餘部分的運作相同。  
  
 `_mbsrev` 會驗證其參數。  如果 `string1` 或 `string2` 為 null 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `_mbsrev` 會傳回 `NULL` 並設定 `errno` 為 `EINVAL`。  `_strrev` 和 `_wcsrev` 並不驗證它們的參數。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響。如需詳細資訊，請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些功能的版本是相同的，不同之處在於不具有的那些有 `_l` 後置字元者使用當前區域設置而那些有  `_l`後置字元者，則不是使用的傳入的區域設置參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
> [!IMPORTANT]
>  這些函式可能容易受到緩衝區滿溢的威脅。  緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsrev`|`_strrev`|`_mbsrev`|`_wcsrev`|  
|**N\/A**|**N\/A**|`_mbsrev_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strrev`|\<string.h\>|  
|`_wcsrev`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsrev`, `_mbsrev_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strrev.c  
// This program checks a string to see  
// whether it is a palindrome: that is, whether  
// it reads the same forward and backward.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* string = "Able was I ere I saw Elba";  
   int result;  
  
   // Reverse string and compare (ignore case):  
   result = _stricmp( string, _strrev( _strdup( string ) ) );  
   if( result == 0 )  
      printf( "The string \"%s\" is a palindrome\n", string );  
   else  
      printf( "The string \"%s\" is not a palindrome\n", string );  
}  
```  
  
  **The string "Able was I ere I saw Elba" is a palindrome**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)