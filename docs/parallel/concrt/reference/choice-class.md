---
title: "choice 類別 | Microsoft Docs"
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
  - "agents/concurrency::choice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "choice 類別"
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# choice 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`choice` 傳訊區塊是多來源的單一目標區塊，代表與一組來源的控制流程互動。 選擇區塊會等候多個來源的其中一個來產生訊息，而且會傳播產生訊息之來源的索引。  
  
## <a name="syntax"></a>語法  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 A `tuple`-根據型別，表示承載的輸入來源。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`type`|類型別名 `T`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[choice:: choice 建構函式](#choice__choice_constructor)|多載。 建構 `choice` 傳訊區塊。|  
|[choice:: ~ choice 解構函式](#choice___dtorchoice_destructor)|終結 `choice` 傳訊區塊。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[choice:: accept 方法](#choice__accept_method)|接受的訊息，這提供 `choice` 區塊中，將擁有權轉移給呼叫者。|  
|[choice:: acquire_ref 方法](#choice__acquire_ref_method)|取得此參考計數 `choice` 傳訊區塊，以防止刪除。|  
|[choice:: consume 方法](#choice__consume_method)|會使用先前提供此訊息 `choice` 傳訊區塊和目標，將擁有權轉移給呼叫者已成功保留。|  
|[choice:: has_value 方法](#choice__has_value_method)|檢查是否這 `choice` 傳訊區塊有尚未初始化的值。|  
|[choice:: index 方法](#choice__index_method)|傳回指數 `tuple` 代表所選取的項目 `choice` 傳訊區塊。|  
|[choice:: link_target 方法](#choice__link_target_method)|此連結的目標區塊 `choice` 傳訊區塊。|  
|[choice:: release 方法](#choice__release_method)|釋放先前成功的訊息保留。|  
|[choice:: release_ref 方法](#choice__release_ref_method)|釋放此參考計數 `choice` 傳訊區塊。|  
|[choice:: reserve 方法](#choice__reserve_method)|先前提供的這一則訊息會保留 `choice` 傳訊區塊。|  
|[choice:: unlink_target 方法](#choice__unlink_target_method)|取消連結從這個目標區塊 `choice` 傳訊區塊。|  
|[choice:: unlink_targets 方法](#choice__unlink_targets_method)|取消連結所有目標從此 `choice` 傳訊區塊。 (覆寫 [Isource:: Unlink_targets](../../../parallel/concrt/reference/isource-class.md#isource__unlink_targets_method)。)|  
|[choice:: value 方法](#choice__value_method)|取得索引的已選取的訊息 `choice` 傳訊區塊。|  
  
## <a name="remarks"></a>備註  
 選擇區塊可確保會使用其中一個內送訊息。  
  
 如需詳細資訊，請參閱 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namechoiceacceptmethoda-choiceaccept-method"></a><a name="choice__accept_method"></a>  choice:: accept 方法  
 接受的訊息，這提供 `choice` 區塊中，將擁有權轉移給呼叫者。  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 所提供的 `message` 物件。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `accept` 方法。  
  
### <a name="return-value"></a>傳回值  
 呼叫者現在擁有訊息指標。  
  
##  <a name="a-namechoiceacquirerefmethoda-choiceacquireref-method"></a><a name="choice__acquire_ref_method"></a>  choice:: acquire_ref 方法  
 取得此參考計數 `choice` 傳訊區塊，以防止刪除。  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 正在呼叫這個方法對目標區塊指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 `ITarget` 物件連結到這個來源期間 `link_target` 方法。  
  
##  <a name="a-namechoicechoiceconstructora-choicechoice-constructor"></a><a name="choice__choice_constructor"></a>  choice:: choice 建構函式  
 建構 `choice` 傳訊區塊。  
  
```  
explicit choice(
    T _Tuple);

 
choice(
    Scheduler& _PScheduler,  
    T _Tuple);

 
choice(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
choice(
    choice&& _Choice);
```  
  
### <a name="parameters"></a>參數  
 `_Tuple`  
 選擇的 `tuple` 來源。  
  
 `_PScheduler`  
 `Scheduler` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。  
  
 `_PScheduleGroup`  
 `ScheduleGroup` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
 `_Choice`  
 作為複製來源處的 `choice` 傳訊區塊。 請注意，原始物件會被遺棄，使其成為移動建構函式。  
  
### <a name="remarks"></a>備註  
 如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。  
  
 移動建構函式不會在鎖定下執行，這表示使用者必須確認在移動時沒有任何輕量工作在執行中。 否則，可能發生許多競爭情況，導致例外狀況或不一致的狀態。  
  
##  <a name="a-namechoicedtorchoicedestructora-choicechoice-destructor"></a><a name="choice___dtorchoice_destructor"></a>  choice:: ~ choice 解構函式  
 終結 `choice` 傳訊區塊。  
  
```  
~choice();
```  
  
##  <a name="a-namechoiceconsumemethoda-choiceconsume-method"></a><a name="choice__consume_method"></a>  choice:: consume 方法  
 會使用先前提供此訊息 `choice` 傳訊區塊和目標，將擁有權轉移給呼叫者已成功保留。  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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
  
##  <a name="a-namechoicehasvaluemethoda-choicehasvalue-method"></a><a name="choice__has_value_method"></a>  choice:: has_value 方法  
 檢查是否這 `choice` 傳訊區塊有尚未初始化的值。  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果區塊已接收值， `false` 否則。  
  
##  <a name="a-namechoiceindexmethoda-choiceindex-method"></a><a name="choice__index_method"></a>  choice:: index 方法  
 傳回指數 `tuple` 代表所選取的項目 `choice` 傳訊區塊。  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>傳回值  
 訊息的索引。  
  
### <a name="remarks"></a>備註  
 可使用擷取訊息裝載 `get` 方法。  
  
##  <a name="a-namechoicelinktargetmethoda-choicelinktarget-method"></a><a name="choice__link_target_method"></a>  choice:: link_target 方法  
 此連結的目標區塊 `choice` 傳訊區塊。  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標 `ITarget` 連結到此區塊 `choice` 傳訊區塊。  
  
##  <a name="a-namechoicereleasemethoda-choicerelease-method"></a><a name="choice__release_method"></a>  choice:: release 方法  
 釋放先前成功的訊息保留。  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_MsgId`  
  `runtime_object_identity` 的 `message` 物件被釋放。  
  
 `_PTarget`  
 正在呼叫的目標區塊的指標 `release` 方法。  
  
##  <a name="a-namechoicereleaserefmethoda-choicereleaseref-method"></a><a name="choice__release_ref_method"></a>  choice:: release_ref 方法  
 釋放此參考計數 `choice` 傳訊區塊。  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 正在呼叫這個方法對目標區塊指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 `ITarget` 從這個來源所連結的物件。 來源區塊可釋放任何資源保留給目標區塊。  
  
##  <a name="a-namechoicereservemethoda-choicereserve-method"></a><a name="choice__reserve_method"></a>  choice:: reserve 方法  
 先前提供的這一則訊息會保留 `choice` 傳訊區塊。  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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
  
##  <a name="a-namechoiceunlinktargetmethoda-choiceunlinktarget-method"></a><a name="choice__unlink_target_method"></a>  choice:: unlink_target 方法  
 取消連結從這個目標區塊 `choice` 傳訊區塊。  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 指標 `ITarget` 區塊中斷連結從這個 `choice` 傳訊區塊。  
  
##  <a name="a-namechoiceunlinktargetsmethoda-choiceunlinktargets-method"></a><a name="choice__unlink_targets_method"></a>  choice:: unlink_targets 方法  
 取消連結所有目標從此 `choice` 傳訊區塊。  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>備註  
 這個方法不需要呼叫解構函式，因為解構函式內部 `single_assignment` 區塊將會取消連結正確。  
  
##  <a name="a-namechoicevaluemethoda-choicevalue-method"></a><a name="choice__value_method"></a>  choice:: value 方法  
 取得索引的已選取的訊息 `choice` 傳訊區塊。  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>參數  
 `_Payload_type`  
 訊息內容型別。  
  
### <a name="return-value"></a>傳回值  
 訊息的內容。  
  
### <a name="remarks"></a>備註  
 因為 `choice` 傳訊區塊可以接受具有不同類型承載的輸入，因此您必須在擷取時指定承載的類型。 您可以決定根據結果的型別 `index` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [join 類別](../../../parallel/concrt/reference/join-class.md)   
 [single_assignment 類別](../../../parallel/concrt/reference/single-assignment-class.md)
