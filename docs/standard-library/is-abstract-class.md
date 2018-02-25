---
title: "is_abstract 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_abstract
dev_langs:
- C++
helpviewer_keywords:
- is_abstract class
- is_abstract
ms.assetid: 8867f660-3434-404c-ba90-c26607a5e0d2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbce676b318534ffec8fded963d5649245b1172f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="isabstract-class"></a>is_abstract 類別
測試類型是否為抽象類別。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct is_abstract;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果 `Ty` 類型是具有至少一個純虛擬函式的類別，則 predicate 類型的執行個體為 true，否則為 false。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__is_abstract.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct abstract   
    {   
    virtual int val() = 0;   
    };   
  
int main()   
    {   
    std::cout << "is_abstract<trivial> == " << std::boolalpha   
        << std::is_abstract<trivial>::value << std::endl;   
    std::cout << "is_abstract<abstract> == " << std::boolalpha   
        << std::is_abstract<abstract>::value << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
is_abstract<trivial> == false  
is_abstract<abstract> == true  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_polymorphic 類別](../standard-library/is-polymorphic-class.md)
