---
title: "is_move_constructible 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_move_constructible
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
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
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 91f451ef7ec496791d6a1a8d28965dbb5b684584
ms.lasthandoff: 02/24/2017

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
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




