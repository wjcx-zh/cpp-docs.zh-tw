---
title: "propagator_block 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a34d127baf13434435c9ab359cf75b7b93c21f6d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="propagatorblock-class"></a>propagator_block 類別
`propagator_block` 類別是同時為來源和目標之訊息區塊的抽象基底類別。 它結合 `source_block` 和 `target_block` 類別的功能。  
  
## <a name="syntax"></a>語法  
  
```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
 public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>參數  
 `_TargetLinkRegistry`  
 要用於保存目標連結連結登錄中。  
  
 `_SourceLinkRegistry`  
 連結的登錄，以用於保留來源連結。  
  
 `_MessageProcessorType`  
 處理訊息的處理器類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`source_iterator`|迭代器類型`source_link_manager`這個`propagator_block`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[propagator_block](#ctor)|建構 `propagator_block` 物件。|  
|[~ propagator_block 解構函式](#dtor)|終結 `propagator_block` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[傳播](#propagate)|以非同步方式將訊息從來源區塊傳遞到此目標區塊。|  
|[傳送](#send)|以同步方式起始到此區塊的訊息。 由呼叫`ISource`區塊。 此函式完成時，訊息將已傳播到區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[decline_incoming_messages](#decline_incoming_messages)|表示區塊應該已拒絕新的訊息。|  
|[initialize_source_and_target](#initialize_source_and_target)|初始化基底物件。 具體來說，`message_processor`需要初始化物件。|  
|[link_source](#link_source)|將指定的來源區塊連結至這個`propagator_block`物件。|  
|[process_input_messages](#process_input_messages)|處理輸入訊息。 這只適用於衍生自 source_block 的傳播程式區塊 (覆寫[source_block:: process_input_messages](source-block-class.md#process_input_messages)。)|  
|[propagate_message](#propagate_message)|當在衍生類別中覆寫時，這個方法以非同步方式將訊息傳遞從`ISource`區塊至此`propagator_block`物件。 它會叫用`propagate`方法，由來源區塊呼叫時。|  
|[register_filter](#register_filter)|註冊將會叫用每個接收訊息的篩選方法。|  
|[remove_network_links](#remove_network_links)|這會移除所有的來源和目標網路連結`propagator_block`物件。|  
|[send_message](#send_message)|當在衍生類別中覆寫時，這個方法以同步方式將訊息傳遞從`ISource`區塊至此`propagator_block`物件。 它會叫用`send`方法，由來源區塊呼叫時。|  
|[unlink_source](#unlink_source)|取消連結指定的來源區塊從此`propagator_block`物件。|  
|[unlink_sources](#unlink_sources)|取消連結所有來源區塊，從這個`propagator_block`物件。 (覆寫[itarget:: Unlink_sources](itarget-class.md#unlink_sources)。)|  
  
## <a name="remarks"></a>備註  
 若要避免多重繼承，`propagator_block`類別繼承自`source_block`類別和`ITarget`抽象類別。 大部分的功能`target_block`類別會在此複寫。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="decline_incoming_messages"></a>decline_incoming_messages 

 表示區塊應該已拒絕新的訊息。  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>備註  
 以確保新的訊息會遭到拒絕，解構函式正在進行時，解構函式會呼叫這個方法。  
  
##  <a name="initialize_source_and_target"></a>initialize_source_and_target 

 初始化基底物件。 具體來說，`message_processor`需要初始化物件。  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>參數  
 `_PScheduler`  
 要用於排程工作排程器。  
  
 `_PScheduleGroup`  
 要用於排程工作的排程群組。  
  
##  <a name="link_source"></a>link_source 

 將指定的來源區塊連結至這個`propagator_block`物件。  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 指標`ISource`是要連結的區塊。  
  
##  <a name="process_input_messages"></a>process_input_messages 

 處理輸入訊息。 這只對衍生自 source_block 的傳播程式區塊有用  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
  
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
 `propagate`目標區塊所連結的來源區塊會叫用方法。 它佇列處理訊息，如果其中一個不已排入佇列的非同步工作或執行。  
  
 方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果`_PMessage`或`_PSource`參數是`NULL`。  
  
##  <a name="propagate_message"></a>propagate_message 

 當在衍生類別中覆寫時，這個方法以非同步方式將訊息傳遞從`ISource`區塊至此`propagator_block`物件。 它會叫用`propagate`方法，由來源區塊呼叫時。  
  
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
  
##  <a name="ctor"></a>propagator_block 

 建構 `propagator_block` 物件。  
  
```
propagator_block();
```  
  
##  <a name="dtor"></a>~ propagator_block 

 終結 `propagator_block` 物件。  
  
```
virtual ~propagator_block();
```  
  
##  <a name="register_filter"></a>register_filter 

 註冊將會叫用每個接收訊息的篩選方法。  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
 `_Filter`  
 篩選方法。  
  
##  <a name="remove_network_links"></a>remove_network_links 

 這會移除所有的來源和目標網路連結`propagator_block`物件。  
  
```
void remove_network_links();
```  
  
##  <a name="send"></a>傳送 

 以同步方式起始到此區塊的訊息。 由呼叫`ISource`區塊。 此函式完成時，訊息將已傳播到區塊。  
  
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
 這個方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況，如果`_PMessage`或`_PSource`參數是`NULL`。  
  
##  <a name="send_message"></a>send_message 

 當在衍生類別中覆寫時，這個方法以同步方式將訊息傳遞從`ISource`區塊至此`propagator_block`物件。 它會叫用`send`方法，由來源區塊呼叫時。  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
### <a name="remarks"></a>備註  
 根據預設，此區塊傳回`declined`除非在衍生類別覆寫。  
  
##  <a name="unlink_source"></a>unlink_source 

 取消連結指定的來源區塊從此`propagator_block`物件。  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 指標`ISource`要取消連結的區塊。  
  
##  <a name="unlink_sources"></a>unlink_sources 

 取消連結所有來源區塊，從這個`propagator_block`物件。  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [source_block 類別](source-block-class.md)   
 [ITarget 類別](itarget-class.md)

