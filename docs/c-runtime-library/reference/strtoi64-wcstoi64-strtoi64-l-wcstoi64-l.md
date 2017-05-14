---
title: "_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
dev_langs:
- C++
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: d6a3924d92cd13e8c70485d9bd288836d66aab05
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="strtoi64-wcstoi64-strtoi64l-wcstoi64l"></a>_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l
將字串轉換成 `__int64` 整數。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 _strtoi64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
__int64 _wcstoi64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
__int64 _strtoi64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
__int64 _wcstoi64_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nptr`  
 以 Null 終止的待轉換字串。  
  
 `endptr`  
 停止掃描的字元指標。  
  
 `base`  
 要使用的數字基底。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `_strtoi64` 會傳回字串 `nptr` 中的代表值，但表示法可能造成溢位時例外，在此情況下傳回 `_I64_MAX` 或 `_I64_MIN`。 如果沒有任何轉換可執行，函式會傳回 0。 `_wcstoi64` 傳回類似 `strtoi64` 的值。  
  
 `_I64_MAX` 和 `_I64_MIN` 在 LIMITS.H 中定義。  
  
 如果 `nptr` 為 `NULL`，或 `base` 為非零值且小於 2 或大於 36，則 `errno` 會設為 `EINVAL`。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_strtoi64` 函式會將 `nptr` 轉換成 `__int64`。 兩個函式都會在它們無法辨識為數字一部分的第一個字元處停止讀取字串 `nptr`。 這可能是終止的 Null 字元，或是它可能是第一個大於或等於 `base` 的數值字元。 `_wcstoi64` 是寬字元版本的 `_strtoi64`，其 `nptr` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoi64`|`_strtoi64`|`_strtoi64`|`_wcstoi64`|  
|`_tcstoi64_l`|`_strtoi64_l`|`_strtoi64_l`|`_wcstoi64_l`|  
  
 地區設定的 `LC_NUMERIC` 類別設定會決定 `nptr` 中的基底字元辨識，如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 不含 _l 尾碼的函式會使用目前的地區設定;`_strtoi64_l`和`_wcstoi64_l`沒有對應的函式相同`_l`後置詞，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，則停止掃描的字元指標會儲存在由 `endptr` 指向的位置。 如果不能執行任何轉換 (找不到任何有效的數字或指定了無效的基底)，則 `nptr` 的值會儲存在由 `endptr` 指向的位置。  
  
 `_strtoi64` 需要 `nptr` 指向格式如下的字串︰  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits`]  
  
 `whitespace` 包含可忽略的空格及定位字元；`digits` 是一或多個十進位數字。 不符合此格式的第一個字元會停止掃描。 如果 `base` 介於 2 到 36 之間，則會作為數字的基底。 如果 `base` 為 0，則使用由 `nptr` 指向的字串起始字元來判斷基底。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 `base` 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果 `base` 為 0，而第一個掃描到的字元是 '0'，則假設為八進位整數，且 '8' 或 '9' 字元會停止掃描。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_strtoi64`, `_strtoi64_l`|\<stdlib.h>|  
|`_wcstoi64`, `_wcstoi64_l`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
