---
title: "completion_future 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::completion_future
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: a9a77c3cf3c183021b70789b0e17a6b8ad8d786c
ms.lasthandoff: 02/24/2017

---
# <a name="completionfuture-class"></a>completion_future 類別
表示對應至 c + + AMP 的非同步作業的未來。  
  
### <a name="syntax"></a>語法  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[completion_future 建構函式](#ctor)|初始化 `completion_future` 類別的新執行個體。|  
|[~ completion_future 解構函式](#dtor)|終結`completion_future`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get 方法](#get)|等到關聯的非同步作業完成為止。|  
|[then 方法](#then)|鏈結的回呼函式物件`completion_future`相關聯的非同步作業執行完成時要執行的物件。|  
|[to_task 方法](#to_task)|傳回`task`物件對應至相關聯的非同步作業。|  
|[有效的方法](#valid)|取得布林值，指出物件是否與非同步作業相關聯。|  
|[wait 方法](#wait)|相關聯的非同步作業完成之前的區塊。|  
|[wait_for 方法](#wait_for)|封鎖，直到相關聯的非同步作業完成或所指定的時間`_Rel_time`過了。|  
|[wait_until 方法](#wait_until)|相關聯的非同步作業完成之前，或直到目前的時間超過指定的值會封鎖`_Abs_time`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 std::shared_future\<void > 運算子](#operator_shared_future)|會隱含地轉換`completion_future`物件傳遞給`std::shared_future`物件。|  
|[運算子 = 運算子](#operator_eq)|將指定的內容複製`completion_future`到這裡的物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `completion_future`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間：** concurrency  


## <a name="a-namectora-completionfuture"></a><a name="ctor"></a>completion_future 

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
  
|名稱|說明|  
|----------|-----------------|  
|`completion_future();`|初始化的新執行個體`completion_future`類別|  
|`completion_future(const completion_future& _Other);`|初始化的新執行個體`completion_future`藉由複製建構函式的類別。|  
|`completion_future(completion_future&& _Other);`|初始化的新執行個體`completion_future`移動建構函式的類別。|  
  
## <a name="a-namegeta-get"></a><a name="get"></a>取得 

等到關聯的非同步作業完成為止。 如果其中一個非同步作業期間發生，則會擲回的預存的例外狀況。  
  
### <a name="syntax"></a>語法  
  
```  
void get() const;  
```  
  
## <a name="a-nameoperatorsharedfuturea-operator-stdsharedfuturevoid"></a><a name="operator_shared_future"></a>運算子 std::shared_future<void> 

會隱含地轉換`completion_future`物件傳遞給`std::shared_future`物件。  
  
### <a name="syntax"></a>語法  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `std::shared_future` 物件。  
  
## <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

將指定的內容複製`completion_future`到這裡的物件。  
  
### <a name="syntax"></a>語法  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 要複製的物件。  
  
### <a name="return-value"></a>傳回值  
 參考`completion_future`物件。  
  
## <a name="overloads-list"></a>多載清單  
  
|名稱|說明|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|將指定的內容複製`completion_future`物件到這裡，使用的深層複本。|  
|`completion_future& operator=(completion_future&& _Other);`|將指定的內容複製`completion_future`的話，就使用移動指派到的物件。|  
  
## <a name="a-namethena-then"></a><a name="then"></a>然後 

鏈結的回呼函式物件`completion_future`相關聯的非同步作業執行完成時要執行的物件。  
  
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
  
## <a name="a-nametotaska-totask"></a><a name="to_task"></a>to_task 

傳回`task`物件對應至相關聯的非同步作業。  
  
### <a name="syntax"></a>語法  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`task`物件對應至相關聯的非同步作業。  
  
## <a name="a-namevalida-valid"></a><a name="valid"></a>有效 

取得布林值，該值會指出物件是否與非同步作業相關聯。  
  
### <a name="syntax"></a>語法  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果物件是相關聯的非同步作業。否則， `false`。  
  
## <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

相關聯的非同步作業完成之前的區塊。  
  
### <a name="syntax"></a>語法  
  
```  
void wait() const;  
```  
  
## <a name="a-namewaitfora-waitfor"></a><a name="wait_for"></a>wait_for 

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
 Std::ratio 代表每個刻度經過的秒數。  
  
 `_Rel_time`  
 最大等待作業完成的時間量。  
  
### <a name="return-value"></a>傳回值  
 傳回:  
  
-   `std::future_status::deferred`如果未執行相關聯的非同步作業。  
  
-   `std::future_status::ready`如果關聯的非同步作業已完成。  
  
-   `std::future_status::timeout`如果指定的時段過了。  
  
## <a name="a-namewaituntila-waituntil"></a><a name="wait_until"></a>wait_until 

相關聯的非同步作業完成之前，或直到目前的時間超過指定的值會封鎖`_Abs_time`。  
  
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
 此時間點以測量時間。  
  
 `_Duration`  
 自啟動後的時間間隔`_Clock`的 epoch，其後函式會將逾時。  
  
 `_Abs_time`  
 其後函式將會逾時的時間點。  
  
### <a name="return-value"></a>傳回值  
 傳回:  
  
1.  `std::future_status::deferred`如果未執行相關聯的非同步作業。  
  
2.  `std::future_status::ready`如果關聯的非同步作業已完成。  
  
3.  `std::future_status::timeout`如果指定的時間週期已逾時。  
  
## <a name="a-namedtora-completionfuture"></a><a name="dtor"></a>~ completion_future 

終結`completion_future`物件。  
  
### <a name="syntax"></a>語法  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)

