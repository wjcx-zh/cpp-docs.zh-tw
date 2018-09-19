---
title: concurrency 命名空間運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13b9288e39e372ecb23299d355abc921353444b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059867"
---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空間運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|  
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|  
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)|  
  
##  <a name="operator_lor"></a>  運算子&#124;&#124;運算子  
 建立工作，這個工作將會在兩個當做引數提供的任一工作已順利完成時成功完成。  
  
```  
template<typename ReturnType>  
task<ReturnType> operator||(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void> operator||(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>參數  
*ReturnType*<br/>
所傳回工作的類型。  
  
*lhs*<br/>
合併至所產生工作的第一個工作。  
  
*rhs*<br/>
合併至所產生工作的第二個工作。  
  
### <a name="return-value"></a>傳回值  
 在任一個輸入工作順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。  
  
### <a name="remarks"></a>備註  
 如果兩個工作都取消或擲回例外狀況，則傳回的工作會以已取消狀態完成，而且其中一個例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。  
  
##  <a name="operator_amp_amp"></a>  運算子&amp;&amp;運算子  
 建立工作，這個工作將會在兩個當做引數提供的工作都已順利完成時成功完成。  
  
```  
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void>  operator&&(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>參數  
*ReturnType*<br/>
所傳回工作的類型。  
  
*lhs*<br/>
合併至所產生工作的第一個工作。  
  
*rhs*<br/>
合併至所產生工作的第二個工作。  
  
### <a name="return-value"></a>傳回值  
 會在兩個輸入工作都順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。  
  
### <a name="remarks"></a>備註  
 如果其中一個工作取消或擲回例外狀況，則傳回的工作會在已取消狀態中提早完成，而且例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。  
  
##  <a name="operator_eq_eq"></a>  運算子 = = 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 若運算子左邊的並行向量等於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 兩個的並行向量相等，如果有相同數目的項目，且其個別元素擁有相同的值。 反之則為不相等。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_neq"></a>  運算子 ！ = 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果並行向量不相等。`false`並行向量是否相等。  
  
### <a name="remarks"></a>備註  
 兩個的並行向量相等，如果有相同數目的項目，且其個別元素擁有相同的值。 反之則為不相等。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_lt"></a>  運算子&lt;運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果運算子左邊的並行向量小於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別中`std`命名空間。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_lt_eq"></a>  運算子&lt;= 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果運算子左邊的並行向量小於或等於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別中`std`命名空間。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_gt"></a>  運算子&gt;運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的並行向量大於運算子右邊的並行向量，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別中`std`命名空間。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_gt_eq"></a>  運算子&gt;= 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
*T*<br/>
並行向量中儲存的項目資料型別。  
  
*A1*<br/>
第一個配置器類型`concurrent_vector`物件。  
  
*A2*<br/>
第二個配置器類型`concurrent_vector`物件。  
  
*_A*<br/>
`concurrent_vector` 類型的物件。  
  
*_KM*<br/>
`concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 若運算子左邊的並行向量大於或等於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別中`std`命名空間。  
  
 這個方法不是相對於其他方法可以修改其中一種並行向量的並行安全`_A`或`_B`。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
