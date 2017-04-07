---
title: "target_block 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
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
ms.openlocfilehash: 2b098523f08345ef366e724c17b6f35211c39e44
ms.lasthandoff: 03/17/2017

---
# <a name="targetblock-class"></a>target_block 類別
`target_block` 類別是一種抽象基底類別，可提供基本的連結管理功能和僅限目標區塊的錯誤檢查。  
  
## <a name="syntax"></a>語法  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>參數  
 `_SourceLinkRegistry`  
 連結的登錄，以用於保留來源連結。  
  
 `_MessageProcessorType`  
 處理訊息的處理器類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`source_iterator`|迭代器類型`source_link_manager`這個`target_block`物件。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[target_block](#ctor)|建構 `target_block` 物件。|  
|[~ target_block 解構函式](#dtor)|終結`target_block`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[傳播](#propagate)|以非同步方式將訊息從來源區塊傳遞到此目標區塊。|  
|[傳送](#send)|以同步方式將訊息從來源區塊傳遞到此目標區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[async_send](#async_send)|以非同步方式傳送訊息以進行處理。|  
|[decline_incoming_messages](#decline_incoming_messages)|表示區塊應該已拒絕新的訊息。|  
|[enable_batched_processing](#enable_batched_processing)|啟用這個區塊的批次處理。|  
|[initialize_target](#initialize_target)|初始化基底物件。 具體來說，`message_processor`需要初始化物件。|  
|[link_source](#link_source)|將指定的來源區塊會連結到這`target_block`物件。|  
|[process_input_messages](#process_input_messages)|處理收到的輸入訊息。|  
|[process_message](#process_message)|在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。|  
|[propagate_message](#propagate_message)|當在衍生類別中覆寫時，這個方法以非同步方式將訊息傳遞從`ISource`這個區塊`target_block`物件。 它會叫用`propagate`方法，由來源區塊呼叫時。|  
|[register_filter](#register_filter)|註冊將會叫用每個收到的訊息的篩選方法。|  
|[remove_sources](#remove_sources)|等候未處理的非同步傳送作業完成之後，取消連結所有來源。|  
|[send_message](#send_message)|當在衍生類別中覆寫時，這個方法以同步方式將訊息傳遞從`ISource`區塊至此`target_block`物件。 它會叫用`send`方法，由來源區塊呼叫時。|  
|[sync_send](#sync_send)|以同步方式傳送訊息以進行處理。|  
|[unlink_source](#unlink_source)|取消連結指定的來源區塊從此`target_block`物件。|  
|[unlink_sources](#unlink_sources)|取消連結所有來源區塊，從這個`target_block`物件。 (覆寫[itarget:: Unlink_sources](itarget-class.md#unlink_sources)。)|  
|[wait_for_async_sends](#wait_for_async_sends)|等候所有完成的非同步傳播。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="async_send"></a>async_send 

 以非同步方式傳送訊息以進行處理。  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 所傳送的郵件指標。  
  
##  <a name="decline_incoming_messages"></a>decline_incoming_messages 

 表示區塊應該已拒絕新的訊息。  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>備註  
 以確保新的訊息會遭到拒絕，解構函式正在進行時，解構函式會呼叫這個方法。  
  
##  <a name="enable_batched_processing"></a>enable_batched_processing 

 啟用這個區塊的批次處理。  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a>initialize_target 

 初始化基底物件。 具體來說，`message_processor`需要初始化物件。  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>參數  
 `_PScheduler`  
 要用於排程工作排程器。  
  
 `_PScheduleGroup`  
 要用於排程工作的排程群組。  
  
##  <a name="link_source"></a>link_source 

 將指定的來源區塊會連結到這`target_block`物件。  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 指標`ISource`是要連結的區塊。  
  
### <a name="remarks"></a>備註  
 此函式不應該直接呼叫`target_block`物件。 區塊應該一起使用來連接`link_target`方法`ISource`區塊，會叫用`link_source`上對應的目標方法。  
  
##  <a name="process_input_messages"></a>process_input_messages 

 處理收到的輸入訊息。  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 在衍生類別中覆寫時，處理這個 `target_block` 物件接受的訊息。  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a>傳播 

 以非同步方式將訊息從來源區塊傳遞到此目標區塊。  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果`_PMessage`或`_PSource`參數是`NULL`。  
  
##  <a name="propagate_message"></a>propagate_message 

 當在衍生類別中覆寫時，這個方法以非同步方式將訊息傳遞從`ISource`這個區塊`target_block`物件。 它會叫用`propagate`方法，由來源區塊呼叫時。  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="register_filter"></a>register_filter 

 註冊將會叫用每個收到的訊息的篩選方法。  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
 `_Filter`  
 篩選方法。  
  
##  <a name="remove_sources"></a>remove_sources 

 等候未處理的非同步傳送作業完成之後，取消連結所有來源。  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>備註  
 所有的目標區塊應該呼叫這個常式，以移除其解構函式中的來源。  
  
##  <a name="send"></a>傳送 

 以同步方式將訊息從來源區塊傳遞到此目標區塊。  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果`_PMessage`或`_PSource`參數是`NULL`。  
  
 使用`send`方法初始化訊息之外，並傳播網路內的郵件是非常危險，可能會導致死結。  
  
 當`send`傳回時，訊息可能已被接受，並傳輸至目標區塊時，或目標已被拒絕。  
  
##  <a name="send_message"></a>send_message 

 當在衍生類別中覆寫時，這個方法以同步方式將訊息傳遞從`ISource`區塊至此`target_block`物件。 它會叫用`send`方法，由來源區塊呼叫時。  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
### <a name="remarks"></a>備註  
 根據預設，此區塊傳回`declined`除非在衍生類別覆寫。  
  
##  <a name="sync_send"></a>sync_send 

 以同步方式傳送訊息以進行處理。  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 所傳送的郵件指標。  
  
##  <a name="ctor"></a>target_block 

 建構 `target_block` 物件。  
  
```
target_block();
```  
  
##  <a name="dtor"></a>~ target_block 

 終結`target_block`物件。  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a>unlink_source 

 取消連結指定的來源區塊從此`target_block`物件。  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 指標`ISource`要取消連結的區塊。  
  
##  <a name="unlink_sources"></a>unlink_sources 

 取消連結所有來源區塊，從這個`target_block`物件。  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a>wait_for_async_sends 

 等候所有完成的非同步傳播。  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>備註  
 這個方法可供訊息區塊解構函式以確保所有的非同步作業已花時間完成，然後再終結區塊。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ITarget 類別](itarget-class.md)

