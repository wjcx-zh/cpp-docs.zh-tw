---
title: 整數限制
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 75cd05e73aba2d2e82e8077e0a289d8b0fae7ec4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178220"
---
# <a name="integer-limits"></a>整數限制

**Microsoft 專屬**

下表列出整數類型的限制。 這些限制也會在標準標頭檔中定義 \<限制 .h >。

## <a name="limits-on-integer-constants"></a>整數常數的限制

|持續性|意義|值|
|--------------|-------------|-----------|
|CHAR_BIT|不是位元欄位之最小變數中的位元數目。|8|
|SCHAR_MIN|變數類型為 **signed char** 的最小值。|-128|
|SCHAR_MAX|變數類型為 **signed char** 的最大值。|127|
|UCHAR_MAX|類型為 **unsigned char** 之變數的最大值。|255 (0xff)|
|CHAR_MIN|類型為 **char** 之變數的最小值。|-128 (如果使用 /J 選項則為 0)|
|CHAR_MAX|類型為 **char** 之變數的最大值。|127 (如果使用 /J 選項則為 255)|
|MB_LEN_MAX|多重字元常數中位元組數目的上限。|5|
|SHRT_MIN|變數類型為 **short** 的最小值。|-32768|
|SHRT_MAX|變數類型為 **short** 的最大值。|32767|
|USHRT_MAX|變數類型為 **unsigned short** 的最大值。|65535 (0xffff)|
|INT_MIN|類型為 **int** 之變數的最小值。|-2147483648|
|INT_MAX|類型為 **int** 之變數的最大值。|2147483647|
|UINT_MAX|類型為 **unsigned int** 之變數的最大值。|4294967295 (0xffffffff)|
|LONG_MIN|變數類型為 **long** 的最小值。|-2147483648|
|LONG_MAX|變數類型為 **long** 的最大值。|2147483647|
|ULONG_MAX|類型為 **unsigned long** 之變數的最大值。|4294967295 (0xffffffff)|
|LLONG_MIN|**Long long**類型之變數的最小值|-9223372036854775808|
|LLONG_MAX|**Long long**類型之變數的最大值|9223372036854775807|
|ULLONG_MAX|不**帶正負號 long long**類型之變數的最大值|18446744073709551615 (0xffffffffffffffff)|

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[浮點數限制](../cpp/floating-limits.md)
