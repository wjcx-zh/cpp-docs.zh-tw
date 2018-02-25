---
title: "is_member_pointer 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_member_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_member_pointer class
- is_member_pointer
ms.assetid: da07ff4e-9ee0-4baa-ad93-1741f10913d1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3acdc4deb52df68059a1cc38660e459dcf656234
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ismemberpointer-class"></a>is_member_pointer 類別
測試類型是否是成員的指標。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct is_member_pointer;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 是成員函式的指標或成員物件的指標，或是它們其中一個的 `cv-qualified` 形式，類別述詞執行個體的值就會是 true，否則會是 false。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__is_member_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct functional   
    {   
    int f();   
    };   
  
int main()   
    {   
    std::cout << "is_member_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_member_pointer<trivial *> == false  
is_member_pointer<int trivial::*> == true  
is_member_pointer<int (functional::*)()> == true  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_member_function_pointer 類別](../standard-library/is-member-function-pointer-class.md)   
 [is_member_object_pointer 類別](../standard-library/is-member-object-pointer-class.md)   
 [is_pointer 類別](../standard-library/is-pointer-class.md)
