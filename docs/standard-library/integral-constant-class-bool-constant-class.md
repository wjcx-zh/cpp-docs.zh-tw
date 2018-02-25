---
title: "integral_constant 類別、bool_constant 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eeb576ec7f845efaeca2a0b7f6a55503c7b298da
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant 類別、bool_constant 類別
從類型及值建立整數常數。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, T v>
struct integral_constant {  
   static constexpr T value = v;  
   typedef T value_type;  
   typedef integral_constant<T, v> type;  
   constexpr operator value_type() const noexcept;  
   constexpr value_type operator()() const noexcept;  
   };  
```
  
### <a name="parameters"></a>參數  
*T*  
常數的類型。  
  
*v*  
常數的值。  
  
## <a name="remarks"></a>備註  
以整數類型 *T* 和該類型的值 *v* 將 `integral_constant` 範本類別特製化時，此類別會代表持有該整數類型之常數並具有指定值的物件。 名為 `type` 的成員是所產生範本特製化類型的別名，而 `value` 成員則持有用來建立特製化的值 *v*。  
  
`bool_constant` 範本類別是使用 `bool` 作為 *T* 引數之 `integral_constant` 的明確部分特製化。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant<int, 5> == 5  
integral_constant<bool, false> == false  
```  
  
## <a name="requirements"></a>需求  

**標頭：**\<type_traits>
  
**命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [false_type](../standard-library/type-traits-typedefs.md#false_type)   
 [true_type](../standard-library/type-traits-typedefs.md#true_type)

