---
title: "is_move_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1003b77fcca3a5b0f6840f53d353c882e45a5ef3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ismoveassignable-class"></a>is_move_assignable 類別
測試是否可對類型進行移動指派。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct is_move_assignable;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果對類型的 rvalue 參考可以指派給對類型的參考，該類型即為可透過移動方式指派的類型。 類型述詞相當於 `is_assignable<T&, T&&>`。 可透過移動方式指派的類型包括可參考的純量類型和類別類型，這些類型具有編譯器所產生或使用者定義的移動指派運算子。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



