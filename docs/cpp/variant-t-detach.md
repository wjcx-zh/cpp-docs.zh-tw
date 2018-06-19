---
title: _variant_t::Detach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b53d6dc51117ffe9b82511c6084e36bc49873b88
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421937"
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Microsoft 特定的**  
  
 中斷連結封裝**VARIANT**物件與這個`_variant_t`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 封裝**VARIANT**。  
  
## <a name="remarks"></a>備註  
 擷取並傳回封裝**VARIANT**，然後清除這個`_variant_t`物件而不將其終結。 此成員函式會移除**VARIANT**來自封裝 （encapsulation） 和集合**VARTYPE**這個`_variant_t`物件`VT_EMPTY`。 您要釋放傳回**VARIANT**藉由呼叫[Vvalue](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)函式。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)