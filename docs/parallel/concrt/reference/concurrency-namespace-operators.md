---
title: "concurrency 命名空間運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 322c95da1774cb0b1d621a46c74125f435ebfbc4
ms.lasthandoff: 03/17/2017

---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空間運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|  
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|  
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)|  
  
##  <a name="operator_lor"></a>運算子 | |運算子  
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
 `ReturnType`  
 所傳回工作的類型。  
  
 `lhs`  
 合併至所產生工作的第一個工作。  
  
 `rhs`  
 合併至所產生工作的第二個工作。  
  
### <a name="return-value"></a>傳回值  
 在任一個輸入工作順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。  
  
### <a name="remarks"></a>備註  
 如果兩個工作都取消或擲回例外狀況，則傳回的工作會以已取消狀態完成，而且其中一個例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。  
  
##  <a name="operator_amp_amp"></a>運算子&amp;&amp;運算子  
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
 `ReturnType`  
 所傳回工作的類型。  
  
 `lhs`  
 合併至所產生工作的第一個工作。  
  
 `rhs`  
 合併至所產生工作的第二個工作。  
  
### <a name="return-value"></a>傳回值  
 會在兩個輸入工作都順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。  
  
### <a name="remarks"></a>備註  
 如果其中一個工作取消或擲回例外狀況，則傳回的工作會在已取消狀態中提早完成，而且例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。  
  
##  <a name="operator_eq_eq"></a>運算子 = = 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果運算子左邊的並行向量和相等運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 如果有相同數目的項目，且個別元素擁有相同的值，兩個並行向量相等。 反之則為不相等。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_neq"></a>運算子 ！ = 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果並行向量是否不相等。`false`並行向量是否相等。  
  
### <a name="remarks"></a>備註  
 如果有相同數目的項目，且個別元素擁有相同的值，兩個並行向量相等。 反之則為不相等。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_lt"></a>運算子&lt;運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果運算子左邊的並行向量小於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別`std`命名空間。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_lt_eq"></a>運算子&lt;= 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果運算子左邊的並行向量是否小於或等於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別`std`命名空間。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_gt"></a>運算子&gt;運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的並行向量大於運算子右邊的並行向量，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別`std`命名空間。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
##  <a name="operator_gt_eq"></a>運算子&gt;= 運算子  
 測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 儲存在並行向量的項目資料型別。  
  
 `A1`  
 第一個配置器類型`concurrent_vector`物件。  
  
 `A2`  
 第二個配置器類型`concurrent_vector`物件。  
  
 `_A`  
 `concurrent_vector` 類型的物件。  
  
 `_B`  
 `concurrent_vector` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果運算子左邊的並行向量大於或等於運算子; 右邊的並行向量否則`false`。  
  
### <a name="remarks"></a>備註  
 此運算子的行為等同於對等的運算子，如`vector`類別`std`命名空間。  
  
 這個方法不相對於其他方法可以修改其中一個的並行向量的並行安全`_A`或`_B`。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

