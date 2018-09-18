---
title: unbounded_buffer 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 615043cd12825fd7bfd23442c3913b6d82b0094e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027541"
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
*類型 （_t)*<br/>
儲存及緩衝區所傳播之訊息的裝載類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[unbounded_buffer](#ctor)|多載。 建構`unbounded_buffer`傳訊區塊。|  
|[~ unbounded_buffer 解構函式](#dtor)|終結`unbounded_buffer`傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[dequeue](#dequeue)|移除項目從`unbounded_buffer`傳訊區塊。|  
|[enqueue](#enqueue)|將項目加入`unbounded_buffer`傳訊區塊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，由此`unbounded_buffer`傳訊區塊，將擁有權傳送給呼叫者。|  
|[consume_message](#consume_message)|會使用先前所提供訊息`unbounded_buffer`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|通知新目標，已連結至這個回呼`unbounded_buffer`傳訊區塊。|  
|[process_input_messages](#process_input_messages)|上的芳鄰`message``_PMessage`以此`unbounded_buffer`傳訊區塊，並嘗試提供給所有連結的目標。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞的訊息`ISource`至此區塊`unbounded_buffer`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。|  
|[propagate_output_messages](#propagate_output_messages)|上的芳鄰`message``_PMessage`以此`unbounded_buffer`傳訊區塊，並嘗試提供給所有連結的目標。 (覆寫[source_block:: propagate_output_messages](source-block-class.md#propagate_output_messages)。)|  
|[release_message](#release_message)|釋放先前的訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|保留先前由此訊息`unbounded_buffer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|保留區釋出之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
|[send_message](#send_message)|以同步方式傳遞的訊息`ISource`至此區塊`unbounded_buffer`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。|  
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  

 如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 接受的訊息，由此`unbounded_buffer`傳訊區塊，將擁有權傳送給呼叫者。  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
##  <a name="consume_message"></a> consume_message 

 會使用先前所提供訊息`unbounded_buffer`傳訊區塊和目標，將擁有權傳送給呼叫者所保留。  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`的`message`物件被取用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但一律置於呼叫`reserve`。  
  
##  <a name="dequeue"></a> 清除佇列 

 移除項目從`unbounded_buffer`傳訊區塊。  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>傳回值  
 移除訊息的承載`unbounded_buffer`。  
  
##  <a name="enqueue"></a> 加入佇列 

 將項目加入`unbounded_buffer`傳訊區塊。  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>參數  
*_Item*<br/>
要新增的項目。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果項目已接受，`false`否則。  
  
##  <a name="link_target_notification"></a> link_target_notification 

 通知新目標，已連結至這個回呼`unbounded_buffer`傳訊區塊。  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>參數  
*_PTarget*<br/>
新連結的目標指標。  
  
##  <a name="propagate_message"></a> propagate_message 

 以非同步方式傳遞的訊息`ISource`至此區塊`unbounded_buffer`傳訊區塊。 它由`propagate`方法中，當呼叫來源區塊。  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
`message` 物件的指標。  
  
*_PSource*<br/>
提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md#message_status)表示決定之訊息的目標。  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages 

 上的芳鄰`message``_PMessage`以此`unbounded_buffer`傳訊區塊，並嘗試提供給所有連結的目標。  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>備註  
 如果另一則訊息已領先中`unbounded_buffer`，已接受或取用任何先前的訊息之前，不會發生傳播給連結的目標。 第一個連結的目標，以便順利`accept`或`consume`訊息會取得擁有權，以及任何其他目標然後取得訊息。  
  
##  <a name="process_input_messages"></a> process_input_messages 

 上的芳鄰`message``_PMessage`以此`unbounded_buffer`傳訊區塊，並嘗試提供給所有連結的目標。  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
正在處理的訊息指標。  
  
##  <a name="release_message"></a> release_message 

 釋放先前的訊息保留。  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`的`message`物件被釋放。  
  
##  <a name="reserve_message"></a> reserve_message 

 保留先前由此訊息`unbounded_buffer`傳訊區塊。  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>參數  
*_MsgId*<br/>
`runtime_object_identity`的`message`物件所保留。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果已成功保留訊息，`false`否則。  
  
### <a name="remarks"></a>備註  
 在後`reserve`呼叫時，如果它傳回`true`，可以是`consume`或`release`採取，或釋放訊息的擁有權必須先呼叫。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 保留區釋出之後，請繼續傳播。  
  
```  
virtual void resume_propagation();  
```  
  
##  <a name="send_message"></a> send_message 

 以同步方式傳遞的訊息`ISource`至此區塊`unbounded_buffer`傳訊區塊。 它由`send`方法中，當呼叫來源區塊。  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>參數  
*_PMessage*<br/>
`message` 物件的指標。  
  
*_PSource*<br/>
提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md#message_status)表示決定之訊息的目標。  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
##  <a name="ctor"></a> unbounded_buffer 

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
*篩選 （_f)*<br/>
判斷是否應該接受所提供的訊息篩選器函式。  
  
*_PScheduler*<br/>
`Scheduler`物件的傳播工作在其中`unbounded_buffer`傳訊區塊已排程。  
  
*_PScheduleGroup*<br/>
`ScheduleGroup`物件的傳播工作在其中`unbounded_buffer`傳訊區塊已排程。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`filter_method`是仿函式簽章`bool (_Type const &)`由此叫用的所在`unbounded_buffer`傳訊區塊，以判斷是否應該接受接受所提供的訊息。  
  
##  <a name="dtor"></a> ~ unbounded_buffer 

 終結`unbounded_buffer`傳訊區塊。  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [overwrite_buffer 類別](overwrite-buffer-class.md)   
 [single_assignment 類別](single-assignment-class.md)


