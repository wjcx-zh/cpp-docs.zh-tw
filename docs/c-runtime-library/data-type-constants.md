---
title: 資料類型常數
ms.date: 06/25/2018
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
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
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
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
ms.openlocfilehash: c4ffbf294083131f29ffe957fd0434182fbb8f99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636926"
---
# <a name="data-type-constants"></a>資料類型常數

資料類型常數是整數和浮點數資料類型所允許值的實作相關範圍。

## <a name="integral-type-constants"></a>整數類型常數

這些常數會提供整數資料類型的範圍。 若要使用這些常數，請在原始程式檔中包括 limits.h 標頭：

```C
#include <limits.h>
```

> [!NOTE]
> [/J](../build/reference/j-default-char-type-is-unsigned.md) 編譯器選項會將預設的 **char** 類型變更為**不帶正負號**。

|常數|值|描述|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|**char** 中的位元數|
|**SCHAR_MIN**|(-128)|帶正負號的最小 **char** 值|
|**SCHAR_MAX**|127|帶正負號的最大 **char** 值|
|**UCHAR_MAX**|255 (0xff)|**不帶正負號**的最大 **char** 值|
|**CHAR_MIN**|(-128) (如果使用 **/J** 選項，則為 0)|**char** 最小值|
|**CHAR_MAX**|127 (如果使用 **/J** 選項，則為 255)|最大 **char** 值|
|**MB_LEN_MAX**|5|多位元組 **char** 中的最大位元組數|
|**SHRT_MIN**|-32768|帶正負號的最小 **short** 值|
|**SHRT_MAX**|32767|帶正負號的最大 **short** 值|
|**USHRT_MAX**|65535 (0xffff)|**不帶正負號**的最大 **short** 值|
|**INT_MIN**|(-2147483647 - 1)|帶正負號的最小 **int** 值|
|**INT_MAX**|2147483647|帶正負號的最大 **int** 值|
|**UINT_MAX**|4294967295 (0xffffffff)|**不帶正負號**的最大 **int** 值|
|**LONG_MIN**|(-2147483647L - 1)|帶正負號的最小 **long** 值|
|**LONG_MAX**|2147483647L|帶正負號的最大 **long** 值|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|**不帶正負號**的最大 **long** 值|
|**LLONG_MIN**|(-9223372036854775807LL - 1)|帶正負號的最小 **long** **long** 或 **__int64** 值|
|**LLONG_MAX**|9223372036854775807LL|帶正負號的最大 **long** **long** 或 **__int64** 值|
|**ULLONG_MAX**|0xffffffffffffffffull|**不帶正負號**的最大 **long** **long** 值|
|**_I8_MIN**|(-127i8 - 1)|帶正負號的最小 8 位元值|
|**_I8_MAX**|127i8|帶正負號的最大 8 位元值|
|**_UI8_MAX**|0xffui8|不帶正負號的最大 8 位元值|
|**_I16_MIN**|(-32767i16 - 1)|帶正負號的最小 16 位元值|
|**_I16_MAX**|32767i16|帶正負號的最大 16 位元值|
|**_UI16_MAX**|0xffffui16|不帶正負號的最大 16 位元值|
|**_I32_MIN**|(-2147483647i32 - 1)|帶正負號的最小 32 位元值|
|**_I32_MAX**|2147483647i32|帶正負號的最大 32 位元值|
|**_UI32_MAX**|0xffffffffui32|不帶正負號的最大 32 位元值|
|**_I64_MIN**|(-9223372036854775807 - 1)|帶正負號的最小 64 位元值|
|**_I64_MAX**|9223372036854775807|帶正負號的最大 64 位元值|
|**_UI64_MAX**|0xffffffffffffffffui64|不帶正負號的最大 64 位元值|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|帶正負號的最小 128 位元值|
|**_I128_MAX**|170141183460469231731687303715884105727i128|帶正負號的最大 128 位元值|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|不帶正負號的最大 128 位元值|
|**SIZE_MAX**|如果已定義 **_WIN64**，則與 **_UI64_MAX** 相同；否則為 **UINT_MAX**|最大的原生整數大小|
|**RSIZE_MAX**|與 (**SIZE_MAX** >> 1) 相同|最大的安全程式庫整數大小|

## <a name="floating-point-type-constants"></a>浮點數類型常數

下列常數提供 **long** **double**、**double** 和 **float** 資料類型的範圍和其他特性。 若要使用這些常數，請在原始程式檔中包括 float.h 標頭：

```C
#include <float.h>
```

|常數|值|描述|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|十進位位數的進位精確度|
|**DBL_DIG**|15|十進位位數精確度|
|**DBL_EPSILON**|2.2204460492503131e-016|最小，因此 1.0 + **DBL_EPSILON** != 1.0|
|**DBL_HAS_SUBNORM**|1|類型支援偏低的 (異常) 數字|
|**DBL_MANT_DIG**|53|有效位數 (尾數) 中的位元數|
|**DBL_MAX**|1.7976931348623158e+308|最大值|
|**DBL_MAX_10_EXP**|308|最大十進位指數|
|**DBL_MAX_EXP**|1024|最大二進位指數|
|**DBL_MIN**|2.2250738585072014e-308|最小的標準化正值|
|**DBL_MIN_10_EXP**|(-307)|最小十進位指數|
|**DBL_MIN_EXP**|(-1021)|最小二進位指數|
|**_DBL_RADIX**|2|指數基數|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|最小的正數偏低值|
|**FLT_DECIMAL_DIG**|9|十進位位數的進位精確度|
|**FLT_DIG**|6|十進位位數精確度|
|**FLT_EPSILON**|1.192092896e-07F|最小，因此 1.0 + **FLT_EPSILON** != 1.0|
|**FLT_HAS_SUBNORM**|1|類型支援偏低的 (異常) 數字|
|**FLT_MANT_DIG**|24|有效位數 (尾數) 中的位元數|
|**FLT_MAX**|3.402823466e+38F|最大值|
|**FLT_MAX_10_EXP**|38|最大十進位指數|
|**FLT_MAX_EXP**|128|最大二進位指數|
|**FLT_MIN**|1.175494351e-38F|最小的標準化正值|
|**FLT_MIN_10_EXP**|(-37)|最小十進位指數|
|**FLT_MIN_EXP**|(-125)|最小二進位指數|
|**FLT_RADIX**|2|指數基數|
|**FLT_TRUE_MIN**|1.401298464e-45F|最小的正數偏低值|
|**LDBL_DIG**|15|十進位位數精確度|
|**LDBL_EPSILON**|2.2204460492503131e-016|最小，因此 1.0 + **LDBL_EPSILON** != 1.0|
|**LDBL_HAS_SUBNORM**|1|類型支援偏低的 (異常) 數字|
|**LDBL_MANT_DIG**|53|有效位數 (尾數) 中的位元數|
|**LDBL_MAX**|1.7976931348623158e+308|最大值|
|**LDBL_MAX_10_EXP**|308|最大十進位指數|
|**LDBL_MAX_EXP**|1024|最大二進位指數|
|**LDBL_MIN**|2.2250738585072014e-308|最小的標準化正值|
|**LDBL_MIN_10_EXP**|(-307)|最小十進位指數|
|**LDBL_MIN_EXP**|(-1021)|最小二進位指數|
|**_LDBL_RADIX**|2|指數基數|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|最小的正數偏低值|
|**DECIMAL_DIG**|與 **DBL_DECIMAL_DIG** 相同|預設值 (double) 十進位位數的進位精確度|

## <a name="see-also"></a>另請參閱

[全域常數](../c-runtime-library/global-constants.md)
