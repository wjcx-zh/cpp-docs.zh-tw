---
title: "strtoull、_strtoull_l、wcstoull、_wcstoull_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
dev_langs: C++
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8af8a6c2d96eb0fa4fd37a41e7f022743ab78d7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strtoull-strtoulll-wcstoull-wcstoulll"></a>strtoull、_strtoull_l、wcstoull、_wcstoull_l
將字串轉換為不帶正負號的長整數值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned long long strtoull(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long long _strtoull_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long long wcstoull(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long long _wcstoull_l(  
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
 若有的話，`strtoull` 會傳回已轉換的值，或在發生溢位時傳回 `ULLONG_MAX`。 如果沒有任何轉換可執行，`strtoull` 會傳回 0。 `wcstoull` 傳回類似 `strtoull` 的值。 如果發生溢位或反向溢位，這兩個函式的 `errno` 都會設為 `ERANGE`。  
  
 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 所有這些函式都會將輸入字串 `nptr` 轉換成 `unsigned long long` 整數值。  
  
 `strtoull` 會在它無法辨識為數字一部分的第一個字元處停止讀取字串 `nptr`。 這可能是終止的 Null 字元，或是它可能是第一個大於或等於 `base` 的數值字元。 地區設定的 `LC_NUMERIC` 類別設定會決定 `nptr` 中的基底字元辨識，如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 `strtoull` 和 `wcstoull` 使用目前的地區設定，`_strtoull_l` 和 `_wcstoull_l` 除了改用傳入的地區設定之外，其他相同。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，則停止掃描的字元指標會儲存在由 `endptr` 指向的位置。 如果不能執行任何轉換 (找不到任何有效的數字或指定了無效的基底)，則 `nptr` 的值會儲存在由 `endptr` 指向的位置。  
  
 `wcstoull` 是寬字元版本的 `strtoull`，其 `nptr` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoull`|`strtoull`|`strtoull`|`wcstoull`|  
|`_tcstoull_l`|`strtoull_l`|`_strtoull_l`|`_wcstoull_l`|  
  
 `strtoull` 需要 `nptr` 以指向格式如下的字串︰  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; [`letters`]]  
  
 `whitespace` 包含可忽略的空格和定位字元；`digits` 是一或多個十進位數字；`letters` 是一或多個 'a' 到 'z' (或 'A' 到 'Z') 字母。 不符合此格式的第一個字元會停止掃描。 如果 `base` 介於 2 到 36 之間，則會作為數字的基底。 如果 `base` 為 0，則使用由 `nptr` 指向的字串起始字元來判斷基底。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 `base` 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果 `base` 為 0，而第一個掃描到的字元是 '0'，則假設為八進位整數，且 '8' 或 '9' 字元會停止掃描。 `strtoull` 允許加號 (`+`) 或減號 (`-`) 符號前置詞，前置減號表示傳回值為負數。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strtoull`|\<stdlib.h>|  
|`wcstoull`|\<stdlib.h> 或 \<wchar.h>|  
|`_strtoull_l`|\<stdlib.h>|  
|`_wcstoull_l`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [strtod](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll、_strtoll_l、wcstoll、_wcstoll_l](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)