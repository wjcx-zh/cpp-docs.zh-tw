---
title: "is_error_condition_enum 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::is_error_condition_enum
- std.is_error_condition_enum
- is_error_condition_enum
- system_error/std::is_error_condition_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 316e375554d80bfa58dfba537e5c36a881028a20
ms.lasthandoff: 02/24/2017

---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum 類別
代表針對 [error_condition](../standard-library/error-condition-class.md) 列舉進行測試的類型述詞。  
  
## <a name="syntax"></a>語法  
  
```
template <_Enum>
class is_error_condition_enum;
```  
  
## <a name="remarks"></a>備註  
 如果類型 `_Enum` 是適合在 `error_condition` 類型的物件中儲存的列舉值，此[類型述詞](../standard-library/type-traits.md)執行個體的值就會是 true。  
  
 允許針對使用者定義的類型將特製化新增到此類型。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<system_error>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)




