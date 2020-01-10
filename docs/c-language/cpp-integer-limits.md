---
title: C 和C++整數限制
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778381"
---
# <a name="c-and-c-integer-limits"></a>C 和C++整數限制

**Microsoft 專屬**

下表列出 C 和C++中整數類型的限制。 這些限制是在 C 標準標頭檔 `<limits.h>` 中定義。 C++標準程式庫標頭 `<limits>` 包括 `<climits>`，其中包括 `<limits.h>`。

Microsoft C 也允許宣告大小的整數變數，這是大小為 8-、16-、32或64位的整數類型。 如需有關 C 中大小整數的詳細資訊，請參閱重設[大小的整數類型](../c-language/c-sized-integer-types.md)。

## <a name="limits-on-integer-constants"></a>整數常數的限制

|**常數**|意義|值|
|------------------|-------------|-----------|
|**CHAR_BIT**|不是位元欄位之最小變數中的位元數目。|8|
|**SCHAR_MIN**|變數類型為 **signed char** 的最小值。|-128|
|**SCHAR_MAX**|變數類型為 **signed char** 的最大值。|127|
|**UCHAR_MAX**|類型為 **unsigned char** 之變數的最大值。|255 (0xff)|
|**CHAR_MIN**|類型為 **char** 之變數的最小值。|-128 (如果使用 /J 選項則為 0)|
|**CHAR_MAX**|類型為 **char** 之變數的最大值。|127 (如果使用 /J 選項則為 255)|
|**MB_LEN_MAX**|多重字元常數中位元組數目的上限。|5|
|**SHRT_MIN**|變數類型為 **short** 的最小值。|-32768|
|**SHRT_MAX**|變數類型為 **short** 的最大值。|32767|
|**USHRT_MAX**|變數類型為 **unsigned short** 的最大值。|65535 (0xffff)|
|**INT_MIN**|類型為 **int** 之變數的最小值。|-2147483647 - 1|
|**INT_MAX**|類型為 **int** 之變數的最大值。|2147483647|
|**UINT_MAX**|類型為 **unsigned int** 之變數的最大值。|4294967295 (0xffffffff)|
|**LONG_MIN**|變數類型為 **long** 的最小值。|-2147483647 - 1|
|**LONG_MAX**|變數類型為 **long** 的最大值。|2147483647|
|**ULONG_MAX**|類型為 **unsigned long** 之變數的最大值。|4294967295 (0xffffffff)|
|**LLONG_MIN**|**Long long**類型之變數的最小值。|-9223372036854775807-1|
|**LLONG_MAX**|**Long long**類型之變數的最大值。|9,223,372,036,854,775,807|
|**ULLONG_MAX**|不**帶正負號 long long**類型之變數的最大值。|18446744073709551615（0xffffffffffffffff）|

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[C 整數常數](../c-language/c-integer-constants.md)
