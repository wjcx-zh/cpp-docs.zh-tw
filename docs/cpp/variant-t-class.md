---
title: "_variant_t 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t
dev_langs: C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57a4d7e4019e742ff8adc50bb78a926dff34d55a
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="variantt-class"></a>_variant_t 類別
**Microsoft 特定的**  
  
 A`_variant_t`物件封裝`VARIANT`資料型別。 管理資源配置和解除配置的類別並函式呼叫**VariantInit**和**Vvalue**依適當情況。  
  
### <a name="construction"></a>建構  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|建構 `_variant_t` 物件。|  
  
### <a name="operations"></a>作業  
  
|||  
|-|-|  
|[Attach](../cpp/variant-t-attach.md)|附加**VARIANT**物件插入`_variant_t`物件。|  
|[清除](../cpp/variant-t-clear.md)|清除封裝**VARIANT**物件。|  
|[ChangeType](../cpp/variant-t-changetype.md)|類型變更`_variant_t`物件指定**VARTYPE**。|  
|[Detach](../cpp/variant-t-detach.md)|中斷連結封裝**VARIANT**物件與這個`_variant_t`物件。|  
|[SetString](../cpp/variant-t-setstring.md)|將字串指派給這個 `_variant_t` 物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](../cpp/variant-t-operator-equal.md)|將新值指派給現有的 `_variant_t` 物件。|  
|[operator ==, !=](../cpp/variant-t-relational-operators.md)|比較兩個 `_variant_t` 物件是否相等或不等。|  
|[擷取器](../cpp/variant-t-extractors.md)|從封裝擷取資料**VARIANT**物件。|  
  
**結束 Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** \<comutil.h >  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)