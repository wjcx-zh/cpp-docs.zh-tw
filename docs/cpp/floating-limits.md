---
title: 浮點數限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a111d2ea3e8e5503754b0d9c0c1a4f69170a41c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401755"
---
# <a name="floating-limits"></a>浮點數限制
**Microsoft 專屬**  
  
 下表列出浮點常數值的限制。 標準標頭檔中也會定義這些限制\<float.h >。  
  
### <a name="limits-on-floating-point-constants"></a>浮點常數的限制  
  
|常數|意義|值|  
|--------------|-------------|-----------|  
|FLT_DIG DBL_DIG LDBL_DIG|位數 q，使得有 q 個小數位數的浮點數可以捨入為浮點表示 (反向亦然)，而不會失去精確度。|6 15 15|  
|FLT_EPSILON DBL_EPSILON LDBL_EPSILON|最小正數 x，使得 x + 1.0 不會等於 1.0。|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG DBL_MANT_DIG LDBL_MANT_DIG|基數中以浮點數有效數字的 FLT_RADIX 指定的位數。 基數為 2;因此這些值會指定位元。|24 53 53|  
|FLT_MAX DBL_MAX LDBL_MAX|最大可顯示的浮點數。|3.402823466e+38F 1.7976931348623158e+308 1.7976931348623158e+308|  
|FLT_MAX_10_EXP DBL_MAX_10_EXP LDBL_MAX_10_EXP|最大整數這類 10 會增加至該數字會是可顯示的浮點數。|38 308 308|  
|FLT_MAX_EXP DBL_MAX_EXP LDBL_MAX_EXP|最大整數，使得增加至該數字的 FLT_RADIX 會是可顯示的浮點數。|128 1024 1024|  
|FLT_MIN DBL_MIN LDBL_MIN|最小正值。|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP DBL_MIN_10_EXP LDBL_MIN_10_EXP|最小負整數這類 10 會增加至該數字會是可顯示的浮點數。|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP DBL_MIN_EXP LDBL_MIN_EXP|最小負整數，使得增加至該數字的 FLT_RADIX 會是可顯示的浮點數。|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX _DBL_RADIX _LDBL_RADIX|指數表示的基數。|2 2 2|  
|FLT_ROUNDS _DBL_ROUNDS _LDBL_ROUNDS|浮點加法的捨入模式。|1 (near) 1 (near) 1 (near)|  
  
> [!NOTE]
>  上表中的資訊在未來的產品版本中可能有所不同。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [整數限制](../cpp/integer-limits.md)