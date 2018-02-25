---
title: "scoped_allocator_adaptor 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
dev_langs:
- C++
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcfc9d5ca7b988be2dad0451aa2f58aacd15c789
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor 類別
表示巢狀配置器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>備註  
 此樣板類別會封裝巢狀的一或多個配置器。 這類每個類別都具備類型 `outer_allocator_type` (`Outer` 的同義字) 的最外層配置器，其為 `scoped_allocator_adaptor` 物件的公用基底。 `Outer` 可用來配置容器所使用的記憶體。 您可以呼叫 `outer_allocator`，來取得此配置器基底物件的參考。  
  
 巢狀的其餘部分會具備 `inner_allocator_type` 類型。 內部配置器可用來配置記憶體，以供容器內的項目使用。 您可以呼叫 `inner_allocator`，來取得此類型之預存物件的參考。 如果 `Inner...` 不是空的，`inner_allocator_type` 就具備 `scoped_allocator_adaptor<Inner...>` 類型，而 `inner_allocator` 會指定成員物件。 否則，`inner_allocator_type` 具備 `scoped_allocator_adaptor<Outer>` 類型，而 `inner_allocator` 會指定整個物件。  
  
 巢狀的行為就如同它含有任意深度，可視需要複寫其最內層的封裝配置器。  
  
 有數個不屬於可見介面一部分的概念，有助於說明此樣板類別的行為。 「最外層的配置器」會調解所有對建構和終結方法的呼叫。 這實際上是透過遞迴函式 `OUTERMOST(X)` 所定義，其中 `OUTERMOST(X)` 為下列其中一項。  
  
-   如果 `X.outer_allocator()` 格式正確，則 `OUTERMOST(X)` 是 `OUTERMOST(X.outer_allocator())`。  
  
-   否則，`OUTERMOST(X)` 為 `X`。  
  
 有三種類型是基於說明目的而定義：  
  
|類型|描述|  
|----------|-----------------|  
|`Outermost`|`OUTERMOST(*this)` 的類型。|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|建構 `scoped_allocator_adaptor` 物件。|  
  
### <a name="typedefs"></a>Typedef  
  
|名稱|描述|  
|----------|-----------------|  
|`const_pointer`|此類型是與 `Outer` 配置器相關聯之 `const_pointer` 的同義字。|  
|`const_void_pointer`|此類型是與 `Outer` 配置器相關聯之 `const_void_pointer` 的同義字。|  
|`difference_type`|此類型是與 `Outer` 配置器相關聯之 `difference_type` 的同義字。|  
|`inner_allocator_type`|此類型是巢狀配置器 `scoped_allocator_adaptor<Inner...>` 之類型的同義字。|  
|`outer_allocator_type`|此類型是基底配置器 `Outer` 之類型的同義字。|  
|`pointer`|此類型是與 `Outer` 配置器相關聯之 `pointer` 的同義字。|  
|`propagate_on_container_copy_assignment`|只有當 `Outer_traits::propagate_on_container_copy_assignment` 保留 true 或 `inner_allocator_type::propagate_on_container_copy_assignment` 保留 true 時，此類型才會保留 true。|  
|`propagate_on_container_move_assignment`|只有當 `Outer_traits::propagate_on_container_move_assignment` 保留 true 或 `inner_allocator_type::propagate_on_container_move_assignment` 保留 true 時，此類型才會保留 true。|  
|`propagate_on_container_swap`|只有當 `Outer_traits::propagate_on_container_swap` 保留 true 或 `inner_allocator_type::propagate_on_container_swap` 保留 true 時，此類型才會保留 true。|  
|`size_type`|此類型是與 `Outer` 配置器相關聯之 `size_type` 的同義字。|  
|`value_type`|此類型是與 `Outer` 配置器相關聯之 `value_type` 的同義字。|  
|`void_pointer`|此類型是與 `Outer` 配置器相關聯之 `void_pointer` 的同義字。|  
  
