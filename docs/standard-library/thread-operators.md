---
title: "&lt;thread&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 7e849e8585b372b5b423a6c960aa926ac7d5cfec
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 判斷某個 `thread::id` 物件是否大於或等於另一個。  
  
```cpp  
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 `!(Left < Right)`  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 判斷某個 `thread::id` 物件是否大於另一個。  
  
```cpp  
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 `Right < Left`  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 判斷某個 `thread::id` 物件是否小於或等於另一個。  
  
```cpp  
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 `!(Right < Left)`  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 判斷某個 `thread::id` 物件是否小於另一個。  
  
```cpp  
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 如果 `Left` 在總排序中位於 `Right` 之前，即為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 運算子會定義所有 `thread::id` 物件的總排序。 這些物件可用來做為關聯容器中的索引鍵。  
  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 比較兩個 `thread::id` 物件是否不相等。  
  
```cpp  
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 `!(Left == Right)`  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 比較兩個 `thread::id` 物件是否相等。  
  
```cpp  
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread::id` 物件。  
  
 `Right`  
 右 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個物件代表執行的同一個執行緒，或者這兩個物件都未代表執行的執行緒，即為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 將 `thread::id` 物件的文字表示插入資料流。  
  
```cpp  
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```  
  
### <a name="parameters"></a>參數  
 `Ostr`  
 [basic_ostream](../standard-library/basic-ostream-class.md) 物件。  
  
 `Id`  
 `thread::id` 物件。  
  
### <a name="return-value"></a>傳回值  
 `Ostr`.  
  
### <a name="remarks"></a>備註  
 此函式會將 `Id` 插入 `Ostr`。  
  
 如果有兩個 `thread::id` 物件要比較是否相等，則這些物件插入的文字表示會一樣。  
  
## <a name="see-also"></a>另請參閱  
 [\<thread>](../standard-library/thread.md)




