---
title: "浮點常數的限制 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 0ba0314abe9d70f25dc458abdbbf41f798fff263
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="limits-on-floating-point-constants"></a>浮點常數的限制
**Microsoft 特定的**  
  
 下表提供浮點常數值的限制。 標頭檔 FLOAT.H 會包含這項資訊。  
  
### <a name="limits-on-floating-point-constants"></a>浮點常數的限制  
  
|常數|意義|值|  
|--------------|-------------|-----------|  
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|位數 *q*，使得有 *q* 個小數位數的浮點數可以捨入為浮點表示 (反向亦然)，而不會失去精確度。|6<br />15<br />15|  
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|最小正數 *x*，使得 *x* + 1.0 不會等於 1.0|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|  
|**FLT_GUARD**||0|  
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|基數中以浮點數有效數字的 **FLT_RADIX** 指定的位數。 基數為 2，因此這些值會指定位元。|24<br />53<br />53|  
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|可顯示的最大浮點數。|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|  
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|最大整數，增加至該數字的這類 10 會是可顯示的浮點數。|38<br />308<br />308|  
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|最大整數，使得增加至該數字的 **FLT_RADIX** 會是可顯示的浮點數。|128<br />1024<br />1024|  
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|最小正值。|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|  
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|最小負整數，增加至該數字的這類 10 會是可顯示的浮點數。|-37<br />-307<br />-307|  
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|最小負整數，使得增加至該數字的 **FLT_RADIX** 會是可顯示的浮點數。|-125<br />-1021<br />-1021|  
|**FLT_NORMALIZE**||0|  
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|指數表示的基數。|2<br />2<br />2|  
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|浮點加法的捨入模式。|1 (接近)<br />1 (接近)<br />1 (接近)|  
  
 請注意，上表中的資訊在未來實作中可能有所不同。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 浮點常數](../c-language/c-floating-point-constants.md)
