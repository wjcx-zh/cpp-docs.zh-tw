---
title: "is_move_constructible 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15c1fb9b3b4e3dc27b887ac70005be55813399a7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 類別
測試類型是否具有移動建構函式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
struct is_move_constructible;
```  
  
#### <a name="parameters"></a>參數  
 T  
 要評估的類型  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是可藉由使用移動作業來建構的類型，類型述詞就會評估為 true。 這個述詞相當於 `is_constructible<T, T&&>`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



