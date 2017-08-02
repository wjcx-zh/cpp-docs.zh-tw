---
title: "資料類型常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
dev_langs:
- C++
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 1406e086818ea6f71d32e345aaf3d0d79b91940c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="data-type-constants"></a>資料類型常數
資料類型常數是整數資料類型所允許值的實作相關範圍。 下列常數指定整數資料類型的範圍，並定義於 LIMITS.H 中。  
  
> [!NOTE]
>  /J 編譯器選項將預設 `char` 類型變更為 `unsigned`。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|**SCHAR_MAX**|127|最大帶正負號 `char` 值|  
|**SCHAR_MIN**|-128|最小帶正負號 `char` 值|  
|**UCHAR_MAX**|255 (0xff)|最大 `unsigned char` 值|  
|**CHAR_BIT**|8|`char` 中的位元數|  
|**USHRT_MAX**|65535 (0xffff)|最大 **unsigned short** 值|  
|**SHRT_MAX**|32767|最大 (帶正負號) **short** 值|  
|**SHRT_MIN**|-32768|最小 (帶正負號) **short** 值|  
|**UINT_MAX**|4294967295 (0xffffffff)|最大 `unsigned int` 值|  
|**ULONG_MAX**|4294967295 (0xffffffff)|最大 `unsigned long` 值|  
|**INT_MAX**|2147483647|最大帶正負號 `int` 值|  
|**INT_MIN**|-2147483647-1|最小 (帶正負號) `int` 值|  
|**LONG_MAX**|2147483647|最大 (帶正負號) **long** 值|  
|**LONG_MIN**|-2147483647-1|最小 (帶正負號) **long** 值|  
|**CHAR_MAX**|127 (如果使用 /J 選項，則為 255)|最大 `char` 值|  
|**CHAR_MIN**|-128 (如果使用 /J 選項，則為 0)|最小 `char` 值|  
|**MB_LEN_MAX**|2|多位元組 `char` 中的最大位元組數|  
|**_I64_MAX**|9223372036854775807|最大 (帶正負號) __**int64** 值|  
|**_I64_MIN**|-9223372036854775807-1|最小 (帶正負號) __**int64** 值|  
|**_UI64_MAX**|0xffffffffffffffff|最大 (不帶正負號) __**int64** 值|  
  
 下列常數提供 **double** 和 **float** 資料類型的範圍和其他特性，並且定義於 FLOAT.H 中：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**DBL_DIG**|15|十進位位數精確度|  
|**DBL_EPSILON**|2.2204460492503131e-016|最小，因此 1.0+**DBL_EPSILON** !=1.0|  
|**DBL_MANT_DIG**|53|尾數中的位元數|  
|**DBL_MAX**|1.7976931348623158e+308|最大值|  
|**DBL_MAX_10_EXP**|308|最大十進位指數|  
|**DBL_MAX_EXP**|1024|最大二進位指數|  
|**DBL_MIN**|2.2250738585072014e-308|最小正值|  
|**DBL_MIN_10_EXP**|(-307)|最小十進位指數|  
|**DBL_MIN_EXP**|(-1021)|最小二進位指數|  
|**_DBL_RADIX**|2|指數基數|  
|**_DBL_ROUNDS**|1|加法四捨五入︰接近|  
|**FLT_DIG**|6|十進位位數精確度|  
|**FLT_EPSILON**|1.192092896e-07F|最小，因此 1.0+**FLT_EPSILON** !=1.0|  
|**FLT_MANT_DIG**|24|尾數中的位元數|  
|**FLT_MAX**|3.402823466e+38F|最大值|  
|**FLT_MAX_10_EXP**|38|最大十進位指數|  
|**FLT_MAX_EXP**|128|最大二進位指數|  
|**FLT_MIN**|1.175494351e-38F|最小正值|  
|**FLT_MIN_10_EXP**|(-37)|最小十進位指數|  
|**FLT_MIN_EXP**|(-125)|最小二進位指數|  
|**FLT_RADIX**|2|指數基數|  
|**FLT_ROUNDS**|1|加法四捨五入︰接近|  
  
## <a name="see-also"></a>另請參閱  
 [全域常數](../c-runtime-library/global-constants.md)
