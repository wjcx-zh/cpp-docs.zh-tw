---
title: "is_signed 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_signed
- std::is_signed
- type_traits/std::is_signed
dev_langs:
- C++
helpviewer_keywords:
- is_signed class
- is_signed
ms.assetid: 20ae44d9-22ad-4fbd-b26a-f18c62689451
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
ms.openlocfilehash: e42e2f5ee1ffe76ffddb89b841c87a9e30e27bc3
ms.lasthandoff: 02/24/2017

---
# <a name="issigned-class"></a>is_signed 類別
測試類型是否為帶正負號的整數。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct is_signed;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果 `Ty` 類型是帶正負號的整數類型或 `cv-qualified` 帶正負號的整數類型，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__is_signed.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_signed<trivial> == " << std::boolalpha   
        << std::is_signed<trivial>::value << std::endl;   
    std::cout << "is_signed<int> == " << std::boolalpha   
        << std::is_signed<int>::value << std::endl;   
    std::cout << "is_signed<unsigned int> == " << std::boolalpha   
        << std::is_signed<unsigned int>::value << std::endl;   
    std::cout << "is_signed<float> == " << std::boolalpha   
        << std::is_signed<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_signed<trivial> == false  
is_signed<int> == true  
is_signed<unsigned int> == false  
is_signed<float> == false  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_unsigned 類別](../standard-library/is-unsigned-class.md)

