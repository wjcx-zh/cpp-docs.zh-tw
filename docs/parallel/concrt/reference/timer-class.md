---
title: "timer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: 21
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d6dfdc1b03ac2d15aa575c16cbe86968f565c1c1
ms.lasthandoff: 03/17/2017

---
# <a name="timer-class"></a>timer 類別
`timer` 傳訊區塊是單一目標 `source_block`，能夠在經過指定的時間長度或在特定時間間隔，將訊息傳送至它的目標。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 這個區塊的輸出訊息的裝載類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[計時器](#ctor)|多載。 建構`timer`會在特定時間間隔引發指定的訊息的傳訊區塊。|  
|[~ timer 解構函式](#dtor)|終結`timer`傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[暫停](#pause)|停駐點`timer`傳訊區塊。 如果它是重複`timer`傳訊區塊，就可以重新啟動與後續`start()`呼叫。 對於非重複的計時器，這有相同的效果`stop`呼叫。|  
|[start](#start)|啟動`timer`傳訊區塊。 指定在此之後的毫秒數呼叫，就會傳送指定的值做為下游`message`。|  
|[停止](#stop)|停駐點`timer`傳訊區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，這提供`timer`傳訊區塊，將擁有權轉移給呼叫者。|  
|[consume_message](#consume_message)|會使用先前所提供訊息`timer`和目標，將擁有權轉移給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|新的目標具有已連結到這會通知回撥`timer`傳訊區塊。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|嘗試提供所產生的訊息`timer`所有連結的目標區塊。|  
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|先前提供的這一則訊息會保留`timer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|釋放保留項目之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a>accept_message 

 接受的訊息，這提供`timer`傳訊區塊，將擁有權轉移給呼叫者。  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
##  <a name="consume_message"></a>consume_message 

 會使用先前所提供訊息`timer`和目標，將擁有權轉移給呼叫者所保留。  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件所使用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="link_target_notification"></a>link_target_notification 

 新的目標具有已連結到這會通知回撥`timer`傳訊區塊。  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 新連結的目標指標。  
  
##  <a name="pause"></a>暫停 

 停駐點`timer`傳訊區塊。 如果它是重複`timer`傳訊區塊，就可以重新啟動與後續`start()`呼叫。 對於非重複的計時器，這有相同的效果`stop`呼叫。  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 嘗試提供所產生的訊息`timer`所有連結的目標區塊。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```  
  
##  <a name="release_message"></a>release_message 

 釋放先前的訊息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被釋放。  
  
##  <a name="reserve_message"></a>reserve_message 

 先前提供的這一則訊息會保留`timer`傳訊區塊。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被保留。  
  
### <a name="return-value"></a>傳回值  
 `true`如果訊息已成功保留，`false`否則。  
  
### <a name="remarks"></a>備註  
 之後`reserve`呼叫時，如果它傳回`true`，`consume`或`release`必須呼叫採取或釋放訊息的擁有權。  
  
##  <a name="resume_propagation"></a>resume_propagation 

 釋放保留項目之後，請繼續傳播。  
  
```
virtual void resume_propagation();
```  
  
##  <a name="start"></a>啟動 

 啟動`timer`傳訊區塊。 指定在此之後的毫秒數呼叫，就會傳送指定的值做為下游`message`。  
  
```
void start();
```  
  
##  <a name="stop"></a>停止 

 停駐點`timer`傳訊區塊。  
  
```
void stop();
```  
  
##  <a name="ctor"></a>計時器 

 建構`timer`會在特定時間間隔引發指定的訊息的傳訊區塊。  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>參數  
 `_Ms`  
 在下游傳播至指定的訊息啟動的呼叫必須經過的毫秒數。  
  
 `value`  
 計時器耗盡時下游傳播值。  
  
 `_PTarget`  
 計時器會將訊息傳送目標。  
  
 `_Repeating`  
 如果為 true，表示計時器會定期引發每`_Ms`毫秒。  
  
 `_Scheduler`  
 `Scheduler`傳播的工作的物件`timer`傳訊區塊已排程已排程。  
  
 `_ScheduleGroup`  
 `ScheduleGroup`傳播的工作的物件`timer`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定執行階段會使用預設排程器`_Scheduler`或`_ScheduleGroup`參數。  
  
##  <a name="dtor"></a>~ 計時器 

 終結`timer`傳訊區塊。  
  
```
~timer();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

