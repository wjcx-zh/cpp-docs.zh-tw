---
title: "is_trivially_move_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_trivially_move_assignable
- std.is_trivially_move_assignable
- std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 11
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
ms.openlocfilehash: b9d94304c6fbbd925ac3b670dc7665402b521dfd
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 類別
測試類型是否有 trivial 移動指派運算子。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct is_trivially_move_assignable;
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果 `Ty` 類型是具有 trivial 移動指派運算子的類別，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
 在下列情況下，類別 `Ty` 的移動指派運算子是 trivial：  
  
 它會隱含地提供  
  
 類別 `Ty` 沒有虛擬函式  
  
 類別 `Ty` 沒有虛擬基底  
  
 類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子  
  
 類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




