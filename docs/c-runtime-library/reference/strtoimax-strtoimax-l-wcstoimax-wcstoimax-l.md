---
title: "strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
dev_langs:
- C++
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
caps.latest.revision: 5
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 8bfc864245fbf2d45b6cc800c2f063dfb8c4ede3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l
將字串轉換成最大的受支援帶正負號整數類型的整數值。  
  
## <a name="syntax"></a>語法  
  
```  
intmax_t strtoimax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
intmax_t wcstoimax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
intmax_t _strtoimax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
intmax_t _wcstoimax_l(  
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
 `strtoimax` 會傳回字串 `nptr` 中的代表值，但表示法可能造成溢位時例外，在此情況下傳回 `INTMAX_MAX` 或 `INTMAX_MIN`，並將 `errno` 設成 `ERANGE`。 如果沒有任何轉換可執行，函式會傳回 0。 `wcstoimax` 傳回類似 `strtoimax` 的值。  
  
 `INTMAX_MAX` 和 `INTMAX_MIN` 在 stdint.h 中定義。  
  
 如果 `nptr` 為 `NULL`，或 `base` 為非零值且小於 2 或大於 36，則 `errno` 會設為 `EINVAL`。  
  
 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `strtoimax` 函式會將 `nptr` 轉換成 `intmax_t`。 `strtoimax` 的寬字元版本是 `wcstoimax`，其 `nptr` 引數是寬字元字串。 否則，這些函式的行為相同。 兩個函式都會在它們無法辨識為數字一部分的第一個字元處停止讀取字串 `nptr`。 這可能是終止的 Null 字元，或是它可能是第一個大於或等於 `base` 的數值字元。  
  
 地區設定的 `LC_NUMERIC` 類別設定會決定 `nptr` 中的基底字元辨識，如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 尾碼的函式使用目前的地區設定，而 `_strtoimax_l` 和 `_wcstoimax_l` 與對應之無 `_l` 尾碼的函式相同，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不是 `NULL`，則停止掃描的字元指標會儲存在由 `endptr` 指向的位置。 如果不能執行任何轉換 (找不到任何有效的數字或指定了無效的基底)，則 `nptr` 的值會儲存在由 `endptr` 指向的位置。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoimax`|`strtoimax`|`strtoimax`|`wcstoimax`|  
|`_tcstoimax_l`|`strtoimax_l`|`_strtoimax_l`|`_wcstoimax_l`|  
  
 `strtoimax` 需要 `nptr` 指向格式如下的字串︰  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; `letters`]  
  
 `whitespace` 包含可忽略的空格和定位字元；`digits` 是一或多個十進位數字；`letters` 是一或多個 'a' 到 'z' (或 'A' 到 'Z') 字母。 不符合此格式的第一個字元會停止掃描。 如果 `base` 介於 2 到 36 之間，則會作為數字的基底。 如果 `base` 為 0，則使用由 `nptr` 指向的字串起始字元來判斷基底。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 `base` 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果 `base` 為 0，而第一個掃描到的字元是 '0'，則假設為八進位整數，且 '8' 或 '9' 字元會停止掃描。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`strtoimax`, `_strtoimax_l`, `wcstoimax`, `_wcstoimax_l`|\<inttypes.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l](../../c-runtime-library/reference/strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
