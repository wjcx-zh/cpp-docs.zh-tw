---
title: "is_constructible 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_constructible
dev_langs: C++
helpviewer_keywords: is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2d2127ec8f007dbf301fca7e01a59a7ef462cd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="isconstructible-class"></a>is_constructible 類別
測試當使用指定的引數類型時，類型是否是可建構的類型。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class... Args>  
struct is_constructible;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
 `Args`  
 要在 `T` 的建構函式中相符的引數類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是可藉由使用 `Args` 中的引數類型來建構的類型，類型述詞執行個體的值就會是 true，否則會是 false。 如果變數定義 `T t(std::declval<Args>()...);` 格式正確，類型 `T` 便是可建構的類型。 `T` 和 `Args` 中的所有類型必須都是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



