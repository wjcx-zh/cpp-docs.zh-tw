---
title: "join 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25a65dae7b030cc1728194cce5d989c34fa06667
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
 `T`  
 訊息的裝載類型加入，且由區塊的傳播。  
  
 `_Jtype`  
 此種類的`join`區塊這有`greedy`或`non_greedy`  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[join](#ctor)|多載。 建構`join`傳訊區塊。|  
|[~ join 解構函式](#dtor)|終結`join`區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，有提供這`join`傳訊區塊，將擁有權傳送給呼叫者。|  
|[consume_message](#consume_message)|取用先前所提供的訊息`join`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|告知新目標的已連結至這個回呼`join`傳訊區塊。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞訊息從`ISource`至此區塊`join`傳訊區塊。 所叫用`propagate`方法，由來源區塊呼叫時。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|建構輸出訊息時，它們具有所有傳播訊息包含每個來源的輸入的訊息。 送出此輸出訊息，每個目標。|  
|[release_message](#release_message)|釋放先前訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|由此先前提供的訊息會保留`join`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|釋放保留項目之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a>accept_message 

 接受的訊息，有提供這`join`傳訊區塊，將擁有權傳送給呼叫者。  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
##  <a name="consume_message"></a>consume_message 

 取用先前所提供的訊息`join`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被取用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="ctor"></a>聯結 

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
 `_NumInputs`  
 數目輸入這`join`區塊仍能繼續。  
  
 `_Filter`  
 篩選函數用來決定是否應該接受所提供的訊息。  
  
 `_PScheduler`  
 `Scheduler`物件所在的傳播工作`join`排定傳訊區塊。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`物件所在的傳播工作`join`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`filter_method`是函式簽章`bool (T const &)`由此叫用`join`傳訊區塊，以判斷它是否應該接受提供的訊息。  
  
##  <a name="dtor"></a>~ 聯結 

 終結`join`區塊。  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a>link_target_notification 

 告知新目標的已連結至這個回呼`join`傳訊區塊。  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a>propagate_message 

 以非同步方式傳遞訊息從`ISource`至此區塊`join`傳訊區塊。 所叫用`propagate`方法，由來源區塊呼叫時。  
  
```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 供應項目訊息的來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 建構輸出訊息時，它們具有所有傳播訊息包含每個來源的輸入的訊息。 送出此輸出訊息，每個目標。  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a>release_message 

 釋放先前訊息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件時釋放。  
  
##  <a name="reserve_message"></a>reserve_message 

 由此先前提供的訊息會保留`join`傳訊區塊。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果訊息已成功保留，`false`否則。  
  
### <a name="remarks"></a>備註  
 之後`reserve`呼叫時，如果它傳回`true`，`consume`或`release`必須呼叫需要或釋出訊息的擁有權。  
  
##  <a name="resume_propagation"></a>resume_propagation 

 釋放保留項目之後，請繼續傳播。  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [choice 類別](choice-class.md)   
 [multitype_join 類別](multitype-join-class.md)
