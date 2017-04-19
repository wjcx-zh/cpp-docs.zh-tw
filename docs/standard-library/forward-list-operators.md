---
title: "&lt;forward_list&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a560de0a7587b5552fc663bdd2b44734a66b5f73
ms.lasthandoff: 02/24/2017

---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>  operator==  
 測試運算子左邊的轉送清單物件是否等於右邊的轉送清單物件。  
  
```
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="remarks"></a>備註  
 這個範本函式會多載 `operator==` 來比較 `forward_list` 範本類別的兩個物件。 函式會傳回 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`。  
  
##  <a name="operator_neq"></a>  operator!=  
 測試運算子左邊的轉送清單物件是否不等於右邊的轉送清單物件。  
  
```
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="return-value"></a>傳回值  
 如果清單不相等，便會傳回 **true**；如果清單相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 此範本函式會傳回 `!(left == right)`。  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 測試運算子左邊的轉送清單物件是否小於右邊的轉送清單物件。  
  
```
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的清單小於但不等於右邊的清單，即為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個範本函式會多載 `operator<` 來比較 `forward_list` 範本類別的兩個物件。 函式會傳回 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`。  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 測試運算子左邊的轉送清單物件是否小於或等於右邊的轉送清單物件。  
  
```
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的清單小於或等於右邊的清單，即為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此範本函式會傳回 `!(right < left)`。  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 測試運算子左邊的轉送清單物件是否大於右邊的轉送清單物件。  
  
```
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單大於右邊的清單，即為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此範本函式會傳回 `right < left`。  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 測試運算子左邊的轉送清單物件是否大於或等於右邊的轉送清單物件。  
  
```
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的轉送清單大於或等於右邊的轉送清單，即為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此範本函式會傳回 `!(left < right)`。  
  
## <a name="see-also"></a>另請參閱  
 [<forward_list>](../standard-library/forward-list.md)




