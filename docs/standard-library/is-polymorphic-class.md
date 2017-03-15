---
title: "is_polymorphic 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_polymorphic
- std::is_polymorphic
- type_traits/std::is_polymorphic
dev_langs:
- C++
helpviewer_keywords:
- is_polymorphic class
- is_polymorphic
ms.assetid: 4e1704db-d6f9-4154-a100-0ba02a373f20
caps.latest.revision: 19
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
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: bf02c7042b7b2a2535ab9d81116d4d97b557c21b
ms.lasthandoff: 02/24/2017

---
# <a name="ispolymorphic-class"></a>is_polymorphic 類別
測試類型是否有虛擬函式。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct is_polymorphic;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 是一個宣告或繼承虛擬函式的類別，則 predicate 類型的執行個體為 true，否則為 false。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__is_polymorphic.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    virtual ~throws()   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_polymorphic<trivial> == " << std::boolalpha   
        << std::is_polymorphic<trivial>::value << std::endl;   
    std::cout << "is_polymorphic<throws> == " << std::boolalpha   
        << std::is_polymorphic<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_polymorphic<trivial> == false  
is_polymorphic<throws> == true  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_abstract 類別](../standard-library/is-abstract-class.md)

