---
title: "strtold、_strtold_l、wcstold、_wcstold_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
dev_langs:
- C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 60c3b2c8c897558d45dc644cfef5c99b336cf06f
ms.lasthandoff: 02/24/2017

---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold、_strtold_l、wcstold、_wcstold_l
將字串轉換為長雙精確度浮點數值。  
  
## <a name="syntax"></a>語法  
  
```  
long double strtold(  
   const char *nptr,  
   char **endptr   
);  
long double _strtold_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
long double wcstold(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
long double wcstold_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nptr`  
 以 Null 終止的待轉換字串。  
  
 `endptr`  
 停止掃描的字元指標。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `strtold` 會傳回浮點數的值當成 `long double`，但表示法可能造成溢位時例外，在此情況下函式會傳回 +/–`HUGE_VALL`。 `HUGE_VALL` 的正負號符合無法表示之值的正負號。 如果沒有任何轉換可執行，`strtold` 會傳回 0，否則會發生反向溢位。  
  
 `wcstold` 傳回類似 `strtold` 的值。 如果發生溢位或反向溢位且叫用無效的參數處理常式，這兩個函式的 `errno` 都會設為 `ERANGE`，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 每個函式都會將輸入字串 `nptr` 轉換成 `long double`。 `strtold` 函式會將 `nptr` 轉換成長雙精確度值。 `strtold` 會在它無法辨識為數字一部分的第一個字元處停止讀取字串 `nptr`。 這可能是終止的 Null 字元。 `strtold` 的寬字元版本是 `wcstold`，其 `nptr` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstold`|`strtold`|`strtold`|`wcstold`|  
|`_tcstold_l`|`_strtold_l`|`_strtold_l`|`_wcstold_l`|  
  
 目前地區設定的 `LC_NUMERIC` 類別設定會決定 `nptr` 中的基底字元辨識。 如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 沒有 `_l` 尾碼的函式使用目前的地區設定，而 `_strtold_l` 和 `_wcstold_l` 與 `_strtold` 和 `_wcstold` 相同，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，則停止掃描的字元指標會儲存在由 `endptr` 指向的位置。 如果不能執行任何轉換 (找不到任何有效的數字或指定了無效的基底)，則 `nptr` 的值會儲存在由 `endptr` 指向的位置。  
  
 `strtold` 需要 `nptr` 指向格式如下的字串︰  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`d` &#124; `D` &#124; `e` &#124; `E`}[`sign`]`digits`]  
  
 `whitespace` 包含可忽略的空格及定位字元；`sign` 是加號 (`+`) 或減號 (`–`)；而且 `digits` 是一或多個十進位數字。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 小數位數的後面會接著包含簡介字母 (`d`、`D`、`e` 或 `E`) 的指數以及選擇性的帶正負號整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`strtold`, `_strtold_l`|\<stdlib.h>|  
|`wcstold`, `_wcstold_l`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_strtold.c  
// Build with: cl /W4 /Tc crt_strtold.c  
// This program uses strtold to convert a  
// string to a long double-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   long double x;  
  
   string = "3.1415926535898This stopped it";  
   x = strtold(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtold = %.13Lf\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
```Output  
string = 3.1415926535898This stopped it  
   strtold = 3.1415926535898  
   Stopped scan at: This stopped it  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## <a name="see-also"></a>另請參閱  
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
