---
title: "呼叫類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrency::call
- agents/concurrency::call
dev_langs:
- C++
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
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
ms.sourcegitcommit: 19244e5527207f852256e646abd18ad298fb28cd
ms.openlocfilehash: b3cfec104346b212217a6854af2390c412c9e015
ms.lasthandoff: 02/24/2017

---
# <a name="call-class"></a>call 類別
`call` 傳訊區塊是一個多來源的排序 `target_block`，它在接收訊息時會叫用指定的函式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 傳播到此區塊的訊息內容型別。  
  
 `_FunctorType`  
 這個區塊可以接受的函式簽章。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[呼叫建構函式](#ctor)|多載。 建構`call`傳訊區塊。|  
|[~ call 解構函式](#dtor)|終結`call`傳訊區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[process_input_messages 方法](#process_input_messages)|輸入訊息上執行的呼叫函式。|  
|[process_message 方法](#process_message)|處理已接受此訊息`call`傳訊區塊。|  
|[propagate_message 方法](#propagate_message)|以非同步方式傳遞訊息從`ISource`區塊至此`call`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。|  
|[send_message 方法](#send_message)|以同步方式傳遞訊息從`ISource`區塊至此`call`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。|  
|[supports_anonymous_source 方法](#supports_anonymous_source)|覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。 (覆寫[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-call"></a><a name="ctor"></a>呼叫 

 建構`call`傳訊區塊。  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>參數  
 `_Func`  
 為每個接受的訊息就會叫用函式。  
  
 `_Filter`  
 篩選函式可判斷是否應該接受所提供的訊息。  
  
 `_PScheduler`  
 `Scheduler`傳播的工作的物件`call`排定傳訊區塊。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`傳播的工作的物件`call`排定傳訊區塊。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 型別`_Call_method`是以簽章仿`void (T const &)`由此叫用`call`傳訊區塊來處理訊息。  
  
 型別`filter_method`是以簽章仿`bool (T const &)`由此叫用`call`傳訊區塊，以判斷它是否應該接受提供的訊息。  
  
##  <a name="a-namedtora-call"></a><a name="dtor"></a>~ 呼叫 

 終結`call`傳訊區塊。  
  
```
~call();
```  
  
##  <a name="a-nameprocessinputmessagesa-processinputmessages"></a><a name="process_input_messages"></a>process_input_messages 

 輸入訊息上執行的呼叫函式。  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
  
##  <a name="a-nameprocessmessagea-processmessage"></a><a name="process_message"></a>process_message 

 處理已接受此訊息`call`傳訊區塊。  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 要處理的訊息指標。  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 以非同步方式傳遞訊息從`ISource`區塊至此`call`傳訊區塊。 它會叫用`propagate`方法，由來源區塊呼叫時。  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="a-namesendmessagea-sendmessage"></a><a name="send_message"></a>send_message 

 以同步方式傳遞訊息從`ISource`區塊至此`call`傳訊區塊。 它會叫用`send`方法，由來源區塊呼叫時。  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>參數  
 `_PMessage`  
 `message` 物件的指標。  
  
 `_PSource`  
 提供訊息來源區塊的指標。  
  
### <a name="return-value"></a>傳回值  
 A [message_status](concurrency-namespace-enums.md)目標決定如何處理訊息的指示。  
  
##  <a name="a-namesupportsanonymoussourcea-supportsanonymoussource"></a><a name="supports_anonymous_source"></a>supports_anonymous_source 

 覆寫 `supports_anonymous_source` 方法，指出這個區塊可以接受未連結的來源提供給它的訊息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>傳回值  
 `true`，因為區塊不會延後提供的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [transformer 類別](transformer-class.md)

