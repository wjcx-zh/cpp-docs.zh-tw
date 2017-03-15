---
title: "future 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future
dev_langs:
- C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6de4fecd3f5f65ac48cbb49f2ed4f874f4283487
ms.lasthandoff: 02/24/2017

---
# <a name="future-class"></a>future 類別
描述「非同步傳回物件」。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
class future;
```  
  
## <a name="remarks"></a>備註  
 每個標準「非同步提供者」都會傳回一個類型是此範本之具現化的物件。 `future` 物件會提供其關聯的非同步提供者的唯一存取途徑。 如果您需要多個與相同非同步提供者關聯的非同步傳回物件，請將 `future` 物件複製到 [shared_future](../standard-library/shared-future-class.md) 物件。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[future::future 建構函式](#future__future_constructor)|建構 `future` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[future::get](#future__get_method)|擷取以相關的非同步狀態儲存的結果。|  
|[future::share](#future__share_method)|將物件轉換為 `shared_future`。|  
|[future::valid](#future__valid_method)|指定物件是否不是空的。|  
|[future::wait](#future__wait_method)|封鎖目前的執行緒，直到相關的非同步狀態變成就緒為止。|  
|[future::wait_for](#future__wait_for_method)|封鎖直到相關的非同步狀態變成就緒為止，或直到指定的時間已過為止。|  
|[future::wait_until](#future__wait_until_method)|封鎖直到相關的非同步狀態變成就緒為止，或直到到了指定的時間點為止。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[future::operator=](#future__operator_eq)|從指定的物件轉移相關的非同步狀態。|  
  
## <a name="requirements"></a>需求  
 **標頭：**future  
  
 **命名空間：** std  
  
##  <a name="a-namefuturefutureconstructora--futurefuture-constructor"></a><a name="future__future_constructor"></a>  future::future 建構函式  
 建構 `future` 物件。  
  
```
future() noexcept;
future(future&& Other) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Other`  
 `future` 物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建構沒有任何相關非同步狀態的 `future` 物件。  
  
 第二個建構函式建構 `future` 物件並從 `Other` 中轉移關聯的非同步狀態。 `Other` 已不再具有相關的非同步狀態。  
  
##  <a name="a-namefuturegetmethoda--futureget"></a><a name="future__get_method"></a>  future::get  
 擷取以相關的非同步狀態儲存的結果。  
  
```
Ty get();
```  
  
### <a name="return-value"></a>傳回值  
 如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。  
  
### <a name="remarks"></a>備註  
 在擷取結果之前，此方法會封鎖目前的執行緒，直到相關的非同步狀態變成就緒為止。  
  
 就部分特製化 `future<Ty&>` 而言，預存值實際上是對傳遞給非同步提供者作為傳回值之物件的參考。  
  
 由於沒有特製化 `future<void>` 適用的任何預存值存在，因此這個方法會傳回 `void`。  
  
 在其他特製化中，此方法會從預存值中移動其傳回值。 因此，請只呼叫此方法一次。  
  
##  <a name="a-namefutureoperatoreqa--futureoperator"></a><a name="future__operator_eq"></a>  future::operator=  
 從指定的物件轉移相關的非同步狀態。  
  
```
future& operator=(future&& Right) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 `future` 物件。  
  
### <a name="return-value"></a>傳回值  
 `*this`  
  
### <a name="remarks"></a>備註  
 在轉移之後，`Right` 便不再具有相關的非同步狀態。  
  
##  <a name="a-namefuturesharemethoda--futureshare"></a><a name="future__share_method"></a>  future::share  
 將物件轉換為 [shared_future](../standard-library/shared-future-class.md) 物件。  
  
```
shared_future<Ty> share();
```  
  
### <a name="return-value"></a>傳回值  
 `shared_future(move(*this))`  
  
##  <a name="a-namefuturevalidmethoda--futurevalid"></a><a name="future__valid_method"></a>  future::valid  
 指定物件是否具有相關的非同步狀態。  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>傳回值  
 如果物件有關聯的非同步狀態，就是 `true`，否則為 `false`。  
  
##  <a name="a-namefuturewaitmethoda--futurewait"></a><a name="future__wait_method"></a>  future::wait  
 封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止。  
  
```cpp  
void wait() const;
```  
  
### <a name="remarks"></a>備註  
 相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成「就緒」。  
  
##  <a name="a-namefuturewaitformethoda--futurewaitfor"></a><a name="future__wait_for_method"></a>  future::wait_for  
 封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止，或直到指定的時間間隔已過為止。  
  
```
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>參數  
 `Rel_time`  
 [chrono::duration](../standard-library/duration-class.md) 物件，會指定執行緒封鎖的時間間隔上限。  
  
### <a name="return-value"></a>傳回值  
 [future_status](../standard-library/future-enums.md#future_status_enumeration)，會指出傳回的原因。  
  
### <a name="remarks"></a>備註  
 相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成就緒。  
  
##  <a name="a-namefuturewaituntilmethoda--futurewaituntil"></a><a name="future__wait_until_method"></a>  future::wait_until  
 封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止，或直到指定的時間點過後為止。  
  
```cpp  
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>參數  
 `Abs_time`  
 [chrono::time_point](../standard-library/time-point-class.md) 物件，會指定可將執行緒解除封鎖的時間。  
  
### <a name="return-value"></a>傳回值  
 [future_status](../standard-library/future-enums.md#future_status_enumeration)，會指出傳回的原因。  
  
### <a name="remarks"></a>備註  
 相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成「就緒」。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)




