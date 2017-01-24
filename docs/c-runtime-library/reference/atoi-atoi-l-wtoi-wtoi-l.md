---
title: "atoi、_atoi_l、_wtoi、_wtoi_l | Microsoft Docs"
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
  - "_wtoi"
  - "_wtoi_l"
  - "atoi"
  - "_atoi_l"
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
  - "_tstoi"
  - "_wtoi"
  - "_ttoi"
  - "atoi"
  - "_atoi_l"
  - "_wtoi_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_atoi_l 函式"
  - "ttoi 函式"
  - "atoi_l 函式"
  - "字串轉換, 到整數"
  - "_wtoi 函式"
  - "wtoi_l 函式"
  - "tstoi 函式"
  - "_ttoi 函式"
  - "_tstoi 函式"
  - "_wtoi_l 函式"
  - "atoi 函式"
  - "wtoi 函式"
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atoi、_atoi_l、_wtoi、_wtoi_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換字串為整數。  
  
## 語法  
  
```  
int atoi(  
   const char *str   
);  
int _wtoi(  
   const wchar_t *str   
);  
int _atoi_l(  
   const char *str,  
   _locale_t locale  
);  
int _wtoi_l(  
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
 每個函式會傳回將輸入字元解譯為數字所產生的 `int` 值。  如果輸入無法轉換為該類型的值，`atoi` 和`_wtoi` 的傳回值為 0。  
  
 在處理大型負整數值的溢位的情況下，則會傳回 `LONG_MIN` 。  `atoi` 和 `_wtoi` 傳回 `INT_MAX` 和 `INT_MIN` 在這些情況。  在所有超出範圍的情況下，`errno` 會設為 `ERANGE`。  如果傳入的參數是 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 \-0。  
  
## 備註  
 這些函式會將字元字串轉換為整數值\(`atoi`和`_wtoi`\)。  輸入字串是可解譯為指定類型的數值的字元序列。   函式在遇到第一個無法辨識為數字一部分的字元時，會停止讀取輸入字串。  這個字元可能是終止字串的 null 字元 \('\\0' 或 L'\\0'\)。  
  
 `atoi` 和  `` 和`_wtoi` 的 `str` 引數有下列形式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 `whitespace` 包含空格或定位字元，這些字元會被忽略。`sign` 是加號 \(\+\) 或減號 \(–\)；`digits` 是一個或多個數字。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstoi`|`atoi`|`atoi`|`_wtoi`|  
|`_ttoi`|`atoi`|`atoi`|`_wtoi`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`atoi`|\<stdlib.h\>|  
|`_atoi_l`, `_wtoi`, `_wtoi_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 範例  
 這個程式會示範如何使用 `atoi` 函式，將儲存為字串的數字轉換為值。  
  
```  
// crt_atoi.c  
// This program shows how numbers   
// stored as strings can be converted to  
// numeric values using the atoi functions.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    int     value = 0;  
  
    // An example of the atoi function.  
    str = "  -2309 ";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function.  
    str = "31412764";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function   
    // with an overflow condition occuring.  
    str = "3336402735171707160320";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **函式：atoi\( " \-2309 " \) \= \-2309**  
**函式：atoi\( "31412764" \) \= 31412764**  
**函式：atoi\( "3336402735171707160320" \) \= 2147483647**  
**發生溢位情況。**   
## .NET Framework 對等用法  
  
-   [System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)  
  
-   [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl、\_atodbl\_l、\_atoldbl、\_atoldbl\_l、\_atoflt、\_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)