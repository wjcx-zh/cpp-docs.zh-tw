---
title: "aligned_union 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- aligned_union
- type_traits/std::aligned_union
dev_langs:
- C++
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: 10
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: d6ecefd7d6877bc65bbf6f5542ae6b7f318a9d27
ms.lasthandoff: 02/24/2017

---
# <a name="alignedunion-class"></a>aligned_union 類別
提供夠大並適當對齊的 POD 類型來儲存等位類型，以及所需的大小。  
  
## <a name="syntax"></a>語法  
  
```  
template <std::size_t Len, class... Types>  
struct aligned_union;  
 
template <std::size_t Len, class... Types>  
using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `Len`  
 等位中最大類型的對齊值。  
  
 `Types`  
 基礎等位中的不同類型。  
  
## <a name="remarks"></a>備註  
 使用此範本類別，即可取得將等位儲存在未初始化儲存空間中所需的對齊和大小。 成員 typedef `type` 會命名適合儲存 `Types` 中所列之任何類型的 POD 類型；大小下限為 `Len`。 類型 `std::size_t` 的靜態成員 `alignment_value` 包含 `Types` 中所列之所有類型需要的最嚴格對齊。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `aligned_union` 配置對齊的堆疊緩衝區來放置等位。  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
value of u->i is 1065353216  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [alignment_of 類別](../standard-library/alignment-of-class.md)