### <a name="structs"></a>結構  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_allocator_adaptor::rebind 結構](#rebind_struct)|將 `Outer::rebind\<Other>::other` 類型定義為 `scoped_allocator_adaptor\<Other, Inner...>` 的同義字。|  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[allocate](#allocate)|使用 `Outer` 配置器來配置記憶體。|  
|[construct](#construct)|建構物件。|  
|[deallocate](#deallocate)|使用外部配置器來取消配置物件。|  
|[destroy](#destroy)|終結指定的物件。|  
|[inner_allocator](#inner_allocator)|擷取 `inner_allocator_type` 類型之預存物件的參考。|  
|[max_size](#max_size)|決定可由外部配置器所配置的物件數目上限。|  
|[outer_allocator](#outer_allocator)|擷取 `outer_allocator_type` 類型之預存物件的參考。|  
|[select_on_container_copy_construction](#select_on_container_copy_construction)|建立新的 `scoped_allocator_adaptor` 物件，以及針對每個對應配置器呼叫 `select_on_container_copy_construction` 來初始化的每個預存配置器物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<scoped_allocator >  
  
 **命名空間：** std  
  
##  <a name="allocate"></a>  scoped_allocator_adaptor::allocate
 使用 `Outer` 配置器來配置記憶體。  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 要配置足夠儲存體的項目數。  
  
 `hint`  
 指標，可藉由找出要求之前所配置的物件位址，來協助配置器物件。  
  
### <a name="return-value"></a>傳回值  
 第一個成員函式會傳回 `Outer_traits::allocate(outer_allocator(), count)`。 第二個成員函式會傳回 `Outer_traits::allocate(outer_allocator(), count, hint)`。  
  
##  <a name="construct"></a>  scoped_allocator_adaptor::construct
 建構物件。  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 要建構物件之記憶體位置的指標。  
  
 `args`  
 引數清單。  
  
 `first`  
 配對中第一個類型的物件。  
  
 `second`  
 配對中第二個類型的物件。  
  
 `right`  
 要移動或複製的現有物件。  
  
### <a name="remarks"></a>備註  
 第一個方法會藉由呼叫 `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`，在 `ptr` 上建構物件，其中 `xargs...` 是下列其中一項。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 保留 false，則 `xargs...` 是 `args...`。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 保留 true，而且 `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` 保留 true，則 `xargs...` 是 `allocator_arg, inner_allocator(), args...`。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 保留 true，而且 `is_constructible<Ty, args..., inner_allocator()>` 保留 true，則 `xargs...` 是 `args..., inner_allocator()`。  
  
 第二個方法會藉由呼叫 `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)` (其中 `xargs...` 是如上述清單中修改的 `first...`) 及 `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)` (其中 `xargs...` 是如上述清單中修改的 `second...`)，在 `ptr` 上建構配對物件。  
  
 第三個方法的行為與 `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)` 相同。  
  
 第四個方法的行為與 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))` 相同。  
  
 第五個方法的行為與 `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))` 相同。  
  
 第六個方法的行為與 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))` 相同。  
  
##  <a name="deallocate"></a>  scoped_allocator_adaptor::deallocate
 使用外部配置器來取消配置物件。  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 要解除配置之物件的起始位置指標。  
  
 `count`  
 要解除配置的物件數目。  
  
##  <a name="destroy"></a>  scoped_allocator_adaptor::destroy
 終結指定的物件。  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 要終結的物件指標。  
  
### <a name="return-value"></a>傳回值  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator
 擷取 `inner_allocator_type` 類型之預存物件的參考。  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 `inner_allocator_type` 類型之預存物件的參考。  
  
##  <a name="max_size"></a>  scoped_allocator_adaptor::max_size
 決定可由外部配置器所配置的物件數目上限。  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>傳回值  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator
 擷取 `outer_allocator_type` 類型之預存物件的參考。  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 `outer_allocator_type` 類型之預存物件的參考。  
  
##  <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind 結構  
 將 `Outer::rebind\<Other>::other` 類型定義為 `scoped_allocator_adaptor\<Other, Inner...>` 的同義字。  
  
struct rebind{  
   typedef Other_traits::rebind\<Other>  
   Other_alloc;  
   typedef scoped_allocator_adaptor\<Other_alloc, Inner...> other;  
   };  
  
##  <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor 建構函式  
 建構 `scoped_allocator_adaptor` 物件。  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>參數  
 `right`  
 現有的 `scoped_allocator_adaptor`。  
  
 `al`  
 用來做為外部配置器的現有配置器。  
  
 `rest`  
 用來做為內部配置器的配置器清單。  
  
### <a name="remarks"></a>備註  
 第一個建構函式預設會建構它的預存配置器物件。 後續三個建構函式的每一個都會從 `right` 的對應物件中建構它的預存配置器物件。 最後一個建構函式會從引數清單的對應引數中建立它的預存配置器物件。  
  
##  <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction
 建立新的 `scoped_allocator_adaptor` 物件，以及針對每個對應配置器呼叫 `select_on_container_copy_construction` 來初始化的每個預存配置器物件。  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>傳回值  
 這個方法會有效地傳回 `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`。 結果是新的 `scoped_allocator_adaptor` 物件，以及對於對應配置器 `al` 呼叫 `al.select_on_container_copy_construction()` 來初始化的每個預存配置器物件。  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)



