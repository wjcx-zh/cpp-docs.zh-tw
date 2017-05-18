---
title: "shared_future 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 84b55dc763d4cd254e4aca55c01690ce5abf0152
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="sharedfuture-class"></a>shared_future 類別
描述「非同步傳回物件」。 相對於 [future](../standard-library/future-class.md) 物件，「非同步提供者」可以與任意數目的 `shared_future` 物件相關聯。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
class shared_future;
```  
  
## <a name="remarks"></a>備註  
 請勿在「空的」`shared_future` 物件上呼叫 `valid`、`operator=` 及建構函式以外的任何方法。  
  
 `shared_future` 物件不會進行同步處理。 在來自多個執行緒的相同物件上呼叫方法會導致資料競爭的情形，因而產生無法預期的結果。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[shared_future](#shared_future)|建構 `shared_future` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get](#get)|擷取以「相關聯的非同步狀態」儲存的結果。|  
|[有效](#valid)|指定物件是否不是空的。|  
|[等候](#wait)|封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。|  
|[wait_for](#wait_for)|封鎖直到相關聯的非同步狀態就緒為止，或直到指定的時間已過為止。|  
|[wait_until](#wait_until)|封鎖直到相關聯的非同步狀態就緒為止，或直到到了指定的時間點為止。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[shared_future::operator=](#op_eq)|指派新的相關聯非同步狀態。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \<未來 >  
  
 **命名空間：** std  
  
##  <a name="get"></a>shared_future:: get
 擷取以「相關聯的非同步狀態」儲存的結果。  
  
```
const Ty& get() const;

Ty& get() const;

void get() const;
```  
  
### <a name="remarks"></a>備註  
 如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。  
  
 在擷取結果之前，此方法會封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。  
  
 就部分特製化 `shared_future<Ty&>` 而言，預存值實際上是對傳遞給「非同步提供者」作為傳回值之物件的參考。  
  
 由於沒有特製化 `shared_future<void>` 適用的任何預存值存在，因此這個方法會傳回 `void`。  
  
##  <a name="op_eq"></a>  shared_future::operator=  
 從指定的物件轉移「相關聯的非同步狀態」。  
  
```
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 `shared_future` 物件。  
  
### <a name="return-value"></a>傳回值  
 `*this`  
  
### <a name="remarks"></a>備註  
 針對第一個運算子，`Right` 在作業完成之後就不再具有相關聯的非同步狀態。  
  
 針對第二個方法，`Right` 會保留它的相關聯非同步狀態。  
  
##  <a name="shared_future"></a>  shared_future::shared_future 建構函式  
 建構 `shared_future` 物件。  
  
```
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 [future](../standard-library/future-class.md) 或 `shared_future` 物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建構沒有「相關聯的非同步狀態」的 `shared_future` 物件。  
  
 第二個建構函式會建構 `shared_future` 物件，並從 `Right` 中轉移相關聯的非同步狀態。 `Right` 已不再具有相關聯的非同步狀態。  
  
 第四個建構函式所建構的 `shared_future` 物件，會具備與 `Right` 相同的相關聯非同步狀態。  
  
##  <a name="valid"></a>shared_future:: valid
 指定物件是否具有「相關聯的非同步狀態」。  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>傳回值  
 如果物件有關聯的非同步狀態，就是 `true`，否則為 `false`。  
  
##  <a name="wait"></a>shared_future:: wait
 封鎖目前的執行緒，直到「相關聯的非同步狀態」就緒為止。  
  
```
void wait() const;
```  
  
### <a name="remarks"></a>備註  
 只有在非同步提供者儲存傳回值或儲存例外狀況後，相關聯的非同步狀態才會就緒。  
  
##  <a name="wait_for"></a>shared_future:: wait_for
 封鎖目前的執行緒，直到相關聯的非同步狀態「就緒」為止，或直到指定的時間已過為止。  
  
```
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>參數  
 `Rel_time`  
 [chrono::duration](../standard-library/duration-class.md) 物件，會指定執行緒封鎖的時間間隔上限。  
  
### <a name="return-value"></a>傳回值  
 [future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。  
  
### <a name="remarks"></a>備註  
 只有在非同步提供者儲存了傳回值或儲存了例外狀況之後，相關聯的非同步狀態才會「就緒」。  
  
##  <a name="wait_until"></a>shared_future:: wait_until
 封鎖目前的執行緒，直到相關聯的非同步狀態「就緒」為止，或直到指定的時間點過後為止。  
  
```
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>參數  
 `Abs_time`  
 [chrono::time_point](../standard-library/time-point-class.md) 物件，會指定可將執行緒解除封鎖的時間。  
  
### <a name="return-value"></a>傳回值  
 [future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。  
  
### <a name="remarks"></a>備註  
 只有在非同步提供者儲存傳回值或儲存例外狀況後，相關聯的非同步狀態才會就緒。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)




