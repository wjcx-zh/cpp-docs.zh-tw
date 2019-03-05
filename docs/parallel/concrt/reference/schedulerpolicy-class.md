---
title: SchedulerPolicy 類別
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: 2eff40b11e4e9a5981ad85c37c8345abefb13fed
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265531"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 類別


  `SchedulerPolicy` 類別包含一組索引鍵/值組，每個原則項目一個，可控制排程器執行個體的行為。

## <a name="syntax"></a>語法

```
class SchedulerPolicy;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|多載。 建構新的排程器原則，並填入值[原則金鑰](concurrency-namespace-enums.md)並行執行階段排程器和 Resource Manager 所支援。|
|[~ SchedulerPolicy 解構函式](#dtor)|終結排程器原則。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|原則索引鍵的值當做提供的擷取`key`參數。|
|[SetConcurrencyLimits](#setconcurrencylimits)|同時設定`MinConcurrency`並`MaxConcurrency`上的原則`SchedulerPolicy`物件。|
|[SetPolicyValue](#setpolicyvalue)|為提供的原則機碼值組`key`參數並傳回最舊的值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|指派給另一個排程器原則的排程器原則。|

## <a name="remarks"></a>備註

如需有關可以使用來控制原則`SchedulerPolicy`類別，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`SchedulerPolicy`

## <a name="requirements"></a>需求

**標頭：** concrt.h，concrtrm.h

**命名空間：** concurrency

##  <a name="getpolicyvalue"></a> GetPolicyValue

原則索引鍵的值當做提供的擷取`key`參數。

```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
要擷取的值的原則金鑰。

### <a name="return-value"></a>傳回值

如果所指定的索引鍵`key`支援參數、 索引鍵的原則值轉換成`unsigned int`。

### <a name="remarks"></a>備註

方法會擲回[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)無效的原則機碼。

##  <a name="operator_eq"></a> 運算子 =

指派給另一個排程器原則的排程器原則。

```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>參數

*_RhsPolicy*<br/>
要指派給此原則的原則。

### <a name="return-value"></a>傳回值

排程器原則的參考。

### <a name="remarks"></a>備註

通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。

##  <a name="ctor"></a> SchedulerPolicy

建構新的排程器原則，並填入值[原則金鑰](concurrency-namespace-enums.md)並行執行階段排程器和 Resource Manager 所支援。

```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>參數

*_PolicyKeyCount*<br/>
這些索引鍵/值組的`_PolicyKeyCount`參數。

*_SrcPolicy*<br/>
要複製的來源原則。

### <a name="remarks"></a>備註

第一個建構函式會建立新的排程器原則，其中所有的原則將會初始化為其預設值。

第二個建構函式會建立新的排程器原則，會使用名為參數樣式的初始化。 值之後`_PolicyKeyCount`參數會提供做為索引鍵/值組。 這個建構函式中未指定任何原則金鑰會有其預設值。 這個建構函式可能會擲回例外狀況[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)， [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)或[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

第三個建構函式是複製建構函式。 通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。

##  <a name="dtor"></a> ~SchedulerPolicy

終結排程器原則。

```
~SchedulerPolicy();
```

##  <a name="setconcurrencylimits"></a> SetConcurrencyLimits

同時設定`MinConcurrency`並`MaxConcurrency`上的原則`SchedulerPolicy`物件。

```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>參數

*_MinConcurrency*<br/>
值`MinConcurrency`原則金鑰。

*_MaxConcurrency*<br/>
值`MaxConcurrency`原則金鑰。

### <a name="remarks"></a>備註

方法會擲回[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)指定的值，如果`MinConcurrency`原則是否大於指定給`MaxConcurrency`原則。

此方法也可能會擲回[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)針對其他無效值。

##  <a name="setpolicyvalue"></a> SetPolicyValue

為提供的原則機碼值組`key`參數並傳回最舊的值。

```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>參數

*key*<br/>
原則機碼設定的值。

*value*<br/>
若要設定原則機碼值。

### <a name="return-value"></a>傳回值

如果所指定的索引鍵`key`支援參數、 索引鍵的舊原則值轉換成`unsigned int`。

### <a name="remarks"></a>備註

方法會擲回[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)無效的原則機碼或其值無法設定任何原則機碼`SetPolicyValue`方法。

方法會擲回[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)不支援所指定的索引鍵的值`key`參數。

請注意，這個方法不可以設定`MinConcurrency`或`MaxConcurrency`原則。 若要設定這些值，請使用[SetConcurrencyLimits](#setconcurrencylimits)方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler 類別](currentscheduler-class.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
