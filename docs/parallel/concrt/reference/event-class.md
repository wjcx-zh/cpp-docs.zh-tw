---
title: event 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb02865b20d1603be38192e770eb26627e6900e7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="event-class"></a>event 類別
其為並行執行階段明確察覺的手動重設事件。  
  
## <a name="syntax"></a>語法  
  
```
class event;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[~ event 解構函式](#dtor)|終結事件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[reset](#reset)|事件重設為未收到信號狀態。|  
|[set](#set)|通知事件。|  
|[等候](#wait)|等待事件發出訊號。|  
|[wait_for_multiple](#wait_for_multiple)|等候發出訊號的多個事件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[timeout_infinite](#timeout_infinite)|值，表示等候應該永遠不會逾時。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `event`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> 事件 

 建構新的事件。  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dtor"></a> ~ 事件 

 終結事件。  
  
```
~event();
```  
  
### <a name="remarks"></a>備註  
 應該沒有執行緒正在等候該事件解構函式執行時。 允許事件解構仍在等候的執行緒，會導致未定義的行為發生。  
  
##  <a name="reset"></a> 重設 

 事件重設為未收到信號狀態。  
  
```
void reset();
```  
  
##  <a name="set"></a> 設定 

 通知事件。  
  
```
void set();
```  
  
### <a name="remarks"></a>備註  
 發出事件訊號會使事件上正在等候的任意數目內容變為可執行。  
  
##  <a name="timeout_infinite"></a> timeout_infinite 

 值，表示等候應該永遠不會逾時。  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="wait"></a> 等候 

 等待事件發出訊號。  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `_Timeout`  
 等候逾時之前，請指出毫秒的數。值`COOPERATIVE_TIMEOUT_INFINITE`表示沒有逾時。  
  
### <a name="return-value"></a>傳回值  
 如果已滿足等候，值`0`會傳回，否則值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時不變得發出信號的事件。  
  
> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 應用程式中，請勿呼叫`wait`在 ASTA 執行緒上因為這個呼叫可能會封鎖目前的執行緒，而且可能會導致應用程式變成沒有回應。  
  
##  <a name="wait_for_multiple"></a> wait_for_multiple 

 等候發出訊號的多個事件。  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `_PPEvents`  
 陣列，要等候的事件。 陣列中的事件數目會以`count`參數。  
  
 `count`  
 中提供的陣列內的事件計數`_PPEvents`參數。  
  
 `_FWaitAll`  
 如果設定為值`true`，參數會指定陣列中的所有事件都提供在`_PPEvents`參數必須被通知以滿足等候。 如果設定為值`false`，它會指定陣列中的任何事件提供在`_PPEvents`參數變成有訊號會滿足等候。  
  
 `_Timeout`  
 等候逾時之前，請指出毫秒的數。值`COOPERATIVE_TIMEOUT_INFINITE`表示沒有逾時。  
  
### <a name="return-value"></a>傳回值  
 如果已滿足等候，陣列中的索引所提供`_PPEvents`參數滿足等候條件; 否則值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時沒有滿足條件。  
  
### <a name="remarks"></a>備註  
 如果參數`_FWaitAll`設定為值`true`函數所傳回的索引來指示必須成為所有事件發出都信號，以滿足等候，帶有沒有特殊的意義不是值的事實以外`COOPERATIVE_WAIT_TIMEOUT`。  
  
> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 應用程式中，請勿呼叫`wait_for_multiple`在 ASTA 執行緒上因為這個呼叫可能會封鎖目前的執行緒，而且可能會導致應用程式變成沒有回應。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
