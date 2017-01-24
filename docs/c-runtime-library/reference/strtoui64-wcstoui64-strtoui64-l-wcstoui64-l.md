---
title: "_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l | Microsoft Docs"
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
  - "_strtoui64"
  - "_strtoui64_l"
  - "_wcstoui64"
  - "_wcstoui64_l"
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
  - "_wcstoui64_l"
  - "strtoui64_l"
  - "wcstoui64"
  - "_wcstoui64"
  - "_strtoui64_l"
  - "strtoui64"
  - "_strtoui64"
  - "wcstoui64_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtoui64 函式"
  - "_strtoui64_l 函式"
  - "_wcstoui64 函式"
  - "_wcstoui64_l 函式"
  - "字串轉換, 到整數"
  - "strtoui64 函式"
  - "strtoui64_l 函式"
  - "wcstoui64 函式"
  - "wcstoui64_l 函式"
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換成不帶正負號的 `__int64` 值。  
  
## 語法  
  
```  
unsigned __int64 _strtoui64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned __int64 _wcstoui64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned __int64 _strtoui64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned __int64 _wcstoui64(  
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
 要停止掃描字元的指標。  
  
 `base`  
 使用的數字底數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_strtoui64` 傳回字串 `nptr` 所表示的值，但是在造成溢位時例外，在該情況下會傳回 `_UI64_MAX`。如果沒有轉換動作可以執行，`strtoui64` 會傳回 0。  
  
 `_UI64_MAX` 定義於 LIMITS.H.。  
  
 如果 `nptr` 為 `NULL`，或 `base` 為非零值且小於 2 或大於 36，則 `errno` 會設定為 `EINVAL`。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_strtoui64` 函式會將 `nptr` 轉換成 `unsigned``__int64`。  `_wcstoui64` 是 `_strtoui64` 的寬字元版本。它的 `nptr` 參數是寬字元字串。  否則，這三個函式的行為相同。  
  
 兩個函式都會在第一個無法辨識為數字部分的字元之處停止讀取字串 `nptr`。  這可能是終止的 null 字元，或者它可能是大於或等於 `base` 的第一個數字字元。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstoui64`|`_strtoui64`|`_strtoui64`|`_wstrtoui64`|  
|`_tcstoui64_l`|`_strtoui64_l`|`_strtoui64_l`|`_wstrtoui64_l`|  
  
 目前地區設定的 `LC_NUMERIC`  分類設定決定如何辨認目前 `nptr` 中的基數字元。如需更多的資訊，請參閱[設定地區設定](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  沒有 \_l 後置字元的函式會使用目前的地區設定；`_strtoui64_l`  和 `_wcstoui64_l`  與沒有 `_l` 後置字元的對應函式相同，除非它們使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，停止掃描的字元的指標會儲存在 `endptr` 所指向的位置。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)， `nptr` 的值會儲存在 `endptr` 所指向的位置。  
  
 `_strtoui64`  預期 `nptr` 指向下列格式的字串：  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits`\]  
  
 `whitespace`  可能由會被忽略的空格和定位字元組成； `digits`  是一個或多個十進位數字。  第一個不符合這個格式的字元會停止掃描。  如果 `base` 介於 2 和 36 之間，則會使用它當做數字的底數。  如果 `base` 為 0，則會使用 `nptr` 指向之字串的初始字元來判斷基底。  如果第一個字元是 0，而第二個字元不是「x」或「X」，字串會解譯為八進位整數。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為十六進位整數。  如果第一個字元是 1' 到 '9'，字串會解譯為十進位整數。  字母 'a' 到 'z' \(或 'A' 到 'Z"\) 被指派值 10 到 35；只允許指派值小於 `base` 的字母。  在基底範圍外的第一個字元停止掃描。  例如，如果 `base` 為 0，而且掃描的第一個字元是「0」，則假設為八進位整數，且「8」或「9」字元將會停止掃描。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strtoui64`|\<stdlib.h\>|  
|`_wcstoui64`|\<stdlib.h\> 或 \<wchar.h\>|  
|`_strtoui64_l`|\<stdlib.h\>|  
|`_wcstoui64_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtoui64.c  
#include <stdio.h>  
  
unsigned __int64 atoui64(const char *szUnsignedInt) {  
   return _strtoui64(szUnsignedInt, NULL, 10);  
}  
  
int main() {  
   unsigned __int64 u = atoui64("18446744073709551615");  
   printf( "u = %I64u\n", u );  
}  
```  
  
  **u \= 18446744073709551615**   
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)