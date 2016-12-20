---
title: "strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l | Microsoft Docs"
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
  - "wcstoimax"
  - "_wcstoimax_l"
  - "_strtoimax_l"
  - "strtoimax"
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
  - "wcstoimax"
  - "_tcstoimax"
  - "strtoimax"
  - "_wcstoimax_l"
  - "_strtoimax_l"
  - "_tcstoimax_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtoimax_l 函式"
  - "_wcstoimax_l 函式"
  - "轉換函式"
  - "strtoimax 函式"
  - "wcstoimax 函式"
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為支援的最大帶正負號整數類型的整數值。  
  
## 語法  
  
```  
intmax_t strtoimax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
intmax_t wcstoimax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
intmax_t _strtoimax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
intmax_t _wcstoimax_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `nptr`  
 要轉換的以 Null 結束字串。  
  
 `endptr`  
 停止掃描的字元指標。  
  
 `base`  
 使用的數字底數。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 `strtoimax` 傳回 `nptr` 字串所表示的值，但是在該表示會造成溢位時例外，在該情況下，則會傳回 `INTMAX_MAX` 或 `INTMAX_MIN`，而且 `errno` 設定為 `ERANGE`。  如果不可以執行轉換動作，函式會傳回 0。  `wcstoimax` 回傳值的方式與 `strtoimax` 相似。  
  
 `INTMAX_MAX` 和 `INTMAX_MIN` 是在 stdint.h 中定義的。  
  
 如果 `nptr` 為 `NULL`，或 `base` 為非零值且小於 2 或大於 36，則 `errno` 會設定為 `EINVAL`。  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `strtoimax` 函式會將 `nptr` 轉換成 `intmax_t`。  `strtoimax` 的寬字元版本是 `wcstoimax` ；它的 `nptr` 參數是寬字元字串。  否則，這三個函式的行為相同。  兩個函式都會在第一個無法辨識為數字部分的字元之處停止讀取字串 `nptr`。  這可能是終止 null 字元，或者它可能是大於或等於 `base` 的第一個數字字元。  
  
 地區設定的 `LC_NUMERIC` 分類設定決定如何辨認目前 `nptr`中的基數字元。如需更多的資訊，請參閱[setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後置字元的函式會使用目前的地區設定；`_strtoimax_l` 和 `_wcstoimax_l` 與沒有 `_l` 後置字元的對應函式相同，但會使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，停止掃描的字元的指標會儲存在 `endptr` 所指向的位置。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)，則 `nptr` 的值會儲存在 `endptr` 所指向的位置。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstoimax`|`strtoimax`|`strtoimax`|`wcstoimax`|  
|`_tcstoimax_l`|`strtoimax_l`|`_strtoimax_l`|`_wcstoimax_l`|  
  
 `strtoimax` 預期 `nptr` 指向下列格式的字串：  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits` &#124; `letters`\]  
  
 `whitespace` 可能包含空格和定位字元，這些字元會被忽略；`digits` 是一個或多個十進位數字；`letters` 是一個或多個 'a' 到 'z' \(或 'A' 到 'Z'\) 的字母。  第一個不符合這個格式的字元會停止掃描。  如果 `base` 介於 2 和 36 之間，則會使用它當做數字的底數。  如果 `base` 為 0，則會使用 `nptr` 指向之字串的初始字元來判斷基底。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為八進位整數。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為十六進位整數。  如果第一個字元是 1' 到 '9'，字串會解譯為十進位整數。  字母 'a' 到 'z' \(或 'A' 到 'Z"\) 被指派值 10 到 35；只允許指派值小於 `base` 的字母。  在基底範圍外的第一個字元停止掃描。  例如，如果 `base` 為 0，而且掃描的第一個字元是 '0'，則假設是八進位整數，而且 '8' 或 '9' 字元將會停止掃描。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtoimax`, `_strtoimax_l`, `wcstoimax`, `_wcstoimax_l`|\<inttypes.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoumax、\_strtoumax\_l、wcstoumax、\_wcstoumax\_l](../../c-runtime-library/reference/strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)