---
title: "strtof、_strtof_l、wcstof、_wcstof_l | Microsoft Docs"
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
  - "_strtof_l"
  - "wcstof"
  - "strtof"
  - "_wcstof_l"
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
  - "_tcstof"
  - "_tcstof_l"
  - "stdlib/strtof"
  - "strtof"
  - "stdlib/_strtof_l"
  - "_strtof_l"
  - "corecrt_wstdlib/wcstof"
  - "wcstof"
  - "corecrt_wstdlib/_wcstof_l"
  - "_wcstof_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtof_l 函式"
  - "_tcstof 函式"
  - "_tcstof_l 函式"
  - "_wcstof_l 函式"
  - "strtof 函式"
  - "wcstof 函式"
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
caps.latest.revision: 9
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtof、_strtof_l、wcstof、_wcstof_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為單精確度浮點數值。  
  
## 語法  
  
```  
float strtof(  
   const char *nptr,  
   char **endptr   
);  
float _strtof_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
float wcstof(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
float wcstof_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `nptr`  
 要轉換的以 Null 結束字串。  
  
 `endptr`  
 停止掃描的字元指標。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 `strtof` 會傳回浮點數的值，除非此表示方式會造成溢位，此時函式會傳回 \+\/\-`HUGE_VALF`。  `HUGE_VALF` 的符號符合無法表示的值的正負號。  如果轉換無法執行或發生反向溢位時，`strtof` 會傳回 0。  
  
 `wcstof` 回傳值的方式與 `strtof` 相似。  對於兩個函式，如果發生上溢位或下溢位，而叫用無效參數處理常式時，`errno` 會設為 `ERANGE`，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 每個函式都會將輸入字串 `nptr` 轉換為 `float`。  `strtof` 函式會將 `nptr` 轉換為單精確度值。  `strtof` 在遇到字串 `nptr` 中第一個無法辨認為數字的一部分的字元時停止讀取。  這可能是結束的空字元。  `wcstof` 是 `strtof` 的寬字元版本。它的 `nptr` 參數是寬字元字串。  否則，這三個函式的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstof`|`strtof`|`strtof`|`wcstof`|  
|`_tcstof_l`|`_strtof_l`|`_strtof_l`|`_wcstof_l`|  
  
 目前地區設定的 `LC_NUMERIC` 分類設定決定如何辨認目前 `nptr`中的基數字元。如需更多的資訊，請參閱[setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後置字元的函式會使用目前的地區設定；有後置字元的對應函式，除了使用傳入的地區設定外，其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，停止掃描的字元的指標會儲存在 `endptr` 所指向的位置。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)，則 `nptr` 的值會儲存在 `endptr` 所指向的位置。  
  
 `strtof` 預期 `nptr` 指向下列格式的字串：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` 可能包含空格和定位字元，這些字元會被忽略；`sign` 是加號 \(`+`\) 或減號 \(`–`\)；`digits` 是一個或多個十進位數字。  如果基數字元之前沒有數字，則基數字元之後必須至少出現一個數字。  十進位數字後面可以跟著指數，指數包括一個引入字母 \(`d` 、 `D` 、 `e` 或 `E`\) 和選擇性地一個帶正負號的整數。  如果指數部分或基數字元都沒有出現，則假設字串中最後一個數字後面有基數字元。  第一個不符合這個格式的字元會停止掃描。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtof`, `_strtof_l`|\<stdlib.h\>|  
|`wcstof`, `_wcstof_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtof.c  
// This program uses strtof to convert a  
// string to a single-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   float x;  
  
   string = "3.14159This stopped it";  
   x = strtof(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtof = %f\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
  **string \= 3.14159This stopped it**  
 **strtof \= 3.141590**  
 **Stopped scan at: This stopped it**   
## .NET Framework 對等用法  
 [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)