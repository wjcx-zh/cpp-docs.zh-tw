---
title: "combinable 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a491f8eef59978808608917531a5237cceacdb21
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="combinable-class"></a>combinable 類別
`combinable<T>` 物件適用於提供資料的執行緒私用複本，在平行演算法期間執行無鎖定的執行緒-本機子運算。 在平行作業結尾處，可以將執行緒私用子運算合併於最終結果。 這個類別可以用來代替共用變數，而且如果該共用變數有許多爭用情形，則可能可以改進效能。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 最後的合併結果的資料型別。 複製建構函式和預設建構函式，必須使用型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[可組合的類別](#ctor)|多載。 建構新`combinable`物件。|  
|[~ combinable 解構函式](#dtor)|終結 `combinable` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[clear](#clear)|清除任何計算的中繼結果，從先前的使用方式。|  
|[combine](#combine)|藉由呼叫提供的結合仿函式會計算從執行緒區域子計算集合的最後一個值。|  
|[combine_each](#combine_each)|藉由呼叫執行緒區域子計算每一次提供的結合仿函式會計算從執行緒區域子計算集合的最後一個值。 最後的結果會累積函式物件。|  
|[本機](#local)|多載。 傳回執行緒私用子運算的參考。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|指派給`combinable`從另一個物件`combinable`物件。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `combinable`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="clear"></a>清除 

 清除任何計算的中繼結果，從先前的使用方式。  
  
```
void clear();
```  
  
##  <a name="ctor"></a>可組合的類別 

 建構新`combinable`物件。  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 初始化仿函式物件的型別。  
  
 `_FnInitialize`  
 函式會初始化每個新的執行緒私用值的型別呼叫`T`。 它必須支援具有簽章的函式呼叫運算子`T ()`。  
  
 `_Copy`  
 將現有`combinable`要複製到這個物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式初始化新的項目類型的預設建構函式`T`。  
  
 第二個建構函式初始化新的項目使用初始化仿函式當做提供`_FnInitialize`參數。  
  
 第三個建構函式是複製建構函式。  
  
##  <a name="dtor"></a>~ 可組合的類別 

 終結 `combinable` 物件。  
  
```
~combinable();
```  
  
##  <a name="combine"></a>結合 

 藉由呼叫提供的結合仿函式會計算從執行緒區域子計算集合的最後一個值。  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用以將兩個執行緒區域子運算結合的函式物件類型。  
  
 `_FnCombine`  
 用來將子運算結合仿函式。 其簽章是`T (T, T)`或`T (const T&, const T&)`，而且必須關聯和交換。  
  
### <a name="return-value"></a>傳回值  
 合併所有這些執行緒私用子運算的最終結果。  
  
##  <a name="combine_each"></a>combine_each 

 藉由呼叫執行緒區域子計算每一次提供的結合仿函式會計算從執行緒區域子計算集合的最後一個值。 最後的結果會累積函式物件。  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用以結合單一的執行緒區域子運算的函式物件類型。  
  
 `_FnCombine`  
 用來結合一個子計算仿函式。 其簽章是`void (T)`或`void (const T&)`，而且必須是關聯式和交換式。  
  
##  <a name="local"></a>本機 

 傳回執行緒私用子運算的參考。  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>參數  
 `_Exists`  
 布林值的參考。 這個引數所參考的布林值會設定為`true`如果子運算已經存在於這個執行緒，且設定為`false`如果這是在此執行緒的第一個子計算。  
  
### <a name="return-value"></a>傳回值  
 執行緒私用子計算參考。  
  
##  <a name="operator_eq"></a>運算子 = 

 指派給`combinable`從另一個物件`combinable`物件。  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>參數  
 `_Copy`  
 將現有`combinable`要複製到這個物件。  
  
### <a name="return-value"></a>傳回值  
 參考`combinable`物件。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

