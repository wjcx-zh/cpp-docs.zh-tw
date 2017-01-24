---
title: "atol、_atol_l、_wtol、_wtol_l | Microsoft Docs"
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
  - "atol"
  - "_wtol_l"
  - "_wtol"
  - "_atol_l"
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
  - "_atol_l"
  - "_ttol_l"
  - "_tstol_l"
  - "_tstol"
  - "_wtol"
  - "_ttol"
  - "_wtol_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tstol 函式"
  - "atol 函式"
  - "ttol 函式"
  - "_atol_l 函式"
  - "_tstol_l 函式"
  - "字串轉換，到整數"
  - "_tstol 函式"
  - "_ttol 函式"
  - "_ttol_l 函式"
  - "atol_l 函式"
  - "wtol_l 函式"
  - "_wtol_l 函式"
  - "wtol 函式"
  - "_wtol 函式"
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atol、_atol_l、_wtol、_wtol_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換成長整數。  
  
## 語法  
  
```  
long atol(  
   const char *str   
);  
long _atol_l(  
   const char *str,  
   _locale_t locale  
);  
long _wtol(  
   const wchar_t *str   
);  
long _wtol_l(  
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
 每個函式會傳回將輸入字元解譯為數字所產生的 `long` 值。  如果輸入無法轉換為該類型的值，`atol` 的傳回值為 0L。  
  
 在處理大型正整數值的溢位的情況下， `atol` 會傳回 `LONG_MAX`;在處理大型負整數值的溢位的情況下，則會傳回 `LONG_MIN` 。  在所有超出範圍的情況下，`errno` 會設為 `ERANGE`。  如果傳入的參數是 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 \-0。  
  
## 備註  
 這些函式會將字元字串轉換為長整數\(`atol`\)。  
  
 輸入字串是可解譯為指定類型的數值的字元序列。   函式在遇到第一個無法辨識為數字一部分的字元時，會停止讀取輸入字串。  這個字元可能是終止字串的`NULL`字元 \('\\0' 或 L'\\0'\)。  
  
 `atol` 的 `str` 引數有下列形式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 `whitespace` 包含空格或定位字元，這些字元會被忽略。`sign` 是加號 \(\+\) 或減號 \(–\)；`digits` 是一個或多個數字。  
  
 `_wtol` 與 `atol` 相同，但是前者採用寬字元字串。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE &和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tstol`|`atol`|`atol`|`_wtol`|  
|`_ttol`|`atol`|`atol`|`_wtol`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`atol`|\<stdlib.h\>|  
|`_atol_l`, `_wtol`, `_wtol_l`|\<stdlib.h\> 以及 \<wchar.h\>|  
  
## 範例  
 這個程式會示範如何使用 `atol` 函式，將儲存為字串的數字轉換為值。  
  
```  
// crt_atol.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the atol functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    long    value = 0;  
  
    // An example of the atol function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **函式atol \( "\-2309 " \) \= \-2309**  
**函式:atol\( "314127.64" \) \=314127**  
**函式:atol\( "3336402735171707160320" \) \= 2147483647**  
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