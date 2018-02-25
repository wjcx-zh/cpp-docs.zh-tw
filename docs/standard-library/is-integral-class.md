---
title: "is_integral 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_integral
dev_langs:
- C++
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 992726f3b1d94b0ed4065c3fc2bb8bf54497a36b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="isintegral-class"></a>is_integral 類別
測試類型是否為整數。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct is_integral;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 是其中一個整數類型，或其中一個整數類型的 `cv-qualified` 形式，則類型述詞的執行個體為 true，否則為 false。  
  
 整數類型是下列其中之一：`bool`、`char`、`unsigned char`、`signed char`、`wchar_t`、`short`、`unsigned short`、`int`、`unsigned int`、`long` 和 `unsigned long`。 此外，在使用提供整數的編譯器時，整數類型可以是 `long long`、`unsigned long long`、`__int64` 和 `unsigned __int64` 的其中之一。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__is_integral.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_integral<trivial> == " << std::boolalpha   
        << std::is_integral<trivial>::value << std::endl;   
    std::cout << "is_integral<int> == " << std::boolalpha   
        << std::is_integral<int>::value << std::endl;   
    std::cout << "is_integral<float> == " << std::boolalpha   
        << std::is_integral<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_integral<trivial> == false  
is_integral<int> == true  
is_integral<float> == false  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_enum 類別](../standard-library/is-enum-class.md)   
 [is_floating_point 類別](../standard-library/is-floating-point-class.md)
