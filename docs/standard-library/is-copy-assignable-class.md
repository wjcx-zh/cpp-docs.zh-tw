---
title: "is_copy_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb6dfc91d47a0b6afb5f0918d036d1b07a5e693f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="iscopyassignable-class"></a>is_copy_assignable 類別
測試類型是否可以在指派上複製。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct is_copy_assignable;
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果 `Ty` 類型是具有複製指派運算子的類別，則 predicate 類型的執行個體保留 true，否則保留 false。 相當於 is_assignable\<Ty&, const Ty&>。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



