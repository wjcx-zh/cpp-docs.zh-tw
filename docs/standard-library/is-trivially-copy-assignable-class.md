---
title: "is_trivially_copy_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 0f8aad09e3ed083b9ffdd2199c9a9ab6462b840b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 類別
測試類型是否有 trivial 複製指派運算子。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct is_trivially_copy_assignable;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果 `T` 類型是具有 trivial 複製指派運算子的類別，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
 類別 `T` 的指派建構函式如果符合下列條件，便是極簡指派建構函式：提供此指派建構函式時是以隱含方式提供、類別 `T` 沒有任何虛擬函式、類別 `T` 沒有任何虛擬基底、類別類型之所有非靜態資料成員的類別都具有極簡指派運算子，以及類別之陣列類型的所有非靜態資料成員的類別都具有極簡指派運算子。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)



