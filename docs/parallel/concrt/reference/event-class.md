---
title: "事件類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::event
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 22
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
ms.openlocfilehash: abda6512f391b59cb48c8e96a489714ee117ae68
ms.lasthandoff: 02/24/2017

---
# <a name="event-class"></a>event 類別
其為並行執行階段明確察覺的手動重設事件。  
  
## <a name="syntax"></a>語法  
  
```
class event;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[~ event 解構函式](#dtor)|終結事件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[reset 方法](#reset)|重設為未收到信號狀態的事件。|  
|[set 方法](#set)|通知事件。|  
|[wait 方法](#wait)|等待事件發出訊號。|  
|[wait_for_multiple 方法](#wait_for_multiple)|等候變成已收到訊號的多個事件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[timeout_infinite 常數](#timeout_infinite)|值，表示等候應該永遠不會逾時。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `event`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-event"></a><a name="ctor"></a>事件 

 建構新的事件。  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedtora-event"></a><a name="dtor"></a>~ 事件 

 終結事件。  
  
```
~event();
```  
  
### <a name="remarks"></a>備註  
 應該沒有執行緒在等候事件時執行解構函式。 允許事件解構仍在等候的執行緒，會導致未定義的行為發生。  
  
##  <a name="a-namereseta-reset"></a><a name="reset"></a>重設 

 重設為未收到信號狀態的事件。  
  
```
void reset();
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>設定 

 通知事件。  
  
```
void set();
```  
  
### <a name="remarks"></a>備註  
 發出事件訊號會使事件上正在等候的任意數目內容變為可執行。  
  
##  <a name="a-nametimeoutinfinitea-timeoutinfinite"></a><a name="timeout_infinite"></a>timeout_infinite 

 值，表示等候應該永遠不會逾時。  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

 等待事件發出訊號。  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `_Timeout`  
 等候逾時之前，表示毫秒數。 值`COOPERATIVE_TIMEOUT_INFINITE`表示無逾時。  
  
### <a name="return-value"></a>傳回值  
 如果滿意等待結果，值`0`會傳回，否則值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時不變得發出信號的事件。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)]應用程式中，請勿呼叫在 ASTA 執行緒上的 `wait`，因為這個呼叫可能會封鎖目前的執行緒，而且造成應用程式變成沒有回應。  
  
##  <a name="a-namewaitformultiplea-waitformultiple"></a><a name="wait_for_multiple"></a>wait_for_multiple 

 等候變成已收到訊號的多個事件。  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `_PPEvents`  
 陣列，要等候的事件。 在陣列中的事件數目會以`count`參數。  
  
 `count`  
 提供在陣列中的事件計數`_PPEvents`參數。  
  
 `_FWaitAll`  
 如果設定為值`true`，參數會指定陣列中的所有事件都提供在`_PPEvents`參數必須變成收到訊號，以滿足等候。 如果設定為值`false`，它會指定陣列中的任何事件提供在`_PPEvents`參數變成已收到訊號會滿足等候。  
  
 `_Timeout`  
 等候逾時之前，表示毫秒數。 值`COOPERATIVE_TIMEOUT_INFINITE`表示無逾時。  
  
### <a name="return-value"></a>傳回值  
 如果滿意等待結果，在陣列中的索引所提供`_PPEvents`參數滿足等候條件; 否則值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時沒有所滿足的條件。  
  
### <a name="remarks"></a>備註  
 如果參數`_FWaitAll`設定為值`true`函數所傳回的索引，表示所有事件必須滿足等候變成收到都訊號，帶有沒有特殊的意義，只是不是值`COOPERATIVE_WAIT_TIMEOUT`。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)]應用程式中，請勿呼叫在 ASTA 執行緒上的 `wait_for_multiple`，因為這個呼叫可能會封鎖目前的執行緒，而且造成應用程式變成沒有回應。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

