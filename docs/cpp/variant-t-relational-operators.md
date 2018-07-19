---
title: _variant_t 關係運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08d7f5c7c244d242c3d1dd7af7d2c2af017bcc78
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942843"
---
# <a name="variantt-relational-operators"></a>_variant_t 關係運算子
**Microsoft 專屬**  
  
 比較兩個 `_variant_t` 物件是否相等或不等。  
  
## <a name="syntax"></a>語法  
  
```  
  
bool operator==(  
   const VARIANT& varSrc) const;  
bool operator==(  
   const VARIANT* pSrc) const;  
bool operator!=(  
   const VARIANT& varSrc) const;  
bool operator!=(  
   const VARIANT* pSrc) const;  
```  
  
#### <a name="parameters"></a>參數  
 *varSrc*  
 A`VARIANT`要與比較`_variant_t`物件。  
  
 *pSrc*  
 指標`VARIANT`要與比較`_variant_t`物件。  
  
## <a name="return-value"></a>傳回值  
 傳回**真**成立，如果**false**如果不是。  
  
## <a name="remarks"></a>備註  
 比較`_variant_t`物件`VARIANT`、 測試是否相等或不等比較。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)