---
title: "_variant_t 關係運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d8bcf9550e3e3f8af1836aa3f6e8747089837142
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="variantt-relational-operators"></a>_variant_t 關係運算子
**Microsoft 特定的**  
  
 比較兩個 `_variant_t` 物件是否相等或不等。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### <a name="parameters"></a>參數  
 *varSrc*  
 A **VARIANT**與比較`_variant_t`物件。  
  
 `pSrc`  
 指標**VARIANT**與比較`_variant_t`物件。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**比較保留，如果**false**如果不是。  
  
## <a name="remarks"></a>備註  
 比較`_variant_t`物件**VARIANT**、 測試是否相等或不等比較。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)
