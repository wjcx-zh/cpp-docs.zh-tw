---
title: "transformer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 994cfbaa79594389d8d3b8390bfc46a5aa75a525
ms.lasthandoff: 03/17/2017

---
# <a name="transformer-class"></a>transformer 類別
`transformer` 傳訊區塊是多來源的單一目標排序 `propagator_block`，可以存放無限個不同類型訊息。  
  
## <a name="syntax"></a>語法  
  
```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```   
  
#### <a name="parameters"></a>參數  
 `_Input`  
 緩衝區所接受之訊息的裝載類型。  
  
 `_Output`  
 儲存及傳播緩衝區之訊息的裝載類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[轉換程式](#ctor)|多載。 建構`transformer`傳訊區塊。|  
|[~ transformer 解構函式](#dtor)|終結`transformer`傳訊區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，這提供`transformer`傳訊區塊，將擁有權轉移給呼叫者。|  
|[consume_message](#consume_message)|會使用先前所提供訊息`transformer`和目標，將擁有權轉移給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|新的目標具有已連結到這會通知回撥`transformer`傳訊區塊。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞訊息從`ISource`區塊至此`transformer`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|在輸入訊息上執行轉換器函式。|  
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|先前提供的這一則訊息會保留`transformer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|釋放保留項目之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
|[send_message](#send_message)|以同步方式傳遞訊息從`ISource`區塊至此`transformer`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。|  
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `transformer`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a>accept_message 

 接受的訊息，這提供`transformer`傳訊區塊，將擁有權轉移給呼叫者。  
  
```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
##  <a name="consume_message"></a>consume_message 

 會使用先前所提供訊息`transformer`和目標，將擁有權轉移給呼叫者所保留。  
  
```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件所使用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="link_target_notification"></a>link_target_notification 

 新的目標具有已連結到這會通知回撥`transformer`傳訊區塊。  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```  
  
##  <a name="propagate_message"></a>propagate_message 

 以非同步方式傳遞訊息從`ISource`區塊至此`transformer`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 在輸入訊息上執行轉換器函式。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

 先前提供的這一則訊息會保留`transformer`傳訊區塊。  
  
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
  
##  <a name="send_message"></a>send_message 

 以同步方式傳遞訊息從`ISource`區塊至此`transformer`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。  
  
```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
##  <a name="ctor"></a>轉換程式 

 建構`transformer`傳訊區塊。  
  
```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
 `_Func`  
 為每個接受的訊息就會叫用函式。  
  
 `_PTarget`  
 使用轉換程式連結至目標區塊的指標。  
  
 `_Filter`  
 篩選函式可判斷是否應該接受所提供的訊息。  
  
 `_PScheduler`  
 `Scheduler`傳播的工作的物件`transformer`排定傳訊區塊。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`傳播的工作的物件`transformer`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`_Transform_method`是以簽章仿`_Output (_Input const &)`由此叫用`transformer`傳訊區塊來處理訊息。  
  
 型別`filter_method`是以簽章仿`bool (_Input const &)`由此叫用`transformer`傳訊區塊，以判斷它是否應該接受提供的訊息。  
  
##  <a name="dtor"></a>~ 轉換程式 

 終結`transformer`傳訊區塊。  
  
```
~transformer();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [call 類別](call-class.md)

