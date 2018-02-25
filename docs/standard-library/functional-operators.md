---
title: "&lt;functional&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf3e013ade27636b8cba3e2eeb5473440f9e14eb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; 運算子
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a> operator==  
 測試可呼叫的物件是否是空的。  
  
```  
template <class Fty>  
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator==(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>參數  
 `Fty`  
 要包裝的函式類型。  
  
 `f`  
 函式物件  
  
 `npc`  
 Null 指標。  
  
### <a name="remarks"></a>備註  
 運算子同時使用是 `function` 物件之參考的引數以及是 Null 指標常數的引數。 兩者都只有在 `function` 物件為空時，才會傳回 true。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__functional__operator_eq.cpp
// compile with: /EHsc   
#include <functional>   
#include <iostream>   

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
  
```  
  
```Output  
empty == true  
empty == false  
```  
  
##  <a name="op_neq"></a> operator!=  
 測試可呼叫的物件是否不是空的。  
  
```  
template <class Fty>  
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>參數  
 `Fty`  
 要包裝的函式類型。  
  
 `f`  
 函式物件  
  
 `npc`  
 Null 指標。  
  
### <a name="remarks"></a>備註  
 運算子同時使用是 `function` 物件之參考的引數以及是 Null 指標常數的引數。 兩者都只有在 `function` 物件不是空的時，才會傳回 true。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__functional__operator_ne.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0;   
    std::cout << std::boolalpha << "not empty == "   
        << (fn0 != 0) << std::endl;   
  
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "not empty == "   
        << (fn1 != 0) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
not empty == false  
not empty == true  
```  
  
## <a name="see-also"></a>請參閱  
 [\<functional>](../standard-library/functional.md)

