---
title: "remove_volatile 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- remove_volatile
- type_traits/std::remove_volatile
dev_langs:
- C++
helpviewer_keywords:
- remove_volatile class
- remove_volatile
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
caps.latest.revision: 20
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 6c4e2273d6eed8e88f101a25f5b53b777a0bc48f
ms.lasthandoff: 02/24/2017

---
# <a name="removevolatile-class"></a>remove_volatile 類別
從類型建立非 volatile 類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <class T>  
struct remove_volatile;  
 
template <class T>  
using remove_volatile_t = typename remove_volatile<T>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要修改的類型。  
  
## <a name="remarks"></a>備註  
 `remove_volatile<T>` 執行個體儲存修改的類型，如果 `T1` 的格式為 `T`，類型為 `volatile T1`，否則為 `T`。  
  
## <a name="example"></a>範例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_volatile_t<volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << " remove_volatile_t<volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_volatile_t<volatile int> == int  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [add_volatile 類別](../standard-library/add-volatile-class.md)

