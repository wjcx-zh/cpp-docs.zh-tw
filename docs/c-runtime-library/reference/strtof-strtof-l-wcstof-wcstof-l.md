---
title: "strtof、_strtof_l、wcstof、_wcstof_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
dev_langs: C++
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0fdfe3a202d18aa1634a2ef692088264ff8fe188
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof、_strtof_l、wcstof、_wcstof_l
將字串轉換為單精確度浮點數值。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="parameters"></a>參數  
 `nptr`  
 以 Null 終止的待轉換字串。  
  
 `endptr`  
 停止掃描的字元指標。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `strtof`傳回值的浮點數，除了當表示法會造成溢位，情況為函式傳回 + /-`HUGE_VALF`。 `HUGE_VALF` 的正負號符合無法表示之值的正負號。 如果沒有任何轉換可執行，`strtof` 會傳回 0，否則會發生反向溢位。  
  
 `wcstof` 傳回類似 `strtof` 的值。 如果發生溢位或反向溢位且叫用無效的參數處理常式，這兩個函式的 `errno` 都會設為 `ERANGE`，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 每個函式都會將輸入字串 `nptr` 轉換成 `float`。 `strtof` 函式會將 `nptr` 轉換成單精確度值。 `strtof` 會在它無法辨識為數字一部分的第一個字元處停止讀取字串 `nptr`。 這可能是終止的 Null 字元。 `wcstof` 是寬字元版本的 `strtof`，其 `nptr` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstof`|`strtof`|`strtof`|`wcstof`|  
|`_tcstof_l`|`_strtof_l`|`_strtof_l`|`_wcstof_l`|  
  
 目前地區設定的 `LC_NUMERIC` 類別設定會決定 `nptr` 中的基底字元辨識，如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 沒有 `_l` 尾碼的函式使用目前的地區設定，有尾碼的函式也一樣，但它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，則停止掃描的字元指標會儲存在由 `endptr` 指向的位置。 如果不能執行任何轉換 (找不到任何有效的數字或指定了無效的基底)，則 `nptr` 的值會儲存在由 `endptr` 指向的位置。  
  
 `strtof` 需要 `nptr` 指向格式如下的字串︰  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`e` &#124; `E`}[`sign`]`digits`]  
  
 `whitespace` 包含可忽略的空格及定位字元；`sign` 是加號 (`+`) 或減號 (`-`)；而且 `digits` 是一或多個十進位數字。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 小數位數的後面可以接著指數，包含簡介字母 (`e` 或 `E`) 以及選擇性帶正負號的整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。  
 
 這些函式的 UCRT 版本不支援轉換 Fortran 樣式 (`d` 或 `D`) 指數字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strtof`, `_strtof_l`|C: \<stdlib.h> C++: &lt;cstdlib> 或 \<stdlib.h>|  
|`wcstof`, `_wcstof_l`|C:\<stdlib.h> 或 \<wchar.h> C++: &lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
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
  
```Output  
string = 3.14159This stopped it  
   strtof = 3.141590  
   Stopped scan at: This stopped it  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)