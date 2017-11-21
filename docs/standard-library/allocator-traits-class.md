---
title: "allocator_traits 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
dev_langs: C++
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 5ddb30840a3f92de70d688cc763394e92b356417
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="allocatortraits-class"></a>allocator_traits 類別
此範本類別所描述的物件補充說明「配置器類型」。 配置器類型是任何類型，可描述用來管理所配置儲存空間的配置器物件。 具體來說，針對任何配置器類型 `Alloc`，您可以使用 `allocator_traits<Alloc>` 來判斷啟用配置器之容器所需的所有資訊。 如需詳細資訊，請參閱預設 [allocator 類別](../standard-library/allocator-class.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <class Alloc>
class allocator_traits;
```  
  
### <a name="typedefs"></a>Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`allocator_traits::allocator_type`|此類型是範本參數 `Alloc` 的同義字。|  
|`allocator_traits::const_pointer`|如果該類型的格式良好，則此類型為 `Alloc::const_pointer`；否則，此類型為 `pointer_traits<pointer>::rebind<const value_type>`。|  
|`allocator_traits::const_void_pointer`|如果該類型的格式良好，則此類型為 `Alloc::const_void_pointer`；否則，此類型為 `pointer_traits<pointer>::rebind<const void>`。|  
|`allocator_traits::difference_type`|如果該類型的格式良好，則此類型為 `Alloc::difference_type`；否則，此類型為 `pointer_traits<pointer>::difference_type`。|  
|`allocator_traits::pointer`|如果該類型的格式良好，則此類型為 `Alloc::pointer`；否則，此類型為 `value_type *`。|  
|`allocator_traits::propagate_on_container_copy_assignment`|如果該類型的格式良好，則此類型為 `Alloc::propagate_on_container_copy_assignment`；否則，此類型為 `false_type`。|  
|`allocator_traits::propagate_on_container_move_assignment`|如果該類型的格式良好，則此類型為 `Alloc::propagate_on_container_move_assignment`；否則，此類型為 `false_type`。 如果類型為 true，則啟用配置器的容器會複製其在 move 指派上的預存配置器。|  
|`allocator_traits::propagate_on_container_swap`|如果該類型的格式良好，則此類型為 `Alloc::propagate_on_container_swap`；否則，此類型為 `false_type`。 如果類型為 true，則啟用配置器的容器會在交換時交換其預存配置器。|  
|`allocator_traits::size_type`|如果該類型的格式良好，則此類型為 `Alloc::size_type`；否則，此類型為 `make_unsigned<difference_type>::type`。|  
|`allocator_traits::value_type`|這個類型是 `Alloc::value_type` 的同義字。|  
|`allocator_traits::void_pointer`|如果該類型的格式良好，則此類型為 `Alloc::void_pointer`；否則，此類型為 `pointer_traits<pointer>::rebind<void>`。|  
  
### <a name="static-methods"></a>靜態方法  
 下列靜態方法會在指定的配置器參數上呼叫對應方法。  
  
|名稱|說明|  
|----------|-----------------|  
|[allocate](#allocate)|靜態方法，使用指定的配置器參數來配置記憶體。|  
|[construct](#construct)|靜態方法，使用指定的配置器來建構物件。|  
|[deallocate](#deallocate)|靜態方法，使用指定的配置器來解除配置指定數目的物件。|  
|[destroy](#destroy)|靜態方法，使用指定的配置器在物件上呼叫解構函式，而不解除配置其記憶體。|  
|[max_size](#max_size)|靜態方法，使用指定的配置器來決定可配置的物件數目上限。|  
|[select_on_container_copy_construction](#select_on_container_copy_construction)|靜態方法，可在指定的配置器上呼叫 `select_on_container_copy_construction`。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
##  <a name="allocate"></a>allocator_traits:: allocate
 靜態方法，使用指定的配置器參數來配置記憶體。  
  
```cpp  
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
 `count`  
 要配置的元素數。  
  
 `hint`  
 `const_pointer`，可找出要求之前所配置物件的位址，來協助配置器物件符合儲存要求。 Null 指標視為沒有提示。  
  
### <a name="return-value"></a>傳回值  
 每個方法都會傳回所配置物件的指標。  
  
 第一個靜態方法會傳回 `al.allocate(count)`。  
  
 如果該運算式的格式良好，則第二個方法會傳回 `al.allocate(count, hint)`；否則會傳回 `al.allocate(count)`。  
  
##  <a name="construct"></a>allocator_traits:: construct
 靜態方法，使用指定的配置器來建構物件。  
  
```cpp  
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
 `ptr`  
 要建構物件之位置的指標。  
  
 `args`  
 傳遞給物件建構函式的引數清單。  
  
### <a name="remarks"></a>備註  
 如果該運算式的格式良好，則靜態成員函式會呼叫 `al.construct(ptr, args...)`；否則會評估 `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`。  
  
##  <a name="deallocate"></a>allocator_traits:: deallocate
 靜態方法，使用指定的配置器來解除配置指定數目的物件。  
  
```cpp  
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
 `ptr`  
 要解除配置之物件的起始位置指標。  
  
 `count`  
 要解除配置的物件數目。  
  
### <a name="remarks"></a>備註  
 此方法會呼叫 `al.deallocate(ptr, count)`。  
  
 這個方法不會擲回任何項目。  
  
##  <a name="destroy"></a>allocator_traits:: destroy
 靜態方法，使用指定的配置器在物件上呼叫解構函式，而不解除配置其記憶體。  
  
```cpp  
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
 `ptr`  
 物件位置的指標。  
  
### <a name="remarks"></a>備註  
 如果該運算式的格式良好，則此方法會呼叫 `al.destroy(ptr)`；否則會評估 `ptr->~Uty()`。  
  
##  <a name="max_size"></a>allocator_traits:: max_size
 靜態方法，使用指定的配置器來決定可配置的物件數目上限。  
  
```cpp  
static size_type max_size(const Alloc& al);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
### <a name="remarks"></a>備註  
 如果該運算式的格式良好，則此方法會傳回 `al.max_size()`；否則會傳回 `numeric_limits<size_type>::max()`。  
  
##  <a name="select_on_container_copy_construction"></a>allocator_traits:: select_on_container_copy_construction
 靜態方法，可在指定的配置器上呼叫 `select_on_container_copy_construction`。  
  
```cpp  
static Alloc select_on_container_copy_construction(const Alloc& al);
```  
  
### <a name="parameters"></a>參數  
 `al`  
 配置器物件。  
  
### <a name="return-value"></a>傳回值  
 如果該類型的格式良好，則此方法會傳回 `al.select_on_container_copy_construction()`；否則會傳回 `al`。  
  
### <a name="remarks"></a>備註  
 此方法用來在建構複製相關聯的容器時指定配置器。  
  
## <a name="see-also"></a>另請參閱  
 [\<memory>](../standard-library/memory.md)   
 [pointer_traits 結構](../standard-library/pointer-traits-struct.md)   
 [scoped_allocator_adaptor 類別](../standard-library/scoped-allocator-adaptor-class.md)
