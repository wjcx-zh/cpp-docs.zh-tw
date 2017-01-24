---
title: "atof、_atof_l、_wtof、_wtof_l | Microsoft Docs"
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
  - "_wtof_l"
  - "atof"
  - "_atof_l"
  - "_wtof"
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
  - "_tstof"
  - "_ttof"
  - "atof"
  - "stdlib/atof"
  - "math/atof"
  - "_atof_l"
  - "stdlib/_atof_l"
  - "math/_atof_l"
  - "_wtof"
  - "corecrt_wstdlib/_wtof"
  - "_wtof_l"
  - "corecrt_wstdlib/_wtof_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tstof 函式"
  - "atof_l 函式"
  - "_atof_l 函式"
  - "atof 函式"
  - "_tstof 函式"
  - "_ttof 函式"
  - "wtof 函式"
  - "_wtof_l 函式"
  - "ttof 函式"
  - "wtof_l 函式"
  - "_wtof 函式"
  - "字串轉換，到浮點值"
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: 26
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atof、_atof_l、_wtof、_wtof_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為雙精度浮點數值。  
  
## 語法  
  
```  
double atof(  
   const char *str   
);  
double _atof_l(  
   const char *str,  
   _locale_t locale  
);  
double _wtof(  
   const wchar_t *str   
);  
double _wtof_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 要轉換的字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 每個函式會傳回將輸入字元解譯為數字所產生的 `double` 值。  如果輸入無法轉換為該類型的值，傳回值為 0.0。  
  
 在所有超出範圍的情況下，errno 會設為 `ERANGE`。  如果傳入的參數是 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 \-0。  
  
## 備註  
 這些函式會轉換為字串為雙精度浮點值。  
  
 輸入字串是可解譯為指定類型的數值的字元序列。   函式在遇到第一個無法辨識為數字一部分的字元時，會停止讀取輸入字串。  這個字元可能是終止字串的 null 字元 \('\\0' 或 L'\\0'\)。  
  
 `atof` 和 `_wtof` 的 `str` 引數有下列形式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E` }\[`sign`\]`digits`\]  
  
 `whitespace` 包含空格或定位字元，這些字元會被忽略。`sign` 是加號 \(\+\) 或減號 \(–\)；`digits` 是一個或多個十進位數字。  如果小數點前沒有數值，至少有一個必須在小數點後出現。  十進位數字後面可能跟著指數，指數包括一個引入字母 \(`d` 、 `D` 、 `e` 或 `E`\) 和選擇性地一個帶正負號的十進位整數。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE 和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstof`|`atof`|`atof`|`_wtof`|  
|`_ttof`|`atof`|`atof`|`_wtof`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`atof`|\<math.h\> 和 \<stdlib.h\>|  
|`_atof_l`|\<math.h\> 和 \<stdlib.h\>|  
|`_wtof`, `_wtof_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 範例  
 這個程式會示範如何使用 `atof` 函式，將儲存為字串的數字轉換為值。  
  
```  
// crt_atof.c  
//  
// This program shows how numbers stored as   
// strings can be converted to numeric  
// values using the atof function.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    double  value = 0;  
  
    // An example of the atof function  
    // using leading and training spaces.  
    str = "  3336402735171707160320 ";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // Another example of the atof function  
    // using the 'd' exponential formatting keyword.  
    str = "3.1412764583d210";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // An example of the atof function  
    // using the 'e' exponential formatting keyword.  
    str = "  -2309.12E-15";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
}  
```  
  
  **函式:atof\( "  3336402735171707160320 " \)  \= 3.336403e\+021**  
**函式: atof\( "3.1412764583d210" \) \= 3.141276e\+210**  
**函式: atof\( "  \-2309.12E\-15" \) \= \-2.309120e\-012**   
## .NET Framework 對等用法  
  
-   [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)  
  
-   [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl、\_atodbl\_l、\_atoldbl、\_atoldbl\_l、\_atoflt、\_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)