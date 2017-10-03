---
title: "&lt;scoped_allocator&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
caps.latest.revision: 10
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: d29a5a99f261776468364717a13b90a1ddde5216
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; 運算子
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 測試兩個 `scoped_allocator_adaptor` 物件是否不相等。  
  
```cpp  
template <class Outer, class... Inner>  
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>參數  
 `left`  
 左 `scoped_allocator_adaptor` 物件。  
  
 `right`  
 右 `scoped_allocator_adaptor` 物件。  
  
### <a name="return-value"></a>傳回值  
 `!(left == right)`  
  
##  <a name="op_eq_eq"></a>  operator==  
 測試兩個 `scoped_allocator_adaptor` 物件是否相等。  
  
```cpp  
template <class Outer, class... Inner>  
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>參數  
 `left`  
 左 `scoped_allocator_adaptor` 物件。  
  
 `right`  
 右 `scoped_allocator_adaptor` 物件。  
  
### <a name="return-value"></a>傳回值  
 `left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`  
  
## <a name="see-also"></a>另請參閱  
 [<scoped_allocator>](../standard-library/scoped-allocator.md)


