---
title: "_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcnt_l"
  - "_mbsnccnt"
  - "_wcsncnt"
  - "_strncnt"
  - "_mbsnccnt_l"
  - "_mbsnbcnt"
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
apitype: "DLLExport"
f1_keywords: 
  - "_mbsnbcnt"
  - "wcsncnt"
  - "_tcsnbcnt"
  - "_mbsnccnt"
  - "_ftcsnbcnt"
  - "mbsnbcnt"
  - "strncnt"
  - "mbsnbcnt_l"
  - "mbsnccnt_l"
  - "mbsnccnt"
  - "_strncnt"
  - "_wcsncnt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcnt 函式"
  - "_mbsnbcnt_l 函式"
  - "_mbsnccnt 函式"
  - "_mbsnccnt_l 函式"
  - "_strncnt 函式"
  - "_tcsnbcnt 函式"
  - "_wcsncnt 函式"
  - "mbsnbcnt 函式"
  - "mbsnbcnt_l 函式"
  - "mbsnccnt 函式"
  - "mbsnccnt_l 函式"
  - "strncnt 函式"
  - "tcsnbcnt 函式"
  - "wcsncnt 函式"
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回字元或位元組數目在指定的計數中。  
  
> [!IMPORTANT]
>  `_mbsnbcnt`、`_mbsnbcnt_l`、`_mbsnccnt`和`_mbsnccnt_l`不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### 參數  
 `str`  
 待檢查字串。  
  
 `count`  
 在 `str`檢查的位元組或字元數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 傳回 `str`多位元組字元的第一個 `count` 中的位元組數目。  `_mbsnccnt` 和 `_mbsnccnt_l` 傳回 `str`多位元組字元的第一個 `count` 中的字元數目。  如果在 `str` 中檢查完成之前遇到 Null 字元，會傳回在 Null 字元之前找到的位元組數目或字元。  如果 `str` 包括小於 `count` 字元或位元組，它們傳回字元或位元組數目字串。  如果 `count` 小於零，則會傳回 0。  在舊版中，這些函式的傳回值型別是 `int` 而非 `size_t`。  
  
 `_strncnt` 在單一位元組字串 `str`的第一個 `count` 位元組傳回字元數。  `_wcsncnt` 所傳回的字元是數寬字元字串 `str`的第一個 `count` 的寬度 \(以字元為單位\)。  
  
## 備註  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 會計算 `str`多位元組字元的第一個 `count` 中的位元組數目。  `_mbsnbcnt` 和 `_mbsnbcnt_l` 取代 `mtob` ，且應在 `mtob`位置使用。  
  
 `_mbsnccnt` 和 `_mbsnccnt_l` 會計算 `str`多位元組字元的第一個 `count` 中的字元數目。  如果 `_mbsnccnt` 和 `_mbsnccnt_l` 以雙位元組字元的第二個位元組遇到 NULL，第一個位元組也視為 NULL 且不包含在傳回的值。  `_mbsnccnt` 和 `_mbsnccnt_l` 取代 `btom` ，且應在 `btom`位置使用。  
  
 如果 `str` 為 null 指標或為 `count` 為 0，這些函式會叫用無效的參數處理常式如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述， `errno` 會設定為 `EINVAL`且函式會傳回 0。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|--------|------------------------------|----------------|-------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbcnt`|\<mbstring.h\>|  
|`_mbsnbcnt_l`|\<mbstring.h\>|  
|`_mbsnccnt`|\<mbstring.h\>|  
|`_mbsnccnt_l`|\<mbstring.h\>|  
|`_strncnt`|\<tchar.h\>|  
|`_wcsncnt`|\<tchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## Output  
  
```  
The first 10 characters are single-byte.  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)