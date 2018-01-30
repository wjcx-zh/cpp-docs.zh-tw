---
title: "整數限制 |Microsoft 文件"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5fc79f225d340777751ca513c0fb47dd33e17ad
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="integer-limits"></a>整數限制

**Microsoft 特定的**

下表列出整數類型的限制。 標準標頭檔 < limits.h > 中，也會定義這些限制。

## <a name="limits-on-integer-constants"></a>整數常數的限制

|常數|意義|值|
|--------------|-------------|-----------|
|**CHAR_BIT**|不是位元欄位之最小變數中的位元數目。|8|
|**SCHAR_MIN**|變數類型為 **signed char** 的最小值。|-128|
|**SCHAR_MAX**|變數類型為 **signed char** 的最大值。|127|
|**UCHAR_MAX**|最大值類型的變數**unsigned char**。|255 (0xff)|
|**CHAR_MIN**|最小值類型的變數**char**。|-128 (如果使用 /J 選項則為 0)|
|**CHAR_MAX**|最大值類型的變數**char**。|127 (如果使用 /J 選項則為 255)|
|**MB_LEN_MAX**|多重字元常數中位元組數目的上限。|5|
|**SHRT_MIN**|變數類型為 **short** 的最小值。|-32768|
|**SHRT_MAX**|變數類型為 **short** 的最大值。|32767|
|**USHRT_MAX**|變數類型為 **unsigned short** 的最大值。|65535 (0xffff)|
|**INT_MIN**|最小值類型的變數**int**。|-2147483648|
|**INT_MAX**|最大值類型的變數**int**。|2147483647|
|**UINT_MAX**|最大值類型的變數**不帶正負號的 int**。|4294967295 (0xffffffff)|
|**LONG_MIN**|變數類型為 **long** 的最小值。|-2147483648|
|**LONG_MAX**|變數類型為 **long** 的最大值。|2147483647|
|**ULONG_MAX**|最大值類型的變數**不帶正負號長**。|4294967295 (0xffffffff)|
|**LLONG_MIN**|最小值類型的變數**long long**|-9223372036854775808|
|**LLONG_MAX**|最大值類型的變數**long long**|9223372036854775807|
|**ULLONG_MAX**|最大值類型的變數**unsigned long long**|18446744073709551615 (0xffffffffffffffff)|

如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。

**結束 Microsoft 特定的**

## <a name="see-also"></a>請參閱

[浮點數限制](../cpp/floating-limits.md)  
