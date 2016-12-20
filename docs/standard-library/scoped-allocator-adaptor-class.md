---
title: "scoped_allocator_adaptor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.scoped_allocator_adaptor"
  - "scoped_allocator_adaptor"
  - "scoped_allocator/std::scoped_allocator_adaptor"
  - "std::scoped_allocator_adaptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scoped_allocator_adaptor 類別"
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 10
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scoped_allocator_adaptor 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示配置器巢。  
  
## 語法  
  
```cpp  
template<class Outer, class... Inner>  
    class scoped_allocator_adaptor;  
```  
  
## 備註  
 樣板類別封裝一或多個配置器巢。  每個類別具有 `outer_allocator_type`， `Outer`的同義字的最外層的配置器，即 `scoped_allocator_adaptor` 物件的公用基底。  `Outer` 用來配置容器所使用的記憶體。  您可以藉由呼叫 `outer_allocator`取得此配置器基底物件的參考。  
  
 巢狀的其餘部分具有型別 `inner_allocator_type`。  內部配置器用來配置項目的記憶體在容器內。  您可以藉由呼叫 `inner_allocator`取得這個型別會儲存物件的參考。  如果 `Inner...` 不是 null，則 `inner_allocator_type` 的型別，則為 `scoped_allocator_adaptor<Inner...>`，而 `inner_allocator` 指定為 10% 的物件。  否則， `inner_allocator_type` 的型別，則為 `scoped_allocator_adaptor<Outer>`，且 `inner_allocator` 會指定整個物件。  
  
 的行為，就像具有任意深度，請複製該程式碼最內層封裝的配置器視需要。  
  
 不可見的介面協助的部分在描述這個範本類別行為的幾個概念。  的 *最外層的配置器* 斡旋所有呼叫建構並終結方法。  它是有效地由遞迴函式 `OUTERMOST(X)`定義的 `OUTERMOST(X)` ，是下列其中一項。  
  
-   如果 `X.outer_allocator()` 是語式正確，則 `OUTERMOST(X)` 為 `OUTERMOST(X.outer_allocator())`。  
  
-   否則，`OUTERMOST(X)` 為 `X`。  
  
 三個型別為平台上會定義:  
  
|型別|說明|  
|--------|--------|  
|`Outermost`|`OUTERMOST(*this)` 的型別。|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### 建構函式  
  
|Name|說明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::scoped\_allocator\_adaptor 建構函式](../Topic/scoped_allocator_adaptor::scoped_allocator_adaptor%20Constructor.md)|建構 `scoped_allocator_adaptor` 物件。|  
  
### Typedef  
  
|Name|說明|  
|----------|--------|  
|`const_pointer`|這個型別是與配置器 `Outer``const_pointer` 的同義字。|  
|`const_void_pointer`|這個型別是與配置器 `Outer``const_void_pointer` 的同義字。|  
|`difference_type`|這個型別是與配置器 `Outer``difference_type` 的同義字。|  
|`inner_allocator_type`|這個型別是巢狀 `scoped_allocator_adaptor<Inner...>`配接器類型的同義字。|  
|`outer_allocator_type`|這個型別是基本的配置器 `Outer`類型的同義字。|  
|`pointer`|型別為 `pointer` 的同義字與配置器 `Outer`。|  
|`propagate_on_container_copy_assignment`|這個型別套用時，才會套用 `Outer_traits::propagate_on_container_copy_assignment` 或 `inner_allocator_type::propagate_on_container_copy_assignment` 套用。|  
|`propagate_on_container_move_assignment`|這個型別套用時，才會套用 `Outer_traits::propagate_on_container_move_assignment` 或 `inner_allocator_type::propagate_on_container_move_assignment` 套用。|  
|`propagate_on_container_swap`|這個型別套用時，才會套用 `Outer_traits::propagate_on_container_swap` 或 `inner_allocator_type::propagate_on_container_swap` 套用。|  
|`size_type`|型別為 `size_type` 的同義字與配置器 `Outer`。|  
|`value_type`|型別為 `value_type` 的同義字與配置器 `Outer`。|  
|`void_pointer`|型別為 `void_pointer` 的同義字與配置器 `Outer`。|  
  
### Structs  
  
|Name|說明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::rebind 結構](../Topic/scoped_allocator_adaptor::rebind%20Struct.md)|定義 `Outer::rebind<Other>::other` 型別為 `scoped_allocator_adaptor<Other, Inner...>`的同義字。|  
  
### 方法  
  
|Name|說明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::allocate 方法](../Topic/scoped_allocator_adaptor::allocate%20Method.md)|使用 `Outer` 配置器，配置記憶體。|  
|[scoped\_allocator\_adaptor::construct 方法](../Topic/scoped_allocator_adaptor::construct%20Method.md)|建構物件。|  
|[scoped\_allocator\_adaptor::deallocate 方法](../Topic/scoped_allocator_adaptor::deallocate%20Method.md)|使用外部配置器，則會解除配置物件。|  
|[scoped\_allocator\_adaptor::destroy 方法](../Topic/scoped_allocator_adaptor::destroy%20Method.md)|終結指定的物件。|  
|[scoped\_allocator\_adaptor::inner\_allocator 方法](../Topic/scoped_allocator_adaptor::inner_allocator%20Method.md)|擷取對 `inner_allocator_type`型別儲存物件的參考。|  
|[scoped\_allocator\_adaptor::max\_size 方法](../Topic/scoped_allocator_adaptor::max_size%20Method.md)|判斷可以由外部配置器所配置的物件數目上限。|  
|[scoped\_allocator\_adaptor::outer\_allocator 方法](../Topic/scoped_allocator_adaptor::outer_allocator%20Method.md)|擷取對 `outer_allocator_type`型別儲存物件的參考。|  
|[scoped\_allocator\_adaptor::select\_on\_container\_copy\_construction 方法](../Topic/scoped_allocator_adaptor::select_on_container_copy_construction%20Method.md)|建立與初始化呼叫的每個儲存的配置器物件的新 `scoped_allocator_adaptor` 物件每一個對應的配置器的 `select_on_container_copy_construction` 。|  
  
## 需求  
 **標題:** \<scoped\_allocator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)