---
title: "add_volatile 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 7e652a784276d01c572ffad0379a20359a7b39f2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="addvolatile-class"></a>add_volatile 類別
從指定類型建立 volatile 類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct add_volatile;  
 
template <class T>
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
### <a name="parameters"></a>參數  
*T*  
要修改的類型。  
  
## <a name="remarks"></a>備註  
如果 *T* 是參考、函式或 volatile 限定類型，`add_volatile<T>` 執行個體具有為 *T* 的成員 typedef `type`，否則為 `volatile` *T*。`add_volatile_t` 別名是存取成員 typedef `type` 的捷徑。 
  
## <a name="example"></a>範例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
} 
```  
  
```Output  
add_volatile<int> == int  
```  
  
## <a name="requirements"></a>需求  

**標頭：**\<type_traits>  
  
**命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
[<type_traits>](../standard-library/type-traits.md)   
[remove_volatile 類別](../standard-library/remove-volatile-class.md)

