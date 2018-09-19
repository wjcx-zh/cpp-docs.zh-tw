---
title: 呼叫類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 585a490ec64152a1268b7707971ea94e69bf9fbf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109713"
---
# <a name="call-class"></a>call 類別
`call` 傳訊區塊是一個多來源的排序 `target_block`，它在接收訊息時會叫用指定的函式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>參數  
*T*<br/>
傳播到此區塊的訊息的裝載類型。  
  
*_FunctorType*<br/>
這個區塊可以接受的函式的簽章。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[呼叫](#ctor)|多載。 建構`call`傳訊區塊。|  
|[~ 呼叫解構函式](#dtor)|終結`call`傳訊區塊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|輸入訊息上執行的呼叫函式。|  
|[process_message](#process_message)|處理訊息，已接受此`call`傳訊區塊。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞的訊息`ISource`至此區塊`call`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。|  
|[send_message](#send_message)|以同步方式傳遞的訊息`ISource`至此區塊`call`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。|  
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> 呼叫 

 建構`call`傳訊區塊。  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
*_Func*<br/>
針對每個接受的訊息將會叫用函式。  
  
*篩選 （_f)*<br/>
判斷是否應該接受所提供的訊息篩選器函式。  
  
*_PScheduler*<br/>
`Scheduler`物件的傳播工作在其中`call`傳訊區塊已排程。  
  
*_PScheduleGroup*<br/>
`ScheduleGroup`物件的傳播工作在其中`call`傳訊區塊已排程。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`_Call_method`是仿函式簽章`void (T const &)`由此叫用的所在`call`傳訊區塊處理的訊息。  
  
 型別`filter_method`是仿函式簽章`bool (T const &)`由此叫用的所在`call`傳訊區塊，以判斷是否應該接受接受所提供的訊息。  
  
##  <a name="dtor"></a> ~ 呼叫 

 終結`call`傳訊區塊。  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a> process_input_messages 

 輸入訊息上執行的呼叫函式。  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
要處理的訊息指標。  
  
##  <a name="process_message"></a> process_message 

 處理訊息，已接受此`call`傳訊區塊。  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
要處理的訊息指標。  
  
##  <a name="propagate_message"></a> propagate_message 

 以非同步方式傳遞的訊息`ISource`至此區塊`call`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
`message` 物件的指標。  
  
*_PSource*<br/>
提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。  
  
##  <a name="send_message"></a> send_message 

 以同步方式傳遞的訊息`ISource`至此區塊`call`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
`message` 物件的指標。  
  
*_PSource*<br/>
提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)表示決定之訊息的目標。  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [transformer 類別](transformer-class.md)
