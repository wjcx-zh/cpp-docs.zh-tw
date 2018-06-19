---
title: overwrite_buffer 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dccde651898bf5ff0986dc2e577a1d2ee5765e3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694192"
---
# <a name="overwritebuffer-class"></a>overwrite_buffer 類別
`overwrite_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，一次能夠存放一個訊息。 新訊息會覆寫先前保留的訊息。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 儲存及緩衝區所傳播之訊息的裝載類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[overwrite_buffer](#ctor)|多載。 建構`overwrite_buffer`傳訊區塊。|  
|[~ overwrite_buffer 解構函式](#dtor)|終結`overwrite_buffer`傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[has_value](#has_value)|檢查是否這`overwrite_buffer`傳訊區塊尚未有值。|  
|[value](#value)|取得參考的訊息儲存在目前裝載`overwrite_buffer`傳訊區塊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受的訊息，有提供這`overwrite_buffer`傳訊區塊，一份訊息傳回給呼叫者。|  
|[consume_message](#consume_message)|取用先前所提供的訊息`overwrite_buffer`傳訊區塊和目標，傳回的訊息複本給呼叫者所保留。|  
|[link_target_notification](#link_target_notification)|告知新目標的已連結至這個回呼`overwrite_buffer`傳訊區塊。|  
|[propagate_message](#propagate_message)|以非同步方式傳遞訊息從`ISource`至此區塊`overwrite_buffer`傳訊區塊。 所叫用`propagate`方法，由來源區塊呼叫時。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|上的芳鄰`message _PMessage`以此`overwrite_buffer`傳訊區塊，並提供其所有連結的目標。|  
|[release_message](#release_message)|釋放先前訊息保留。 (覆寫[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|由此先前提供的訊息會保留`overwrite_buffer`傳訊區塊。 (覆寫[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|釋放保留項目之後，請繼續傳播。 (覆寫[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
|[send_message](#send_message)|以同步方式將傳遞訊息，以從`ISource`至此區塊`overwrite_buffer`傳訊區塊。 所叫用`send`方法，由來源區塊呼叫時。|  
|[supports_anonymous_source](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>備註  
 `overwrite_buffer`傳訊區塊會散佈到其目標其儲存訊息的複本。  
  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 接受的訊息，有提供這`overwrite_buffer`傳訊區塊，一份訊息傳回給呼叫者。  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 `overwrite_buffer`傳訊區塊傳回副本的訊息，其目標，而不是傳送目前保留訊息的擁有權。  
  
##  <a name="consume_message"></a> consume_message 

 取用先前所提供的訊息`overwrite_buffer`傳訊區塊和目標，傳回的訊息複本給呼叫者所保留。  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被取用。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="has_value"></a> has_value 

 檢查是否這`overwrite_buffer`傳訊區塊尚未有值。  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果區塊已接收值，`false`否則。  
  
##  <a name="link_target_notification"></a> link_target_notification 

 告知新目標的已連結至這個回呼`overwrite_buffer`傳訊區塊。  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 新連結的目標指標。  
  
##  <a name="dtor"></a> ~ overwrite_buffer 

 終結`overwrite_buffer`傳訊區塊。  
  
```
~overwrite_buffer();
```  
  
##  <a name="ctor"></a> overwrite_buffer 

 建構`overwrite_buffer`傳訊區塊。  
  
```
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
 `_Filter`  
 篩選函數用來決定是否應該接受所提供的訊息。  
  
 `_PScheduler`  
 `Scheduler`物件所在的傳播工作`overwrite_buffer`排定傳訊區塊。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`物件所在的傳播工作`overwrite_buffer`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`filter_method`是函式簽章`bool (T const &)`由此叫用`overwrite_buffer`傳訊區塊，以判斷它是否應該接受提供的訊息。  
  
##  <a name="propagate_message"></a> propagate_message 

 以非同步方式傳遞訊息從`ISource`至此區塊`overwrite_buffer`傳訊區塊。 所叫用`propagate`方法，由來源區塊呼叫時。  
  
```
virtual message_status propagate_message(
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
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 上的芳鄰`message _PMessage`以此`overwrite_buffer`傳訊區塊，並提供其所有連結的目標。  
  
```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 指標`message`物件這個`overwrite_buffer`已取得的擁有權。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫中的目前訊息`overwrite_buffer`新接受訊息`_PMessage`。  
  
##  <a name="send_message"></a> send_message 

 以同步方式將傳遞訊息，以從`ISource`至此區塊`overwrite_buffer`傳訊區塊。 所叫用`send`方法，由來源區塊呼叫時。  
  
```
virtual message_status send_message(
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
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
##  <a name="release_message"></a> release_message 

 釋放先前訊息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件時釋放。  
  
##  <a name="reserve_message"></a> reserve_message 

 由此先前提供的訊息會保留`overwrite_buffer`傳訊區塊。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被保留。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已成功保留，`false`否則。  
  
### <a name="remarks"></a>備註  
 之後`reserve`呼叫時，如果它傳回`true`，`consume`或`release`必須呼叫需要或釋出訊息的擁有權。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 釋放保留項目之後，請繼續傳播。  
  
```
virtual void resume_propagation();
```  
  
##  <a name="value"></a> 值 

 取得參考的訊息儲存在目前裝載`overwrite_buffer`傳訊區塊。  
  
```
T value();
```  
  
### <a name="return-value"></a>傳回值  
 目前儲存訊息的裝載。  
  
### <a name="remarks"></a>備註  
 中儲存的值`overwrite_buffer`無法在這個方法會傳回之後，立即變更。 這個方法會等候訊息到達時，如果目前沒有任何訊息儲存在`overwrite_buffer`。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [unbounded_buffer 類別](unbounded-buffer-class.md)   
 [single_assignment 類別](single-assignment-class.md)
