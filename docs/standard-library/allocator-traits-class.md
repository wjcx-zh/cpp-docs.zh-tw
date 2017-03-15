---
title: "allocator_traits 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator_traits"
  - "memory/std::allocator_traits::propagate_on_container_move_assignment"
  - "memory/std::allocator_traits::const_pointer"
  - "memory/std::allocator_traits::propagate_on_container_swap"
  - "memory/std::allocator_traits::propagate_on_container_copy_assignment"
  - "memory/std::allocator_traits::difference_type"
  - "memory/std::allocator_traits::allocator_type"
  - "memory/std::allocator_traits::value_type"
  - "memory/std::allocator_traits::pointer"
  - "memory/std::allocator_traits::size_type"
  - "memory/std::allocator_traits::const_void_pointer"
  - "memory/std::allocator_traits::void_pointer"
dev_langs: 
  - "C++"
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# allocator_traits 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述補充 *配置器*類型的物件。  配置器類型是描述一配置器物件為流程配置儲存體使用的任何型別。  具體來說，為任何配置器型別 `Alloc`，您可以使用 `allocator_traits<Alloc>` 由配置器可讓容器所需的所有資訊。  如需詳細資訊，請參閱預設的 [allocator 類別](../standard-library/allocator-class.md)。  
  
## 語法  
  
```cpp  
template<class Alloc>  
    class allocator_traits;  
```  
  
### Typedef  
  
|Name|說明|  
|----------|--------|  
|`allocator_traits::allocator_type`|這個型別是樣板參數 `Alloc`的同義字。|  
|`allocator_traits::const_pointer`|如果該型別不正確的，這個型別是 `Alloc::const_pointer`;否則，這個型別是 `pointer_traits<pointer>::rebind<const value_type>`。|  
|`allocator_traits::const_void_pointer`|如果該型別不正確的，這個型別是 `Alloc::const_void_pointer`;否則，這個型別是 `pointer_traits<pointer>::rebind<const void>`。|  
|`allocator_traits::difference_type`|如果該型別不正確的，這個型別是 `Alloc::difference_type`;否則，這個型別是 `pointer_traits<pointer>::difference_type`。|  
|`allocator_traits::pointer`|如果該型別不正確的，這個型別是 `Alloc::pointer`;否則，這個型別是 `value_type *`。|  
|`allocator_traits::propagate_on_container_copy_assignment`|如果該型別不正確的，這個型別是 `Alloc::propagate_on_container_copy_assignment`;否則，這個型別是 `false_type`。|  
|`allocator_traits::propagate_on_container_move_assignment`|如果該型別不正確的，這個型別是 `Alloc::propagate_on_container_move_assignment`;否則，這個型別是 `false_type`。  如果型別套用，配置器可讓容器複製它在移動工作所儲存的配置器。|  
|`allocator_traits::propagate_on_container_swap`|如果該型別不正確的，這個型別是 `Alloc::propagate_on_container_swap`;否則，這個型別是 `false_type`。  如果型別套用，配置器可讓容器交換其在 Exchange 儲存的配置器。|  
|`allocator_traits::size_type`|如果該型別不正確的，這個型別是 `Alloc::size_type`;否則，這個型別是 `make_unsigned<difference_type>::type`。|  
|`allocator_traits::value_type`|型別為 `Alloc::value_type`的同義字。|  
|`allocator_traits::void_pointer`|如果該型別不正確的，這個型別是 `Alloc::void_pointer`;否則，這個型別是 `pointer_traits<pointer>::rebind<void>`。|  
  
### 靜態方法  
 下列靜態方法呼叫中的特定配置器參數的對應方法。  
  
|Name|說明|  
|----------|--------|  
|[allocator\_traits::allocate 方法](../Topic/allocator_traits::allocate%20Method.md)|使用特定配置器參數，該靜態方法所配置的記憶體。|  
|[allocator\_traits::construct 方法](../Topic/allocator_traits::construct%20Method.md)|使用指定的配置器建構物件的靜態方法。|  
|[allocator\_traits::deallocate 方法](../Topic/allocator_traits::deallocate%20Method.md)|使用指定的配置器解除物件指定數字的靜態方法。|  
|[allocator\_traits::destroy 方法](../Topic/allocator_traits::destroy%20Method.md)|使用指定的配置器呼叫物件的解構函式，而不需解除其記憶體的靜態方法。|  
|[allocator\_traits::max\_size 方法](../Topic/allocator_traits::max_size%20Method.md)|使用指定的配置器判斷物件的最大數目可以配置的靜態方法。|  
|[allocator\_traits::select\_on\_container\_copy\_construction 方法](../Topic/allocator_traits::select_on_container_copy_construction%20Method.md)|會在指定的配置器的 `select_on_container_copy_construction` 的靜態方法。|  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<memory\>](../standard-library/memory.md)   
 [pointer\_traits 結構](../standard-library/pointer-traits-struct.md)   
 [scoped\_allocator\_adaptor 類別](../standard-library/scoped-allocator-adaptor-class.md)