---
title: "strtod、_strtod_l、wcstod、_wcstod_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcstod"
  - "_wcstod_l"
  - "_strtod_l"
  - "strtod"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstod"
  - "strtod"
  - "wcstod"
  - "_strtod_l"
  - "_wcstod_l"
  - "stdlib/strtod"
  - "corecrt_wstdlib/wcstod"
  - "stdlib/_strtod_l"
  - "corecrt_wstdlib/_wcstod_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtod_l 函式"
  - "_tcstod 函式"
  - "_tcstod_l 函式"
  - "_wcstod_l 函式"
  - "字串轉換, 到浮點值"
  - "strtod 函式"
  - "strtod_l 函式"
  - "tcstod 函式"
  - "tcstod_l 函式"
  - "wcstod 函式"
  - "wcstod_l 函式"
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: 20
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtod、_strtod_l、wcstod、_wcstod_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換字串為雙精確度值。  
  
## 語法  
  
```  
double strtod(  
   const char *nptr,  
   char **endptr   
);  
double _strtod_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
double wcstod(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
double wcstod_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `nptr`  
 要轉換的以 Null 結束字串。  
  
 `endptr`  
 要停止掃描字元的指標。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `strtod` 會傳回浮點數的值，除非此表示方式會造成溢位，此時函式會傳回 \+\/\-`HUGE_VAL`。  `HUGE_VAL` 的符號符合無法表示的值的正負號。  如果轉換無法執行或發生反向溢位時，`strtod` 會傳回 0。  
  
 `wcstod` 回傳值的方式與 `strtod` 相似。  對於兩個函式，如果發生上溢位或下溢位，而叫用無效參數處理常式時，`errno` 會設為 `ERANGE`，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 每個函式都會將輸入字串 `nptr` 轉換為 `double`。  `strtod` 函式轉換 `nptr` 為雙精確度值。  `strtod` 在遇到字串 `nptr` 中第一個無法辨認為數字的一部分的字元時停止讀取。  這可能是結束的空字元。  `wcstod` 是 `strtod` 的寬字元版本。它的 `nptr` 參數是寬字元字串。  這三個函式其餘部分的運作相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstod`|`strtod`|`strtod`|`wcstod`|  
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|  
  
 目前地區設定的 `LC_NUMERIC` 分類設定決定如何辨認目前 `nptr` 中的基底字元。如需更多的資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後綴的函式使用目前的地區設定， `_strtod_l` 與 `_strtod_l` 相同，差異在於它們會使用傳遞的區域設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，停止掃描的字元的指標會儲存在 `endptr` 所指向的位置。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)， `nptr` 的值會儲存在 `endptr` 所指向的位置。  
  
 `strtod` 預期 `nptr` 指向下列格式的字串：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` 可能包含空格和定位字元，這些字元會被忽略；`sign` 是加號 \(`+`\) 或減號 \(`–`\)；`digits` 是一個或多個十進位數字。  如果基數字元之前沒有數字，則基數字元之後必須至少出現一個數字。  十進位數字後面可以跟著指數，指數包括一個引入字母 \(`d` 、 `D` 、 `e` 或 `E`\) 和選擇性地一個帶正負號的整數。  如果指數部分或基數字元都沒有出現，則假設字串中最後一個數字後面有基數字元。  第一個不符合這個格式的字元會停止掃描。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtod`, `_strtod_l`|\<stdlib.h\>|  
|`wcstod`, `_wcstod_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtod.c  
// This program uses strtod to convert a  
// string to a double-precision value; strtol to  
// convert a string to long integer values; and strtoul  
// to convert a string to unsigned long-integer values.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char   *string, *stopstring;  
   double x;  
   long   l;  
   int    base;  
   unsigned long ul;  
  
   string = "3.1415926This stopped it";  
   x = strtod( string, &stopstring );  
   printf( "string = %s\n", string );  
   printf("   strtod = %f\n", x );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "-10110134932This stopped it";  
   l = strtol( string, &stopstring, 10 );  
   printf( "string = %s\n", string );  
   printf("   strtol = %ld\n", l );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "10110134932";  
   printf( "string = %s\n", string );  
  
   // Convert string using base 2, 4, and 8:  
   for( base = 2; base <= 8; base *= 2 )  
   {  
      // Convert the string:  
      ul = strtoul( string, &stopstring, base );  
      printf( "   strtol = %ld (base %d)\n", ul, base );  
      printf( "   Stopped scan at: %s\n", stopstring );  
   }  
}  
```  
  
  **string \= 3.1415926This stopped it**  
 **strtod \= 3.141593**  
 **Stopped scan at: This stopped it**  
**string \= \-10110134932This stopped it**  
 **strtol \= \-2147483648**  
 **Stopped scan at: This stopped it**  
**string \= 10110134932**  
 **strtol \= 45 \(base 2\)**  
 **Stopped scan at: 34932**  
 **strtol \= 4423 \(base 4\)**  
 **Stopped scan at: 4932**  
 **strtol \= 2134108 \(base 8\)**  
 **Stopped scan at: 932**   
## .NET Framework 對等用法  
 [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)