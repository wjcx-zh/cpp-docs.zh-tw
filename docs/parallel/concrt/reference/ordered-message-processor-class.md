---
title: "ordered_message_processor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 17
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
ms.openlocfilehash: 1c3147001db16b610992d2501ed12ad4bd001fc9
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor 類別
`ordered_message_processor` 是 `message_processor`，可讓訊息區塊按照接收順序處理訊息。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 處理器所處理的訊息內容型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`type`|類型別名`T`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ordered_message_processor](#ctor)|建構 `ordered_message_processor` 物件。|  
|[~ ordered_message_processor 解構函式](#dtor)|終結`ordered_message_processor`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[async_send](#async_send)|非同步訊息佇列，並開始處理工作，如果這已經不做。 (覆寫[message_processor:: async_send](message-processor-class.md#async_send)。)|  
|[初始化](#initialize)|初始化`ordered_message_processor`與適當的回呼函式、 排程和排程群組的物件。|  
|[initialize_batched_processing](#initialize_batched_processing)|初始化批次訊息處理|  
|[sync_send](#sync_send)|同步訊息佇列，以及啟動的處理工作，如果這已經不做。 (覆寫[message_processor:: sync_send](message-processor-class.md#sync_send)。)|  
|[等候](#wait)|處理器特定旋轉等待，用於訊息區塊的解構函式，以確定所有非同步處理工作已完成，然後再終結區塊的時間。 (覆寫[message_processor:: wait](message-processor-class.md#wait)。)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|以非同步方式呼叫的處理函式。 它從佇列中清除訊息，並開始處理它們。 (覆寫[message_processor:: process_incoming_message](message-processor-class.md#process_incoming_message)。)|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="async_send"></a>async_send 

 非同步訊息佇列，並開始處理工作，如果這已經不做。  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 訊息的指標。  
  
##  <a name="initialize"></a>初始化 

 初始化`ordered_message_processor`與適當的回呼函式、 排程和排程群組的物件。  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>參數  
 `_PScheduler`  
 要用於排程輕量工作排程器指標。  
  
 `_PScheduleGroup`  
 排程群組來排程輕量型工作的指標。  
  
 `_Handler`  
 處理常式仿函式叫用回呼時。  
  
##  <a name="initialize_batched_processing"></a>initialize_batched_processing 

 初始化批次訊息處理  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>參數  
 `_Processor`  
 處理器仿函式叫用回呼時。  
  
 `_Propagator`  
 傳播程式仿函式叫用回呼時。  
  
##  <a name="ctor"></a>ordered_message_processor 

 建構 `ordered_message_processor` 物件。  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>備註  
 這`ordered_message_processor`會排程非同步或同步處理常式，直到`initialize`函式呼叫。  
  
##  <a name="dtor"></a>~ ordered_message_processor 

 終結`ordered_message_processor`物件。  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>備註  
 等候所有未完成的非同步作業，然後再終結處理器。  
  
##  <a name="process_incoming_message"></a>process_incoming_message 

 以非同步方式呼叫的處理函式。 它從佇列中清除訊息，並開始處理它們。  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="sync_send"></a>sync_send 

 同步訊息佇列，以及啟動的處理工作，如果這已經不做。  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 訊息的指標。  
  
##  <a name="wait"></a>等候 

 處理器特定旋轉等待，用於訊息區塊的解構函式，以確定所有非同步處理工作已完成，然後再終結區塊的時間。  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

