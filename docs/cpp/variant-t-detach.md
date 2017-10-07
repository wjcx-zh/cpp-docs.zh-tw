---
title: "_variant_t::Detach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 402d8bfeb6aea45460124bdeaaa8b3ee485df622
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)
