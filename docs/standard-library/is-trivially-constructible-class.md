---
title: "is_trivially_constructible 類別 | Microsoft Docs"
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
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
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
ms.openlocfilehash: 109e119100a3cb561159cca9bce95f793922e58d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 類別
測試類型在使用指定引數類型的情況下，是否是可透過極簡方式建構的類型。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class... Args>  
struct is_trivially_constructible;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
 `Args`  
 要在 `T` 的建構函式中相符的引數類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是可藉由使用 `Args` 中的引數類型透過極簡方式建構的類型，類型述詞執行個體的值就會是 true，否則會是 false。 如果變數定義 `T t(std::declval<Args>()...);` 格式正確，且已知不會呼叫任何非極簡作業，類型 `T` 便是可透過極簡方式建構的類型。 `T` 和 `Args` 中的所有類型必須都是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




