---
title: completion_future 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6aa7e9c160a7bedc6eed58a63c07ae7bb65913
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="completionfuture-class"></a>completion_future 類別
表示未來對應 c + + AMP 的非同步作業。  
  
### <a name="syntax"></a>語法  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[completion_future 建構函式](#ctor)|初始化 `completion_future` 類別的新執行個體。|  
|[~ completion_future 解構函式](#dtor)|終結`completion_future`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get](#get)|等候直到相關聯的非同步作業完成為止。|  
|[then](#then)|鏈結的回呼函式物件`completion_future`關聯的非同步作業執行完成時要執行的物件。|  
|[to_task](#to_task)|傳回`task`對應至相關聯的非同步作業的物件。|  
|[valid](#valid)|取得布林值，指出物件是否與非同步作業相關聯。|  
|[等候](#wait)|相關聯的非同步作業完成之前的區塊。|  
|[wait_for](#wait_for)|封鎖，直到相關聯的非同步作業完成或所指定的時間`_Rel_time`過了。|  
|[wait_until](#wait_until)|封鎖，直到相關聯的非同步作業完成或直到目前的時間超過指定的值`_Abs_time`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator std::shared_future\<void>](#operator_shared_future)|會隱含地轉換`completion_future`物件`std::shared_future`物件。|  
|[operator=](#operator_eq)|將指定的內容複製`completion_future`成這一個物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `completion_future`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** concurrency  


## <a name="ctor"></a> completion_future 

初始化 `completion_future` 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `completion_future`複製或移動的物件。  
  
### <a name="overloads-list"></a>多載清單  
  
|名稱|描述|  
|----------|-----------------|  
|`completion_future();`|初始化的新執行個體`completion_future`類別|  
|`completion_future(const completion_future& _Other);`|初始化的新執行個體`completion_future`藉由複製建構函式的類別。|  
|`completion_future(completion_future&& _Other);`|初始化的新執行個體`completion_future`移動建構函式的類別。|  
  
## <a name="get"></a> 取得 

等候直到相關聯的非同步作業完成為止。 如果其中一個非同步作業期間發生，就會擲回的預存的例外狀況。  
  
### <a name="syntax"></a>語法  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a> operator std::shared_future<void> 

會隱含地轉換`completion_future`物件`std::shared_future`物件。  
  
### <a name="syntax"></a>語法  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `std::shared_future` 物件。  
  
## <a name="operator_eq"></a> 運算子 = 

將指定的內容複製`completion_future`成這一個物件。  
  
### <a name="syntax"></a>語法  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 要複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`completion_future`物件。  
  
## <a name="overloads-list"></a>多載清單  
  
|名稱|描述|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|將指定的內容複製`completion_future`物件到這裡，使用的深層複本。|  
|`completion_future& operator=(completion_future&& _Other);`|將指定的內容複製`completion_future`成這一個，使用一個移動指派的物件。|  
  
## <a name="then"></a> 然後 

鏈結的回呼函式物件`completion_future`關聯的非同步作業執行完成時要執行的物件。  
  
### <a name="syntax"></a>語法  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>參數  
 `_Functor`  
 回呼仿函式。  
  
 `_Func`  
 回呼函式物件。  
  
## <a name="to_task"></a> to_task 

傳回`task`對應至相關聯的非同步作業的物件。  
  
### <a name="syntax"></a>語法  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`task`對應至相關聯的非同步作業的物件。  
  
## <a name="valid"></a> 有效 

取得布林值，該值會指出物件是否與非同步作業相關聯。  
  
### <a name="syntax"></a>語法  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果物件是非同步作業; 相關聯否則， `false`。  
  
## <a name="wait"></a> 等候 

相關聯的非同步作業完成之前的區塊。  
  
### <a name="syntax"></a>語法  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a> wait_for 

封鎖，直到相關聯的非同步作業完成或所指定的時間`_Rel_time`過了。  
  
### <a name="syntax"></a>語法  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>參數  
 `_Rep`  
 表示刻度數目的算術類型。  
  
 `_Period`  
 Std::ratio，表示每個刻度經過的秒數字。  
  
 `_Rel_time`  
 最大等待作業完成的時間量。  
  
### <a name="return-value"></a>傳回值  
 會傳回：  
  
-   `std::future_status::deferred` 如果關聯的非同步作業並未執行。  
  
-   `std::future_status::ready` 如果關聯的非同步作業已完成。  
  
-   `std::future_status::timeout` 如果指定的時間期限到期為止。  
  
## <a name="wait_until"></a> wait_until 

封鎖，直到相關聯的非同步作業完成或直到目前的時間超過指定的值`_Abs_time`。  
  
### <a name="syntax"></a>語法  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>參數  
 `_Clock`  
 在這個時間點會測量時鐘。  
  
 `_Duration`  
 啟動之後的時間間隔`_Clock`的 epoch，其後函式會逾時。  
  
 `_Abs_time`  
 此函式階段逾時之後的時間點。  
  
### <a name="return-value"></a>傳回值  
 會傳回：  
  
1.  `std::future_status::deferred` 如果關聯的非同步作業並未執行。  
  
2.  `std::future_status::ready` 如果關聯的非同步作業已完成。  
  
3.  `std::future_status::timeout` 如果指定的時間期間已過期。  
  
## <a name="dtor"></a> ~ completion_future 

終結`completion_future`物件。  
  
### <a name="syntax"></a>語法  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
