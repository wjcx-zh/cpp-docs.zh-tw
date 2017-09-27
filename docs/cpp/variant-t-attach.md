---
title: "_variant_t::Attach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
- VARIANT object, attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 33e21d3bea71c80b8b60df222682fda560fbce9c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)
