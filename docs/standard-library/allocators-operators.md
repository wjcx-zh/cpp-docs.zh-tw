---
title: "&lt;allocators&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c6b19eb0c4f8d63ce288ce47a759e949714daf5e
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a> operator!=  
 測試指定類別的配置器物件之間是否不等。  
  
```
template <class Type, class Sync>  
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`left`|要測試是否不相等的其中一個配置器物件。|  
|`right`|要測試是否不相等的其中一個配置器物件。|  
  
### <a name="return-value"></a>傳回值  
 如果配置器物件不相等，則為 **true**；如果配置器物件相等，則為 **false**。  
  
### <a name="remarks"></a>備註  
 範本運算子會傳回 `!(left == right)`。  
  
##  <a name="op_eq_eq"></a> operator==  
 測試指定類別的配置器物件之間是否相等。  
  
```
template <class Type, class Sync>  
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`left`|要測試是否相等的其中一個配置器物件。|  
|`right`|要測試是否相等的其中一個配置器物件。|  
  
### <a name="return-value"></a>傳回值  
 如果配置器物件相等，則為 **true**；如果配置器物件不相等，則為 **false**。  
  
### <a name="remarks"></a>備註  
 這個範本運算子會傳回 `left.equals(right)`。  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




