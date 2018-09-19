---
title: join 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46073d07cbca27256ca169ab94e0fe027bf98b15
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118852"
---
# <a name="join-class"></a>join 類別
`join` 傳訊區塊是單一目標、多來源的排序 `propagator_block`，會與來自其每個來源的 `T` 類型訊息合併。  
  
## <a name="syntax"></a>語法  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>參數  
*T*<br/>
訊息的裝載類型加入，而且由區塊所傳播。  
  
*_Jtype*<br/>
類型的`join`區塊，這是，可能是`greedy`或 `non_greedy`  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[join](#ctor)|多載。 建構`join`傳訊區塊。|  
|[~ join 解構函式](#dtor)|終結`join`區塊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，由此`join`傳訊區塊，將擁有權傳送給呼叫者。|  
|[consume_message](#consume_message)|會使用先前所提供訊息`join`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|通知新目標，已連結至這個回呼`join`傳訊區塊。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞的訊息`ISource`至此區塊`join`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|建構輸出訊息時將它們全部傳播完成訊息，包含來自每個來源的輸入的訊息。 送出的這個輸出訊息至其目標。|  
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|保留先前由此訊息`join`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|保留區釋出之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 接受的訊息，由此`join`傳訊區塊，將擁有權傳送給呼叫者。  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
##  <a name="consume_message"></a> consume_message 

 會使用先前所提供訊息`join`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`的`message`物件被取用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但一律置於呼叫`reserve`。  
  
##  <a name="ctor"></a> 聯結 

 建構`join`傳訊區塊。  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
*_NumInputs*<br/>
數字輸入這樣`join`將允許的區塊。  
  
*篩選 （_f)*<br/>
判斷是否應該接受所提供的訊息篩選器函式。  
  
*_PScheduler*<br/>
`Scheduler`物件的傳播工作在其中`join`傳訊區塊已排程。  
  
*_PScheduleGroup*<br/>
`ScheduleGroup`物件的傳播工作在其中`join`傳訊區塊已排程。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`filter_method`是仿函式簽章`bool (T const &)`由此叫用的所在`join`傳訊區塊，以判斷是否應該接受接受所提供的訊息。  
  
##  <a name="dtor"></a> ~ 聯結 

 終結`join`區塊。  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification 

 通知新目標，已連結至這個回呼`join`傳訊區塊。  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 以非同步方式傳遞的訊息`ISource`至此區塊`join`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。  
  
```
message_status propagate_message(
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
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 建構輸出訊息時將它們全部傳播完成訊息，包含來自每個來源的輸入的訊息。 送出的這個輸出訊息至其目標。  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a> release_message 

 釋放先前的訊息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`的`message`物件被釋放。  
  
##  <a name="reserve_message"></a> reserve_message 

 保留先前由此訊息`join`傳訊區塊。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果已成功保留訊息，`false`否則。  
  
### <a name="remarks"></a>備註  
 在後`reserve`呼叫時，如果它傳回`true`，可以是`consume`或`release`採取，或釋放訊息的擁有權必須先呼叫。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 保留區釋出之後，請繼續傳播。  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [choice 類別](choice-class.md)   
 [multitype_join 類別](multitype-join-class.md)
