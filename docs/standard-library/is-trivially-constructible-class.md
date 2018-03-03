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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a01ee89c1bb07ab0ca3c9c54161b7d9a3097be3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



