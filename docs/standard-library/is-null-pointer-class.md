---
title: "is_null_pointer 類別 | Microsoft Docs"
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
- type_traits/std::is_null_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2fc4b728008bc15d1e63093a4332a7d10d4fcc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="isnullpointer-class"></a>is_null_pointer 類別
測試類型是否為 std::nullptr_t。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct is_null_pointer;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是 `std::nullptr_t`，類型述詞執行個體的值就會是 true，否則會是 false。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



