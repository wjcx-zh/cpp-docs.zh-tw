---
title: "ITarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
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
ms.openlocfilehash: 4bd6b21e274431449c8fac452995dd66fc1aef1b
ms.lasthandoff: 03/17/2017

---
# <a name="itarget-class"></a>ITarget 類別
`ITarget` 類別是所有目標區塊的介面。 目標區塊會使用 `ISource` 區塊提供給它們的訊息。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 裝載目標區塊所接受之訊息內的資料型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`filter_method`|所傳回的區塊使用任何方法的簽章`bool`值，以判斷是否應該接受提供的訊息。|  
|`type`|類型別名`T`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[~ ITarget 解構函式](#dtor)|終結`ITarget`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[傳播](#propagate)|在衍生類別中覆寫，以非同步的方式會將訊息從來源區塊到此目標區塊。|  
|[傳送](#send)|在衍生類別中覆寫，以同步方式將訊息傳遞至目標區塊。|  
|[supports_anonymous_source](#supports_anonymous_source)|在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回 `true`，目標就不可延後提供的訊息，因為之後要使用延後的訊息就需要在其來源連結登錄中識別來源。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[link_source](#link_source)|當在衍生類別中覆寫時，連結指定的來源區塊這`ITarget`區塊。|  
|[unlink_source](#unlink_source)|當在衍生類別中覆寫時，取消連結指定的來源區塊從此`ITarget`區塊。|  
|[unlink_sources](#unlink_sources)|當在衍生類別中覆寫時，取消連結所有來源區塊，從這個`ITarget`區塊。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ITarget`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="dtor"></a>~ ITarget 

 終結`ITarget`物件。  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a>link_source 

 當在衍生類別中覆寫時，連結指定的來源區塊這`ITarget`區塊。  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 `ISource`封鎖連結到這`ITarget`區塊。  
  
### <a name="remarks"></a>備註  
 此函式不應該直接呼叫`ITarget`區塊。 區塊應該一起使用來連接`link_target`方法`ISource`區塊，會叫用`link_source`上對應的目標方法。  
  
##  <a name="propagate"></a>傳播 

 在衍生類別中覆寫，以非同步的方式會將訊息從來源區塊到此目標區塊。  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
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
  
##  <a name="send"></a>傳送 

 在衍生類別中覆寫，以同步方式將訊息傳遞至目標區塊。  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
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
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回 `true`，目標就不可延後提供的訊息，因為之後要使用延後的訊息就需要在其來源連結登錄中識別來源。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>傳回值  
 如果區塊可以接受未與它連結的來源提供的訊息，則為 `true`，否則為 `false`。  
  
##  <a name="unlink_source"></a>unlink_source 

 當在衍生類別中覆寫時，取消連結指定的來源區塊從此`ITarget`區塊。  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_PSource`  
 `ISource`封鎖正在取消連結從這個`ITarget`區塊。  
  
### <a name="remarks"></a>備註  
 此函式不應該直接呼叫`ITarget`區塊。 應該使用中斷區塊`unlink_target`或`unlink_targets`方法`ISource`區塊，會叫用`unlink_source`上對應的目標方法。  
  
##  <a name="unlink_sources"></a>unlink_sources 

 當在衍生類別中覆寫時，取消連結所有來源區塊，從這個`ITarget`區塊。  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ISource 類別](isource-class.md)

