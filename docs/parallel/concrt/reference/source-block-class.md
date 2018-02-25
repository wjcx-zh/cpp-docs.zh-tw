---
title: "source_block 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61b79d716aa836c14e18d9c0ac20210526b7fd52
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="sourceblock-class"></a>source_block 類別
`source_block` 類別是僅限來源區塊的抽象基底類別。 類別會提供基本連結管理功能與常見的錯誤檢查功能。  
  
## <a name="syntax"></a>語法  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>參數  
 `_TargetLinkRegistry`  
 要用於保留目標連結連結登錄。  
  
 `_MessageProcessorType`  
 針對訊息處理的處理器類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`target_iterator`|查核連接的目標迭代器。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[source_block](#ctor)|建構 `source_block` 物件。|  
|[~ source_block 解構函式](#dtor)|終結`source_block`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept](#accept)|接受的訊息，有提供這`source_block`物件，將擁有權傳送給呼叫者。|  
|[acquire_ref](#acquire_ref)|取得這個參考計數`source_block`物件，以防止刪除。|  
|[consume](#consume)|會使用先前提供由此訊息`source_block`物件且已成功保留目標，將擁有權傳送給呼叫者。|  
|[link_target](#link_target)|將目標區塊連結至這個`source_block`物件。|  
|[release](#release)|釋放先前成功的訊息保留。|  
|[release_ref](#release_ref)|釋放此參考計數`source_block`物件。|  
|[reserve](#reserve)|由此先前提供的訊息會保留`source_block`物件。|  
|[unlink_target](#unlink_target)|取消連結的目標區塊，從這個`source_block`物件。|  
|[unlink_targets](#unlink_targets)|取消連結所有目標區塊，從這個`source_block`物件。 (覆寫[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|當在衍生類別中覆寫時，可以接受來源所提供的訊息。 訊息區塊應該覆寫此方法以驗證`_MsgId`，並傳回訊息。|  
|[async_send](#async_send)|非同步訊息排入佇列而啟動的傳播工作，如果這已經未完成|  
|[consume_message](#consume_message)|在衍生類別中覆寫時，會使用先前保留的訊息。|  
|[enable_batched_processing](#enable_batched_processing)|啟用這個區塊的批次處理。|  
|[initialize_source](#initialize_source)|初始化`message_propagator`在這個`source_block`。|  
|[link_target_notification](#link_target_notification)|告知新目標的已連結至這個回呼`source_block`物件。|  
|[process_input_messages](#process_input_messages)|處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用|  
|[propagate_output_messages](#propagate_output_messages)|將訊息傳播至目標。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|當在衍生類別中覆寫時，會傳播至任何或所有連結的目標指定的訊息。 這是主要傳播常式之訊息區塊。|  
|[release_message](#release_message)|當在衍生類別中覆寫時，釋放先前訊息保留。|  
|[remove_targets](#remove_targets)|移除這個來源區塊的所有目標連結。 這應該從解構函式呼叫。|  
|[reserve_message](#reserve_message)|當在衍生類別中覆寫時，會保留先前提供的這一則訊息`source_block`物件。|  
|[resume_propagation](#resume_propagation)|當在衍生類別中覆寫時，會繼續傳播之後已釋放保留。|  
|[sync_send](#sync_send)|同步訊息排入佇列，並啟動的傳播工作，如果這已經不做。|  
|[unlink_target_notification](#unlink_target_notification)|告知目標已取消從這個回呼`source_block`物件。|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|等候所有完成的非同步傳播。 這項 （propagator block） 特定微調等候用於訊息區塊的解構函式，以確定所有非同步傳播已完成，然後再終結區塊的時間。|  
  
## <a name="remarks"></a>備註  
 訊息區塊應衍生自這個區塊，以充分利用連結管理與這個類別所提供的同步處理。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="accept"></a> 接受 

 接受的訊息，有提供這`source_block`物件，將擁有權傳送給呼叫者。  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標`accept`方法。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
 `accept`由此所提供的訊息時，方法呼叫目標`ISource`區塊。 訊息指標傳回可能不同於傳遞給`propagate`方法`ITarget`封鎖，如果此來源決定要建立一份訊息。  
  
##  <a name="accept_message"></a> accept_message 

 當在衍生類別中覆寫時，可以接受來源所提供的訊息。 訊息區塊應該覆寫此方法以驗證`_MsgId`，並傳回訊息。  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 執行階段物件身分識別的`message`物件。  
  
### <a name="return-value"></a>傳回值  
 呼叫端現在具有的擁有權的訊息指標。  
  
### <a name="remarks"></a>備註  
 若要傳送擁有權，應該會傳回原始訊息指標。 若要維護的擁有權，一份訊息內容必須進行並傳回。  
  
##  <a name="acquire_ref"></a> acquire_ref 

 取得這個參考計數`source_block`物件，以防止刪除。  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`ITarget`連結到這個期間的來源物件`link_target`方法。  
  
##  <a name="async_send"></a> async_send 

 非同步訊息排入佇列而啟動的傳播工作，如果這已經未完成  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 指標`message`以非同步方式傳送物件。  
  
##  <a name="consume"></a> 使用 

 會使用先前提供由此訊息`source_block`物件且已成功保留目標，將擁有權傳送給呼叫者。  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的保留`message`物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標`consume`方法。  
  
### <a name="return-value"></a>傳回值  
 指標`message`物件，呼叫端現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
 方法會擲回[bad_target](bad-target-class.md)例外狀況如果參數`_PTarget`不表示呼叫的目標`reserve`。  
  
 `consume`方法很類似`accept`，但必須一律加上呼叫`reserve`傳回`true`。  
  
##  <a name="consume_message"></a> consume_message 

 在衍生類別中覆寫時，會使用先前保留的訊息。  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被取用。  
  
### <a name="return-value"></a>傳回值  
 呼叫端現在具有的擁有權的訊息指標。  
  
### <a name="remarks"></a>備註  
 類似於`accept`，但呼叫一律置於`reserve`。  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 啟用這個區塊的批次處理。  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a> initialize_source 

 初始化`message_propagator`在這個`source_block`。  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>參數  
 `_PScheduler`  
 要用於排程工作排程器。  
  
 `_PScheduleGroup`  
 要用於排程工作的排程群組。  
  
##  <a name="link_target"></a> link_target 

 將目標區塊連結至這個`source_block`物件。  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標`ITarget`區塊連結至這個`source_block`物件。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
##  <a name="link_target_notification"></a> link_target_notification 

 告知新目標的已連結至這個回呼`source_block`物件。  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a> process_input_messages 

 處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages 

 將訊息傳播至目標。  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 當在衍生類別中覆寫時，會傳播至任何或所有連結的目標指定的訊息。 這是主要傳播常式之訊息區塊。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 要傳播訊息指標。  
  
##  <a name="release"></a> 發行 

 釋放先前成功的訊息保留。  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的保留`message`物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標`release`方法。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
 方法會擲回[bad_target](bad-target-class.md)例外狀況如果參數`_PTarget`不表示呼叫的目標`reserve`。  
  
##  <a name="release_message"></a> release_message 

 當在衍生類別中覆寫時，釋放先前訊息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件時釋放。  
  
##  <a name="release_ref"></a> release_ref 

 釋放此參考計數`source_block`物件。  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 正在呼叫這個方法的目標區塊的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`ITarget`要從這個來源取消連結的物件。 來源區塊，才能釋放任何資源保留給目標區塊。  
  
##  <a name="remove_targets"></a> remove_targets 

 移除這個來源區塊的所有目標連結。 這應該從解構函式呼叫。  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a> 保留 

 由此先前提供的訊息會保留`source_block`物件。  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`所提供的`message`物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標`reserve`方法。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已成功保留，`false`否則。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
 在您呼叫後`reserve`，如果成功，您必須呼叫`consume`或`release`才能採取或放棄擁有的訊息，分別。  
  
##  <a name="reserve_message"></a> reserve_message 

 當在衍生類別中覆寫時，會保留先前提供的這一則訊息`source_block`物件。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
 `runtime_object_identity`的`message`物件被保留。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已成功保留，`false`否則。  
  
### <a name="remarks"></a>備註  
 之後`reserve`呼叫時，如果它傳回`true`，`consume`或`release`必須呼叫需要或釋出訊息的擁有權。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 當在衍生類別中覆寫時，會繼續傳播之後已釋放保留。  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a> source_block 

 建構 `source_block` 物件。  
  
```
source_block();
```  
  
##  <a name="dtor"></a> ~source_block 

 終結`source_block`物件。  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a> sync_send 

 同步訊息排入佇列，並啟動的傳播工作，如果這已經不做。  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 指標`message`要以同步方式傳送物件。  
  
##  <a name="unlink_target"></a> unlink_target 

 取消連結的目標區塊，從這個`source_block`物件。  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標`ITarget`從此取消連結的區塊`source_block`物件。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_PTarget`是`NULL`。  
  
##  <a name="unlink_target_notification"></a> unlink_target_notification 

 告知目標已取消從這個回呼`source_block`物件。  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 `ITarget`已取消連結的區塊。  
  
##  <a name="unlink_targets"></a> unlink_targets 

 取消連結所有目標區塊，從這個`source_block`物件。  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends 

 等候所有完成的非同步傳播。 這項 （propagator block） 特定微調等候用於訊息區塊的解構函式，以確定所有非同步傳播已完成，然後再終結區塊的時間。  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ISource 類別](isource-class.md)
