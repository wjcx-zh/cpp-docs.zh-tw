---
title: "strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l | Microsoft Docs"
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
  - "_wcstoumax_l"
  - "_strtoumax_l"
  - "wcstoumax"
  - "strtoumax"
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
  - "wcstoumax"
  - "_tcstoumax"
  - "_strtoumax_l"
  - "_wcstoumax_l"
  - "_tcstoumax_l"
  - "strtoumax"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtoumax_l 函式"
  - "_wcstoumax_l 函式"
  - "轉換函式"
  - "strtoumax 函式"
  - "wcstoumax 函式"
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為支援的最大不正負號整數類型的整數值。  
  
## 語法  
  
```  
uintmax_t strtoumax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
uintmax_t _strtoumax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
uintmax_t wcstoumax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
uintmax_t _wcstoumax_l(  
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
 要使用的地區設定。  
  
## 傳回值  
 `strtoumax` 傳回轉換後的值 \(如果有\)，在溢位時則傳回 `UINTMAX_MAX`。  如果不可以執行轉換動作，`strtoumax` 會傳回 0。  `wcstoumax` 回傳值的方式與 `strtoumax` 相似。  對於這兩個函式，如果發生溢位或反向溢位時，`errno` 會設為 `ERANGE`。  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 每個這些函式都會將輸入字串 `nptr` 轉換為 `uintmax_t` 整數值。  
  
 `strtoumax` 在遇到字串 `nptr` 中第一個無法辨認為數字的一部分的字元時停止讀取。  這可能是終止 null 字元，或者它可能是大於或等於 `base` 的第一個數字字元。  地區設定的 `LC_NUMERIC` 分類設定決定如何辨認 `nptr` 中的基數字元。  如需詳細資訊，請參閱[setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `strtoumax` 和 `wcstoumax` 使用目前的地區設定；`_strtoumax_l` 和 `_wcstoumax_l` 也是相同，不過改用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，停止掃描的字元的指標會儲存在 `endptr` 所指向的位置。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)，則 `nptr` 的值會儲存在 `endptr` 所指向的位置。  
  
 `strtoumax` 的寬字元版本是 `wcstoumax` ；它的 `nptr` 參數是寬字元字串。  否則，這三個函式的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstoumax`|`strtoumax`|`strtoumax`|`wcstoumax`|  
|`_tcstoumax_l`|`strtoumax_l`|`_strtoumax_l`|`_wcstoumax_l`|  
  
 `strtoumax` 預期 `nptr` 指向下列格式的字串：  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits` &#124; \[`letters`\]\]  
  
 `whitespace` 可能包含已忽略的空格和定位字元；`digits` 是一個或多個十進位數字；`letters` 是一個或多個 'a' 到 'z' \(或 'A' 到 'Z'\) 的字母。  第一個不符合這個格式的字元會停止掃描。  如果 `base` 介於 2 和 36 之間，則會使用它當做數字的底數。  如果 `base` 為 0，則會使用 `nptr` 指向之字串的初始字元來判斷基底。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為八進位整數。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為十六進位整數。  如果第一個字元是 1' 到 '9'，字串會解譯為十進位整數。  字母 'a' 到 'z' \(或 'A' 到 'Z"\) 被指派值 10 到 35；只允許指派值小於 `base` 的字母。  在基底範圍外的第一個字元停止掃描。  例如，如果 `base` 為 0，而且掃描的第一個字元是 '0'，則假設是八進位整數，而且 '8' 或 '9' 字元將會停止掃描。  `strtoumax` 允許加號 \(`+`\) 或減號 \(`–`\) 前置字元；前置減號指示傳回值是轉換後字串的絕對值的二的補數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtoumax`|\<stdlib.h\>|  
|`wcstoumax`|\<stdlib.h\> 或 \<wchar.h\>|  
|`_strtoumax_l`|\<stdlib.h\>|  
|`_wcstoumax_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [strtod](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoimax、\_strtoimax\_l、wcstoimax、\_wcstoimax\_l](../../c-runtime-library/reference/strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll、\_strtoll\_l、wcstoll、\_wcstoll\_l](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)