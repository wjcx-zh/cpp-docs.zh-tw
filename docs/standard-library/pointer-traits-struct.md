---
title: "pointer_traits 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
dev_langs:
- C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: dbb9a0a8ecd59b76a84ce05b3c239de42be647cb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="pointertraits-struct"></a>pointer_traits 結構
提供樣板類別 `allocator_traits` 的物件所需的資訊，以描述具有指標類型 `Ptr` 的配置器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <class Ptr>
struct pointer_traits;
```  
  
## <a name="remarks"></a>備註  
 Ptr 可以是類型 `Ty *` 的原始指標，或是具有下列屬性的類別。  
```  
struct Ptr
   { // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj);
   // optional
   };  
```
### <a name="typedefs"></a>Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`typedef T2 difference_type`|類型 `T2` 為 `Ptr::difference_type` (如果該類型存在)，否則為 `ptrdiff_t`。 如果 `Ptr` 為原始指標，則類型為 `ptrdiff_t`。|  
|`typedef T1 element_type`|類型 `T1` 為 `Ptr::element_type` (如果該類型存在)，否則為 `Ty`。 如果 `Ptr` 為原始指標，則類型為 `Ty`。|  
|`typedef Ptr pointer`|類型為 `Ptr`。|  
  
### <a name="structs"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|`pointer_traits::rebind`|嘗試將基礎指標類型轉換為指定類型。|  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[pointer_to](#pointer_to)|將任意的參考轉換為 `Ptr` 類別的物件。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
##  <a name="pointer_to"></a>  pointer_to  
 傳回 `Ptr::pointer_to(obj)` 的靜態方法 (如果該函式存在)。 否則，不可能將任意參考轉換為 `Ptr` 類別的物件。 如果 `Ptr` 是原始指標，此方法會傳回 `addressof(obj)`。  
  
```cpp  
static pointer pointer_to(element_type& obj);
```  
  
## <a name="see-also"></a>另請參閱  
 [\<memory>](../standard-library/memory.md)   
 [allocator_traits 類別](../standard-library/allocator-traits-class.md)


