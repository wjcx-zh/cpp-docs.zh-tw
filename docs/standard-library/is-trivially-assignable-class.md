---
title: "is_trivially_assignable 類別 | Microsoft Docs"
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
- is_trivially_assignable
- std.is_trivially_assignable
- std::is_trivially_assignable
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4b640307631b1407e5309adaa63b39e100839f91
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 類別
測試是否可將 `From` 類型的值透過極簡方式指派給 `To` 類型  
  
## <a name="syntax"></a>語法  
  
```
template <class To, class From>  
struct is_trivially_assignable;
```  
  
#### <a name="parameters"></a>參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## <a name="remarks"></a>備註  
 運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不需要任何非極簡作業。 `From` 和 `To` 兩者必須是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




