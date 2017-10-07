---
title: "is_nothrow_constructible 類別 | Microsoft Docs"
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
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 2ff20de3656cde44d79936c6bf1374134eb95068
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 類別
測試當使用指定的引數類型時，類型是否是可建構的類型且已知不會擲回。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class... Args>  
struct is_nothrow_constructible;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
 `Args`  
 要在 `T` 的建構函式中相符的引數類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是可藉由使用 `Args` 中的引數類型來建構的類型，且編譯器已知該建構函式不會擲回，類型述詞執行個體的值就會是 true；否則會是 false。 如果變數定義 `T t(std::declval<Args>()...);` 格式正確，類型 `T` 便是可建構的類型。 `T` 和 `Args` 中的所有類型必須都是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




