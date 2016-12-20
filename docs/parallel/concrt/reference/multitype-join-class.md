---
title: "multitype_join 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::multitype_join"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multitype_join 類別"
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multitype_join 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`multitype_join` 傳訊區塊是多來源的單一目標傳訊區塊，會與來自其來源的不同類型訊息合併，並且為其目標提供 Tuple 合併的訊息。  
  
## <a name="syntax"></a>語法  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
  `tuple` 訊息的內容類型加入及傳播區塊。  
  
 `_Jtype`  
 此種類的 `join` 區塊，可能是 `greedy` 或 `non_greedy`  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`type`|類型別名 `T`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[multitype_join:: multitype_join 建構函式](#multitype_join__multitype_join_constructor)|多載。 建構 `multitype_join` 傳訊區塊。|  
|[multitype_join:: ~ multitype_join 解構函式](#multitype_join___dtormultitype_join_destructor)|終結 `multitype_join` 傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[multitype_join:: accept 方法](#multitype_join__accept_method)|接受的訊息，這提供 `multitype_join` 區塊中，將擁有權轉移給呼叫者。|  
|[multitype_join:: acquire_ref 方法](#multitype_join__acquire_ref_method)|取得此參考計數 `multitype_join` 傳訊區塊，以防止刪除。|  
|[multitype_join:: consume 方法](#multitype_join__consume_method)|會使用先前所提供訊息 `multitype_join` 傳訊區塊和目標，將擁有權轉移給呼叫者已成功保留。|  
|[multitype_join:: link_target 方法](#multitype_join__link_target_method)|此連結的目標區塊 `multitype_join` 傳訊區塊。|  
|[multitype_join:: release 方法](#multitype_join__release_method)|釋放先前成功的訊息保留。|  
|[multitype_join:: release_ref 方法](#multitype_join__release_ref_method)|釋放此參考計數 `multiple_join` 傳訊區塊。|  
|[multitype_join:: reserve 方法](#multitype_join__reserve_method)|先前提供的這一則訊息會保留 `multitype_join` 傳訊區塊。|  
|[multitype_join:: unlink_target 方法](#multitype_join__unlink_target_method)|取消連結從這個目標區塊 `multitype_join` 傳訊區塊。|  
|[multitype_join:: unlink_targets 方法](#multitype_join__unlink_targets_method)|取消連結所有目標從此 `multitype_join` 傳訊區塊。 (覆寫 [Isource:: Unlink_targets](../../../parallel/concrt/reference/isource-class.md#isource__unlink_targets_method)。)|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namemultitypejoinacceptmethoda-multitypejoinaccept-method"></a><a name="multitype_join__accept_method"></a>  multitype_join:: accept 方法  
 接受的訊息，這提供 `multitype_join` 區塊中，將擁有權轉移給呼叫者。  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 所提供的 `message` 物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `accept` 方法。  
  
### <a name="return-value"></a>傳回值  
 呼叫者現在擁有訊息指標。  
  
##  <a name="a-namemultitypejoinacquirerefmethoda-multitypejoinacquireref-method"></a><a name="multitype_join__acquire_ref_method"></a>  multitype_join:: acquire_ref 方法  
 取得此參考計數 `multitype_join` 傳訊區塊，以防止刪除。  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 正在呼叫這個方法對目標區塊指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 `ITarget` 物件連結到這個來源期間 `link_target` 方法。  
  
##  <a name="a-namemultitypejoinconsumemethoda-multitypejoinconsume-method"></a><a name="multitype_join__consume_method"></a>  multitype_join:: consume 方法  
 會使用先前所提供訊息 `multitype_join` 傳訊區塊和目標，將擁有權轉移給呼叫者已成功保留。  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 的保留 `message` 物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `consume` 方法。  
  
### <a name="return-value"></a>傳回值  
 指標 `message` 物件，呼叫者現在會有的擁有權。  
  
### <a name="remarks"></a>備註  
  `consume` 方法很類似 `accept`, ，但必須一律加上呼叫 `reserve` 傳回 `true`。  
  
##  <a name="a-namemultitypejoinlinktargetmethoda-multitypejoinlinktarget-method"></a><a name="multitype_join__link_target_method"></a>  multitype_join:: link_target 方法  
 此連結的目標區塊 `multitype_join` 傳訊區塊。  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標 `ITarget` 連結到此區塊 `multitype_join` 傳訊區塊。  
  
##  <a name="a-namemultitypejoinmultitypejoinconstructora-multitypejoinmultitypejoin-constructor"></a><a name="multitype_join__multitype_join_constructor"></a>  multitype_join:: multitype_join 建構函式  
 建構 `multitype_join` 傳訊區塊。  
  
```  
explicit multitype_join(
    T _Tuple);

 
multitype_join(
    Scheduler& _PScheduler,  
    T _Tuple);

 
multitype_join(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
multitype_join(
    multitype_join&& _Join);
```  
  
### <a name="parameters"></a>參數  
 `_Tuple`  
 此 `tuple` 傳訊區塊的 `multitype_join` 來源。  
  
 `_PScheduler`  
 `Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。  
  
 `_PScheduleGroup`  
 `ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
 `_Join`  
 作為複製來源處的 `multitype_join` 傳訊區塊。 請注意，原始物件會被遺棄，使其成為移動建構函式。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 移動建構函式不會在鎖定下執行，這表示使用者必須確認在移動時沒有任何輕量工作在執行中。 否則，可能發生許多競爭情況，導致例外狀況或不一致的狀態。  
  
##  <a name="a-namemultitypejoindtormultitypejoindestructora-multitypejoinmultitypejoin-destructor"></a><a name="multitype_join___dtormultitype_join_destructor"></a>  multitype_join:: ~ multitype_join 解構函式  
 終結 `multitype_join` 傳訊區塊。  
  
```  
~multitype_join();
```  
  
##  <a name="a-namemultitypejoinreleasemethoda-multitypejoinrelease-method"></a><a name="multitype_join__release_method"></a>  multitype_join:: release 方法  
 釋放先前成功的訊息保留。  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 的 `message` 物件被釋放。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `release` 方法。  
  
##  <a name="a-namemultitypejoinreleaserefmethoda-multitypejoinreleaseref-method"></a><a name="multitype_join__release_ref_method"></a>  multitype_join:: release_ref 方法  
 釋放此參考計數 `multiple_join` 傳訊區塊。  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 正在呼叫這個方法對目標區塊指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 `ITarget` 從這個來源所連結的物件。 來源區塊可釋放任何資源保留給目標區塊。  
  
##  <a name="a-namemultitypejoinreservemethoda-multitypejoinreserve-method"></a><a name="multitype_join__reserve_method"></a>  multitype_join:: reserve 方法  
 先前提供的這一則訊息會保留 `multitype_join` 傳訊區塊。  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 的 `message` 物件被保留。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `reserve` 方法。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已成功保留， `false` 否則。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。  
  
### <a name="remarks"></a>備註  
 在您呼叫後 `reserve`, ，如果成功，您必須呼叫 `consume` 或 `release` 才能採取或分別給予持有的訊息。  
  
##  <a name="a-namemultitypejoinunlinktargetmethoda-multitypejoinunlinktarget-method"></a><a name="multitype_join__unlink_target_method"></a>  multitype_join:: unlink_target 方法  
 取消連結從這個目標區塊 `multitype_join` 傳訊區塊。  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標 `ITarget` 區塊中斷連結從這個 `multitype_join` 傳訊區塊。  
  
##  <a name="a-namemultitypejoinunlinktargetsmethoda-multitypejoinunlinktargets-method"></a><a name="multitype_join__unlink_targets_method"></a>  multitype_join:: unlink_targets 方法  
 取消連結所有目標從此 `multitype_join` 傳訊區塊。  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [choice 類別](../../../parallel/concrt/reference/choice-class.md)   
 [join 類別](../../../parallel/concrt/reference/join-class.md)
