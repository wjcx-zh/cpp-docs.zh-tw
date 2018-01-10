---
title: "is_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_assignable
dev_langs: C++
helpviewer_keywords: is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba99c19328b576900b1c269c24949baa832c8be7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="isassignable-class"></a>is_assignable 類別
測試是否可將 `From` 類型的值指派給 `To` 類型。  
  
## <a name="syntax"></a>語法  
  
```
template <class To, class From>  
struct is_assignable;
```  
  
#### <a name="parameters"></a>參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## <a name="remarks"></a>備註  
 未評估的運算式 `declval<To>() = declval<From>()` 必須格式正確。 `From` 和 `To` 兩者必須是完整類型 `void`，或是界限未知的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)



