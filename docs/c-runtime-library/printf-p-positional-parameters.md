---
title: "printf_p 位置參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_printf_p 函式, 位置參數"
  - "printf_p 函式, 位置參數"
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# printf_p 位置參數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位置參數會提供根據數字指定的功能，其中引數會取代至格式字串中的欄位。  您可以使用下列位置參數 `printf` 函式：  
  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)  
  
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)  
 [\_sprintf\_p、\_sprintf\_p\_l、\_swprintf\_p、\_swprintf\_p\_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)  
  
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)  
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)  
  
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)  
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)  
  
 [vprintf、\_vprintf\_l、vwprintf、\_vwprintf\_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
 [\_vprintf\_p、\_vprintf\_p\_l、\_vwprintf\_p、\_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)  
  
 [vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)  
 [\_vfprintf\_p、\_vfprintf\_p\_l、\_vfwprintf\_p、\_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)  
  
 [vsprintf、\_vsprintf\_l、vswprintf、\_vswprintf\_l、\_\_vswprintf\_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)  
 [\_vsprintf\_p、\_vsprintf\_p\_l、\_vswprintf\_p、\_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)  
  
## 指定位置參數  
  
##### 參數索引  
 依預設，如果並未顯示位置格式，則位置函式的運作方式與非位置函式完全相同。  使用格式「`%m$x`」指定位置參數，其中 `m` 代表數值的序數數字，指出位於格式字串之前參數清單中的參數位置，且  `x` 表示 `printf` 函式中指定的型別欄位字元型別。  清單中的參數會針對清單中的第一個元素從值 1 開始編製索引，依此類推。  如需有關型別欄位字元的詳細資訊，請參閱 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)。  
  
 如需這個行為的範例，請參閱：  
  
```  
_printf_p("%1$s %2$s", "November", "10");  
```  
  
 將會列印  
  
```  
November 10  
```  
  
 所使用的數字順序不需符合指定的引數順序。  因此，下列是有效的範本：  
  
```  
_printf_p("%2$s %1$s", "November", "10");  
```  
  
 將會列印  
  
```  
10 November  
```  
  
 格式化時參數可能會使用一次以上，與傳統格式字串中不同，因此  
  
```  
_printf_p("%1$d times %1$d is %2$d", 10, 100);  
```  
  
 將會列印  
  
```  
10 times 10 is 100  
```  
  
 不過，所有引數都必須在格式字串中的某處至少使用一次。  
  
 格式字串中允許的位置參數最大數目是由 `_ARGMAX` 所指定。  
  
##### 寬度和精確度  
 當 \* 符號用來指定寬度或精確度是由引數所決定時，則寬度或精確度數值的位置必須緊接在 \* 符號後面顯示。  例如：  
  
```  
_printf_p("%1$*2$s","Hello", 10);  
```  
  
 或  
  
```  
_printf_p("%2$*1$s",10, "Hello");  
```  
  
##### 混合位置和非位置引數  
 位置參數無法在相同格式字串中與非位置參數混合。  不過，`printf_p` 和相關的功能仍支援格式字串中的非位置參數不包含任何位置參數。  
  
## 範例  
  
```  
// positional_args.c  
// Positional arguments allow the specification of the order  
// in which arguments are consumed in a formatting string.  
  
#include <stdio.h>  
  
int main(int argc, char *argv[])  
{  
    int     i = 1,  
            j = 2,  
            k = 3;  
    double  x = 0.1,  
            y = 0.2,  
            z = 0.3;  
    char    *s1 = "abc",  
            *s2 = "def",  
            *s3 = "ghi";  
  
    // If positional arguments are unspecified,  
    // normal input order is used.  
    _printf_p("%d %d %d\n", i, j, k);  
  
    // Positional args are numbers indicating the  
    // argument enclosed in curly braces.  
    _printf_p("%3$d %1$d %2$d\n", i, j, k);  
  
    // The same positional argument may be reused.  
    _printf_p("%1$d %2$d %1$d\n", i, j);  
  
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);  
  
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);  
}  
```  
  
  **1 2 3**  
**3 1 2**  
**1 2 1**  
**abc def ghi**  
**ghi abc def**   
## 請參閱  
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)