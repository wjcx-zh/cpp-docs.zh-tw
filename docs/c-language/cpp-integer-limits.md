---
title: "C++ 整數限制 | Microsoft Docs"
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
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c1d45ba449173c5cc2bf3fbed663a7d987c22e1c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="c-integer-limits"></a>C++ 整數限制
**Microsoft 特定的**  
  
 下表列出整數類型的限制。 這些限制在標準標頭檔 LIMITS.H 中定義。 Microsoft C 也允許使用可調整大小的整數變數，即大小為 8、16 或 32 位元的整數類型。 如需可調整大小整數的詳細資訊，請參閱[可調整大小的整數類型](../c-language/c-sized-integer-types.md)。  
  
### <a name="limits-on-integer-constants"></a>整數常數的限制  
  
|**常數**|意義|值|  
|------------------|-------------|-----------|  
|**CHAR_BIT**|不是位元欄位之最小變數中的位元數目。|8|  
|**SCHAR_MIN**|變數類型為 **signed char** 的最小值。|-128|  
|**SCHAR_MAX**|變數類型為 **signed char** 的最大值。|127|  
|**UCHAR_MAX**|變數類型為 `unsigned char` 的最大值。|255 (0xff)|  
|**CHAR_MIN**|變數類型為 `char` 的最小值。|-128 (如果使用 /J 選項則為 0)|  
|**CHAR_MAX**|變數類型為 `char` 的最大值。|127 (如果使用 /J 選項則為 255)|  
|**MB_LEN_MAX**|多重字元常數中位元組數目的上限。|5|  
|**SHRT_MIN**|變數類型為 **short** 的最小值。|-32768|  
|**SHRT_MAX**|變數類型為 **short** 的最大值。|32767|  
|**USHRT_MAX**|變數類型為 **unsigned short** 的最大值。|65535 (0xffff)|  
|**INT_MIN**|變數類型為 `int` 的最小值。|-2147483647 - 1|  
|**INT_MAX**|變數類型為 `int` 的最大值。|2147483647|  
|**UINT_MAX**|變數類型為 `unsigned int` 的最大值。|4294967295 (0xffffffff)|  
|**LONG_MIN**|變數類型為 **long** 的最小值。|-2147483647 - 1|  
|**LONG_MAX**|變數類型為 **long** 的最大值。|2147483647|  
|**ULONG_MAX**|變數類型為 `unsigned long` 的最大值。|4294967295 (0xffffffff)|  
  
 如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 整數常數](../c-language/c-integer-constants.md)
