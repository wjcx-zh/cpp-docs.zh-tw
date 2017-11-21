---
title: "extent 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::extent
dev_langs: C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 185cb6108801b31c19301a0f7488352a6948f5bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="extent-class"></a>extent 類別
取得陣列維度。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty, unsigned I = 0>  
struct extent;  
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
 `I`  
 要查詢的陣列界限  
  
## <a name="remarks"></a>備註  
 如果 `Ty` 是至少有 `I` 個維度的陣列類型，則類型查詢會保留 `I` 所指定之維度中的項目數。 如果 `Ty` 不是陣列型別或其等級小於 `I`，或者如果 `I` 為零，而且 `Ty` 的類型是「`U` 的未知界限陣列」，則類型查詢會保留 0 值。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
extent 0 == 5  
extent 1 == 10  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_all_extents 類別](../standard-library/remove-all-extents-class.md)   
 [remove_extent 類別](../standard-library/remove-extent-class.md)
