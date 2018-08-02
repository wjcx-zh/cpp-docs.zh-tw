---
title: _variant_t::Detach |Microsoft Docs
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
ms.openlocfilehash: 895df401ab10ae85641fd2eed9f7a9654916f33f
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465222"
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Microsoft 專屬**  
  
 中斷連結封裝`VARIANT`物件，這個`_variant_t`物件。  
  
## <a name="syntax"></a>語法  
  
```  
VARIANT Detach( );  
```  
  
## <a name="return-value"></a>傳回值  
 封裝`VARIANT`。  
  
## <a name="remarks"></a>備註  
 擷取並傳回封裝`VARIANT`，然後清除這個`_variant_t`而不會終結它的物件。 此成員函式移除`VARIANT`來自封裝和集合`VARTYPE`這個`_variant_t`物件設為 VT_EMPTY。 它可以決定是否要釋放傳回`VARIANT`藉由呼叫[VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835)函式。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)