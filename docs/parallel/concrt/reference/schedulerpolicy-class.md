---
title: "SchedulerPolicy 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a00f7d9cafbd84fc3bbf6b10f322fad6166110cd
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 類別
`SchedulerPolicy` 類別包含一組索引鍵/值組，每個原則項目一個，可控制排程器執行個體的行為。  
  
## <a name="syntax"></a>語法  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SchedulerPolicy](#ctor)|多載。 建構新的排程器原則，並填入值[原則機碼](concurrency-namespace-enums.md)並行執行階段排程和資源管理員支援。|  
|[~ SchedulerPolicy 解構函式](#dtor)|終結排程器原則。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|擷取的原則機碼值當做提供`key`參數。|  
|[SetConcurrencyLimits](#setconcurrencylimits)|同時設定`MinConcurrency`和`MaxConcurrency`上的原則`SchedulerPolicy`物件。|  
|[SetPolicyValue](#setpolicyvalue)|設定的原則機碼值當做提供`key`參數並傳回舊值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|從另一個排程器原則中指定的排程器原則。|  
  
## <a name="remarks"></a>備註  
 如需有關使用控制原則`SchedulerPolicy`類別，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h，concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="getpolicyvalue"></a>GetPolicyValue 

 擷取的原則機碼值當做提供`key`參數。  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>參數  
 `key`  
 原則索引鍵擷取的值。  
  
### <a name="return-value"></a>傳回值  
 如果所指定的索引鍵`key`支援參數、 索引鍵的原則值轉換成`unsigned int`。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)無效的原則機碼。  
  
##  <a name="operator_eq"></a>運算子 = 

 從另一個排程器原則中指定的排程器原則。  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>參數  
 `_RhsPolicy`  
 要指派給此原則的原則。  
  
### <a name="return-value"></a>傳回值  
 排程器原則的參考。  
  
### <a name="remarks"></a>備註  
 通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。  
  
##  <a name="ctor"></a>SchedulerPolicy 

 建構新的排程器原則，並填入值[原則機碼](concurrency-namespace-enums.md)並行執行階段排程和資源管理員支援。  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>參數  
 `_PolicyKeyCount`  
 數字的索引鍵/值組隨後的`_PolicyKeyCount`參數。  
  
 `_SrcPolicy`  
 要複製的來源原則。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建立新的排程器原則，其中所有的原則將會初始化成為其預設值。  
  
 第二個建構函式會建立新的排程器原則，會使用名為參數樣式的初始化。 值之後`_PolicyKeyCount`參數會提供做為索引鍵/值組。 這個建構函式中未指定的任何原則機碼會有其預設值。 這個建構函式可能會擲回例外狀況[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)， [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)或[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)。  
  
 第三個建構函式是複製建構函式。 通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。  
  
##  <a name="dtor"></a>~ SchedulerPolicy 

 終結排程器原則。  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a>SetConcurrencyLimits 

 同時設定`MinConcurrency`和`MaxConcurrency`上的原則`SchedulerPolicy`物件。  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>參數  
 `_MinConcurrency`  
 值`MinConcurrency`原則機碼。  
  
 `_MaxConcurrency`  
 值`MaxConcurrency`原則機碼。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)如果指定的值`MinConcurrency`原則是否大於指定的`MaxConcurrency`原則。  
  
 這個方法也可以擲回[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)針對其他無效值。  
  
##  <a name="setpolicyvalue"></a>SetPolicyValue 

 設定的原則機碼值當做提供`key`參數並傳回舊值。  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 原則機碼設定的值。  
  
 `value`  
 若要設定原則機碼值。  
  
### <a name="return-value"></a>傳回值  
 如果所指定的索引鍵`key`支援參數，舊的原則值，索引鍵轉換成`unsigned int`。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)無效的原則機碼或其值無法設定任何原則機碼`SetPolicyValue`方法。  
  
 方法會擲回[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)不支援所指定的索引鍵的值`key`參數。  
  
 請注意，這個方法不允許設定`MinConcurrency`或`MaxConcurrency`原則。 若要設定這些值，請使用[SetConcurrencyLimits](#setconcurrencylimits)方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler 類別](currentscheduler-class.md)   
 [Scheduler 類別](scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




