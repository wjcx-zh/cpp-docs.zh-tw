---
title: "unbounded_buffer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 9a9c44985b1e9475b8760d835e2a8fd45361ea5a
ms.lasthandoff: 03/17/2017

---


`unbounded_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠存放無限個訊息。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   class             _Type  
>  
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;  
```  
  
#### <a name="parameters"></a>參數  
 `_Type`  
 儲存及傳送緩衝區之訊息的裝載類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[unbounded_buffer](#ctor)|多載。 建構`unbounded_buffer`傳訊區塊。|  
|[~ unbounded_buffer 解構函式](#dtor)|終結`unbounded_buffer`傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[清除佇列](#dequeue)|移除項目從`unbounded_buffer`傳訊區塊。|  
|[在佇列中](#enqueue)|將項目加入`unbounded_buffer`傳訊區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，這提供`unbounded_buffer`傳訊區塊，將擁有權轉移給呼叫者。|  
|[consume_message](#consume_message)|會使用先前所提供訊息`unbounded_buffer`傳訊區塊和目標，將擁有權轉移給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|新的目標具有已連結到這會通知回撥`unbounded_buffer`傳訊區塊。|  
|[process_input_messages](#process_input_messages)|數位`message``_PMessage`以此`unbounded_buffer`傳訊區塊，嘗試提供其所有連結的目標。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞訊息從`ISource`區塊至此`unbounded_buffer`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。|  
|[propagate_output_messages](#propagate_output_messages)|數位`message``_PMessage`以此`unbounded_buffer`傳訊區塊，嘗試提供其所有連結的目標。 (覆寫[source_block:: propagate_output_messages](source-block-class.md#propagate_output_messages)。)|  
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|先前提供的這一則訊息會保留`unbounded_buffer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|釋放保留項目之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
|[send_message](#send_message)|以同步方式傳遞訊息從`ISource`區塊至此`unbounded_buffer`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。|  
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  

 如需詳細資訊，請參閱[非同步訊息區](../asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a>accept_message 

 接受的訊息，這提供`unbounded_buffer`傳訊區塊，將擁有權轉移給呼叫者。  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
##  <a name="consume_message"></a>consume_message 

 會使用先前所提供訊息`unbounded_buffer`傳訊區塊和目標，將擁有權轉移給呼叫者所保留。  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件所使用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="dequeue"></a>清除佇列 

 移除項目從`unbounded_buffer`傳訊區塊。  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>傳回值  
 移除訊息的承載`unbounded_buffer`。  
  
##  <a name="enqueue"></a>在佇列中 

 將項目加入`unbounded_buffer`傳訊區塊。  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>參數  
 `_Item`  
 要新增的項目。  
  
### <a name="return-value"></a>傳回值  
 `true`如果項目已接受，`false`否則。  
  
##  <a name="link_target_notification"></a>link_target_notification 

 新的目標具有已連結到這會通知回撥`unbounded_buffer`傳訊區塊。  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 新連結的目標指標。  
  
##  <a name="propagate_message"></a>propagate_message 

 以非同步方式傳遞訊息從`ISource`區塊至此`unbounded_buffer`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md#message_status)目標決定如何處理訊息的指示。  
  
##  <a name="propagate_output_messages"></a>propagate_output_messages 

 數位`message``_PMessage`以此`unbounded_buffer`傳訊區塊，嘗試提供其所有連結的目標。  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>備註  
 如果另一個訊息已預先在這一個`unbounded_buffer`，直到已接受或取用任何先前的訊息不會發生傳播至連結的目標。 第一個連結的目標，以便順利`accept`或`consume`訊息會取得擁有權，並沒有其他目標會再收到訊息。  
  
##  <a name="process_input_messages"></a>process_input_messages 

 數位`message``_PMessage`以此`unbounded_buffer`傳訊區塊，嘗試提供其所有連結的目標。  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
  
##  <a name="release_message"></a>release_message 

 釋放先前的訊息保留。  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被釋放。  
  
##  <a name="reserve_message"></a>reserve_message 

 先前提供的這一則訊息會保留`unbounded_buffer`傳訊區塊。  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
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

 以同步方式傳遞訊息從`ISource`區塊至此`unbounded_buffer`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md#message_status)目標決定如何處理訊息的指示。  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
##  <a name="ctor"></a>unbounded_buffer 

 建構`unbounded_buffer`傳訊區塊。  
  
```  
unbounded_buffer();  
  
unbounded_buffer(  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler,  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup,  
   filter_method const&                 _Filter  
);  
```  
  
### <a name="parameters"></a>參數  
 `_Filter`  
 篩選函式可判斷是否應該接受所提供的訊息。  
  
 `_PScheduler`  
 `Scheduler`傳播的工作的物件`unbounded_buffer`排定傳訊區塊。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`傳播的工作的物件`unbounded_buffer`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`filter_method`是以簽章仿`bool (_Type const &)`由此叫用`unbounded_buffer`傳訊區塊，以判斷它是否應該接受提供的訊息。  
  
##  <a name="dtor"></a>~ unbounded_buffer 

 終結`unbounded_buffer`傳訊區塊。  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [overwrite_buffer 類別](overwrite-buffer-class.md)   
 [single_assignment 類別](single-assignment-class.md)



