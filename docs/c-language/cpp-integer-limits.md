---
title: C 和 c + + 整數限制
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 1484b43719696578be437909351e24a550ec9869
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217112"
---
# <a name="c-and-c-integer-limits"></a>C 和 c + + 整數限制

**Microsoft 特定的**

下表列出 C 和 c + + 中的整數類型限制。 這些限制會定義在 C 標準標頭檔中 `<limits.h>` 。 C + + 標準程式庫標頭 `<limits>` 包含 `<climits>` ，其中包含 `<limits.h>` 。

Microsoft C 也允許宣告大小的整數變數，這是大小為 8-、16-、32或64位的整數類型。 如需有關 C 中大小整數的詳細資訊，請參閱重設[大小的整數類型](../c-language/c-sized-integer-types.md)。

## <a name="limits-on-integer-constants"></a>整數常數的限制

|**常數**|意義|值|
|------------------|-------------|-----------|
|**CHAR_BIT**|不是位元欄位之最小變數中的位元數目。|8|
|**SCHAR_MIN**|類型變數的最小值 **`signed char`** 。|-128|
|**SCHAR_MAX**|類型變數的最大值 **`signed char`** 。|127|
|**UCHAR_MAX**|類型變數的最大值 **`unsigned char`** 。|255 (0xff)|
|**CHAR_MIN**|類型變數的最小值 **`char`** 。|-128 (如果使用 /J 選項則為 0)|
|**CHAR_MAX**|類型變數的最大值 **`char`** 。|127 (如果使用 /J 選項則為 255)|
|**MB_LEN_MAX**|多重字元常數中位元組數目的上限。|5|
|**SHRT_MIN**|類型變數的最小值 **`short`** 。|-32768|
|**SHRT_MAX**|類型變數的最大值 **`short`** 。|32767|
|**USHRT_MAX**|類型變數的最大值 **`unsigned short`** 。|65535 (0xffff)|
|**INT_MIN**|類型變數的最小值 **`int`** 。|-2147483647 - 1|
|**INT_MAX**|類型變數的最大值 **`int`** 。|2147483647|
|**UINT_MAX**|類型變數的最大值 **`unsigned int`** 。|4294967295 (0xffffffff)|
|**LONG_MIN**|類型變數的最小值 **`long`** 。|-2147483647 - 1|
|**LONG_MAX**|類型變數的最大值 **`long`** 。|2147483647|
|**ULONG_MAX**|類型變數的最大值 **`unsigned long`** 。|4294967295 (0xffffffff)|
|**LLONG_MIN**|類型變數的最小值 **`long long`** 。|-9223372036854775807-1|
|**LLONG_MAX**|類型變數的最大值 **`long long`** 。|9,223,372,036,854,775,807|
|**ULLONG_MAX**|類型變數的最大值 **`unsigned long long`** 。|18446744073709551615（0xffffffffffffffff）|

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 整數常數](../c-language/c-integer-constants.md)
