---
title: 整數限制
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: a113dd687e6f135af950f461e024b9fd9feaf1b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213381"
---
# <a name="integer-limits"></a>整數限制

**Microsoft 特定**

下表列出整數類型的限制。 當您包含標準標頭檔時，也會定義這些限制的預處理器宏 \<climits> 。

## <a name="limits-on-integer-constants"></a>整數常數的限制

| 持續性 | 意義 | 值 |
|--|--|--|
| `CHAR_BIT` | 不是位元欄位之最小變數中的位元數目。 | 8 |
| `SCHAR_MIN` | 類型變數的最小值 **`signed char`** 。 | -128 |
| `SCHAR_MAX` | 類型變數的最大值 **`signed char`** 。 | 127 |
| `UCHAR_MAX` | 類型變數的最大值 **`unsigned char`** 。 | 255 (0xff) |
| `CHAR_MIN` | 類型變數的最小值 **`char`** 。 | -128;如果使用選項，則為 0 **`/J`** |
| `CHAR_MAX` | 類型變數的最大值 **`char`** 。 | 127;255（如果 **`/J`** 使用選項） |
| `MB_LEN_MAX` | 多重字元常數中位元組數目的上限。 | 5 |
| `SHRT_MIN` | 類型變數的最小值 **`short`** 。 | -32768 |
| `SHRT_MAX` | 類型變數的最大值 **`short`** 。 | 32767 |
| `USHRT_MAX` | 類型變數的最大值 **`unsigned short`** 。 | 65535 (0xffff) |
| `INT_MIN` | 類型變數的最小值 **`int`** 。 | -2147483648 |
| `INT_MAX` | 類型變數的最大值 **`int`** 。 | 2147483647 |
| `UINT_MAX` | 類型變數的最大值 **`unsigned int`** 。 | 4294967295 (0xffffffff) |
| `LONG_MIN` | 類型變數的最小值 **`long`** 。 | -2147483648 |
| `LONG_MAX` | 類型變數的最大值 **`long`** 。 | 2147483647 |
| `ULONG_MAX` | 類型變數的最大值 **`unsigned long`** 。 | 4294967295 (0xffffffff) |
| `LLONG_MIN` | 類型變數的最小值**`long long`** | -9223372036854775808 |
| `LLONG_MAX` | 類型變數的最大值**`long long`** | 9223372036854775807 |
| `ULLONG_MAX` | 類型變數的最大值**`unsigned long long`** | 18446744073709551615 (0xffffffffffffffff) |

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

## <a name="see-also"></a>另請參閱

[浮動限制](../cpp/floating-limits.md)
