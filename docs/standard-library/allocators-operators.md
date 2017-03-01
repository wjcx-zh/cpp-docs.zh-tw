---
title: "&lt;allocators&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6185bc74c530d6327d0ac37a5425a7653ba36841
ms.lasthandoff: 02/24/2017

---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子
|||  
|-|-|  
|[operator!=](#operator_neq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a> operator!=  
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
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a> operator==  
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




