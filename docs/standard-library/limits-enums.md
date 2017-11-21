---
title: "&lt;limits&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 1b69623aa9eccfca57667d4f33546512799b172f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 列舉
|||  
|-|-|  
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|  
  
##  <a name="float_denorm_style"></a>  float_denorm_style 列舉  
 此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：  
  
```
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```  
  
### <a name="return-value"></a>傳回值  
 此列舉會傳回：  
  
- **denorm_indeterminate**，表示在轉譯階段無法判斷反正規化形式是否存在。  
  
- **denorm_absent**，表示反正規化形式不存在。  
  
- **denorm_present**，表示反正規化形式存在。  
  
### <a name="example"></a>範例  
  如需可存取此列舉之值的範例，請參閱 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm)。  
  
##  <a name="float_round_style"></a>  float_round_style 列舉  
 此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。  
  
```
enum float_round_style {    
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```  
  
### <a name="return-value"></a>傳回值  
 此列舉會傳回：  
  
- **round_indeterminate**，表示無法判斷捨入方法。  
  
- **round_toward_zero**，表示捨入至零。  
  
- **round_to_nearest**，表示捨入至最接近的整數。  
  
- **round_toward_infinity**，表示以背離於零的方式捨入。  
  
- **round_toward_neg_infinity**，表示捨入至較小的負數。  
  
### <a name="example"></a>範例  
  如需可存取此列舉之值的範例，請參閱 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style)。  
  
## <a name="see-also"></a>另請參閱  
 [\<limits>](../standard-library/limits.md)



