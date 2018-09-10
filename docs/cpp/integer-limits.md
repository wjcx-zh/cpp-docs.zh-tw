---
title: 整數限制 |Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f49e224520751e08ba6aa7e37932314e11ef8a5
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315181"
---
# <a name="integer-limits"></a>整數限制

**Microsoft 專屬**

下表列出整數類型的限制。 標準標頭檔中也會定義這些限制\<limits.h >。

## <a name="limits-on-integer-constants"></a>整數常數的限制

|常數|意義|值|
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
|LLONG_MIN|最小值型別的變數**long long**|-9223372036854775808|
|LLONG_MAX|最大值類型的變數**long long**|9223372036854775807|
|ULLONG_MAX|最大值類型的變數**unsigned long long**|18446744073709551615 (0xffffffffffffffff)|

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[浮點數限制](../cpp/floating-limits.md)