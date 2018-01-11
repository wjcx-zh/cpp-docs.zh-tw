---
title: "aligned_storage 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::aligned_storage
dev_langs: C++
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10fdc0726ee4c20b9c2e4f6058ef4a5010f0229c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="alignedstorage-class"></a>aligned_storage 類別
建立適當對齊的類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <std::size_t Len, std::size_t Align>  
struct aligned_storage;  
 
template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>  
using aligned_storage_t = typename aligned_storage<Len, Align>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `Len`  
 物件大小。  
  
 `Align`  
 物件對齊。  
  
## <a name="remarks"></a>備註  
 範本成員 typedef `type` 是對齊為 `Align` 且大小為 `Len` 之 POD 類型的同義字。 對於特定類型 `T`，`Align` 必須等於 `alignment_of<T>::value`，或等於預設對齊。  
  
## <a name="example"></a>範例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
typedef std::aligned_storage<sizeof (int),   
    std::alignment_of<double>::value>::type New_type;   
int main()   
    {   
    std::cout << "alignment_of<int> == "   
        << std::alignment_of<int>::value << std::endl;   
    std::cout << "aligned to double == "   
        << std::alignment_of<New_type>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
alignment_of<int> == 4  
aligned to double == 8  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [alignment_of 類別](../standard-library/alignment-of-class.md)