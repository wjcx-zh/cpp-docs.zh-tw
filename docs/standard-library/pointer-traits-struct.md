---
title: "pointer_traits 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::pointer_traits::element_type"
  - "memory/std::pointer_traits::pointer"
  - "memory/std::pointer_traits"
  - "memory/std::pointer_traits::difference_type"
  - "memory/std::pointer_traits::rebind"
  - "xmemory0/std::pointer_traits::element_type"
  - "xmemory0/std::pointer_traits::pointer"
  - "xmemory0/std::pointer_traits"
  - "xmemory0/std::pointer_traits::difference_type"
  - "xmemory0/std::pointer_traits::rebind"
dev_langs: 
  - "C++"
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# pointer_traits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供樣板類別 `allocator_traits` 的物件所需的資訊，以描述具有指標類型 `Ptr` 的配置器。  
  
## 語法  
  
```cpp  
template<class Ptr>  
    struct pointer_traits;  
```  
  
## 備註  
 Ptr 可以屬於型別 `Ty *` 或具有下列屬性的類別是未經處理的指標。  
  
```  
template<class Ty, class... Rest>  
    struct Ptr  
    { // describes a pointer type usable by allocators  
    typedef Ptr pointer;  
    typedef T1 element_type; // optional  
    typedef T2 difference_type; // optional  
    template<class Other>  
        using rebind = typename Ptr<Other, Rest...>; // optional  
  
    static pointer pointer_to(element_type& obj); // optional  
    };  
```  
  
> [!WARNING]
>  當 C\+\+ 標準指定 `rebind` 成員做為別名範本時， Visual C\+\+ 實作變更為 `struct`。  
  
### Typedef  
  
|Name|說明|  
|----------|--------|  
|`typedef T2 difference_type`|這個型別的 `T2` 為 `Ptr::difference_type` ，如果該型別，否則為 `ptrdiff_t`。  如果 `Ptr` 是原始指標，型別為 `ptrdiff_t`。|  
|`typedef T1 element_type`|這個型別的 `T1` 為 `Ptr::element_type` ，如果該型別，否則為 `Ty`。  如果 `Ptr` 是原始指標，型別為 `Ty`。|  
|`typedef Ptr pointer`|型別為 `Ptr`。|  
  
### Structs  
  
|Name|說明|  
|----------|--------|  
|`pointer_traits::rebind`|嘗試將轉換基底指標型別為指定型別。|  
  
### 方法  
  
|Name|說明|  
|----------|--------|  
|[pointer\_traits::pointer\_to 方法](../Topic/pointer_traits::pointer_to%20Method.md)|轉換成 `Ptr`類別物件的選擇性參考。|  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<memory\>](../standard-library/memory.md)   
 [allocator\_traits 類別](../standard-library/allocator-traits-class.md)