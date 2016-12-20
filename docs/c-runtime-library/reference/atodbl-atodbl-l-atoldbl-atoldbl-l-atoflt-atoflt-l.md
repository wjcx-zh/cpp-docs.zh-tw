---
title: "_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l | Microsoft Docs"
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
  - "_atoldbl"
  - "_atoldbl_l"
  - "_atodbl"
  - "_atoflt"
  - "_atoflt_l"
  - "_atodbl_l"
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
  - "_atoflt"
  - "_atoflt_l"
  - "atodbl_l"
  - "atoflt_l"
  - "_atoldbl"
  - "_atoldbl_l"
  - "atodbl"
  - "_atodbl_l"
  - "atoldbl"
  - "atoflt"
  - "atoldbl_l"
  - "_atodbl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_atodbl 函式"
  - "_atoldbl_l 函式"
  - "atoflt 函式"
  - "atoflt_l 函式"
  - "atoldbl 函式"
  - "_atoldbl 函式"
  - "atodbl_l 函式"
  - "_atoflt_l 函式"
  - "atoldbl_l 函式"
  - "atodbl 函式"
  - "字串轉換，到浮點值"
  - "_atoflt 函式"
  - "_atodbl_l 函式"
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為雙精度浮點數 \(`_atodbl`\)、長雙精度浮點數 \(`_atoldbl`\)，或浮點數 \(`_atoflt`\)。  
  
## 語法  
  
```  
int _atodbl(  
   _CRT_DOUBLE * value,  
   char * str  
);  
int _atodbl_l (  
   _CRT_DOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoldbl(  
   _LDOUBLE * value,  
   char * str  
);  
int _atoldbl_l (  
   _LDOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoflt(  
   _CRT_FLOAT * value,  
   const char * str  
);  
int _atoflt_l(  
   _CRT_FLOAT * value,  
   const char * str,  
   locale_t locale  
);  
```  
  
#### 參數  
 `value`  
 透過由字串轉換成浮點值而產生的雙精度、長雙精度或浮點數值。  這些值封裝在一個結構中。  
  
 `str`  
 要剖析轉換為浮點值的字串。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 如果成功則傳回 0。  可能的錯誤碼是 `_UNDERFLOW` 或 `_OVERFLOW`，定義於標頭檔 Math.h 中。  
  
## 備註  
 這些函式將字串轉換成浮點值。  這些函式和和函式的 `atof` 系列的差異是這些函式不產生浮點程式碼，且不會產生硬體例外狀況。  相反地，錯誤狀況報告為錯誤碼。  
  
 如果字串沒有有效的解譯如浮點值， `value` 會設定為零，且傳回值為零。  
  
 有 `_l` 後置字元的函式版本除了使用傳入的地區設定參數 \(而不是目前的地區設定\) 外，其餘與沒有後置字元的函式版本相同。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_atodbl`, `_atoldbl`, `_atoflt`<br /><br /> `_atodbl_l`, `_atoldbl_l`, `_atoflt_l`|\<stdlib.h\>|  
  
## 範例  
  
```  
// crt_atodbl.c  
// Uses _atodbl to convert a string to a double precision  
// floating point value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
   char str1[256] = "3.141592654";  
   char abc[256] = "abc";  
   char oflow[256] = "1.0E+5000";  
   _CRT_DOUBLE dblval;  
   _CRT_FLOAT fltval;  
   int retval;  
  
   retval = _atodbl(&dblval, str1);  
  
   printf("Double value: %lf\n", dblval.x);  
   printf("Return value: %d\n\n", retval);  
  
   retval = _atoflt(&fltval, str1);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // A non-floating point value: returns 0.  
   retval = _atoflt(&fltval, abc);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // Overflow.  
   retval = _atoflt(&fltval, oflow);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   return 0;  
}  
```  
  
  **Double value: 3.141593**  
**Return value: 0**  
**Float value: 3.141593**  
**Return value: 0**  
**Float value: 0.000000**  
**Return value: 0**  
**Float value: 1.\#INF00**  
**Return value: 3**   
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)