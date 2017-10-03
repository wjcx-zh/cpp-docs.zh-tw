---
title: "is_nothrow_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: f4e0b1cc873c5b83f7a307e98965ac4891153f60
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 類別
測試是否可將 `From` 類型的值指派給 `To` 類型，且該指派已知不會擲回。  
  
## <a name="syntax"></a>語法  
  
```
template <class To, class From>  
struct is_nothrow_assignable;
```  
  
#### <a name="parameters"></a>參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## <a name="remarks"></a>備註  
 運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不會擲回。 `From` 和 `To` 兩者必須是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




