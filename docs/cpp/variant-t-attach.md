---
title: "_variant_t::Attach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs: C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: effeaaaf3f8df9eb100d5e92e760eb439a865552
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="varianttattach"></a>_variant_t::Attach
**Microsoft 特定的**  
  
 附加**VARIANT**物件插入`_variant_t`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### <a name="parameters"></a>參數  
 *varSrc*  
 A **VARIANT**物件附加至這個`_variant_t`物件。  
  
## <a name="remarks"></a>備註  
 取得擁有權**VARIANT**透過封裝方式。 此成員函式會釋放所有現有的封裝**VARIANT**，然後複製提供**VARIANT**，並設定其**VARTYPE**至`VT_EMPTY`以確定其只有由釋放資源`_variant_t`解構函式。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)