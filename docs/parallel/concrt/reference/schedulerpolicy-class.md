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
ms.openlocfilehash: fed33c198502b75e824bcaf698227d283f4b85f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142743"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 類別

`SchedulerPolicy` 類別包含一組索引鍵/值組，每個原則項目一個，可控制排程器執行個體的行為。

## <a name="syntax"></a>語法

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|已多載。 會建立新的排程器原則，並將並行執行階段排程器和 Resource Manager 所支援的[原則金鑰](concurrency-namespace-enums.md)值填入其中。|
|[~ SchedulerPolicy 的析構函式](#dtor)|終結排程器原則。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|抓取提供做為 `key` 參數之原則金鑰的值。|
|[SetConcurrencyLimits](#setconcurrencylimits)|同時設定 `SchedulerPolicy` 物件的 `MinConcurrency` 和 `MaxConcurrency` 原則。|
|[SetPolicyValue](#setpolicyvalue)|將提供的原則金鑰值設定為 `key` 參數，並傳回舊值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|從另一個排程器原則指派排程器原則。|

## <a name="remarks"></a>備註

如需可使用 `SchedulerPolicy` 類別來控制之原則的詳細資訊，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`SchedulerPolicy`

## <a name="requirements"></a>需求

**標頭：** concrt .h，concrtrm.h。h

**命名空間：** concurrency

## <a name="getpolicyvalue"></a>GetPolicyValue

抓取提供做為 `key` 參數之原則金鑰的值。

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
要為其取得值的原則索引鍵。

### <a name="return-value"></a>傳回值

如果支援 `key` 參數所指定的索引鍵，則會將索引鍵的原則值轉換成 `unsigned int`。

### <a name="remarks"></a>備註

方法將會擲回無效原則金鑰的[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) 。

## <a name="operator_eq"></a>operator =

從另一個排程器原則指派排程器原則。

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>參數

*_RhsPolicy*<br/>
要指派給此原則的原則。

### <a name="return-value"></a>傳回值

排程器原則的參考。

### <a name="remarks"></a>備註

通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。

## <a name="ctor"></a>SchedulerPolicy

會建立新的排程器原則，並將並行執行階段排程器和 Resource Manager 所支援的[原則金鑰](concurrency-namespace-enums.md)值填入其中。

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>參數

*_PolicyKeyCount*<br/>
遵循 `_PolicyKeyCount` 參數的索引鍵/值組數目。

*_SrcPolicy*<br/>
要複製的來源原則。

### <a name="remarks"></a>備註

第一個函式會建立新的排程器原則，其中所有的原則都會初始化為其預設值。

第二個函式會建立新的排程器原則，使用初始化的具名引數樣式。 `_PolicyKeyCount` 參數之後的值會以索引鍵/值組的形式提供。 未在此函式中指定的任何原則金鑰都會有其預設值。 此函式可能會擲回例外狀況[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)、 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)或[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)。

第三個函式是複製的函式。 通常，定義新的排程器原則最方便的方法是複製現有的原則，並使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法修改。

## <a name="dtor"></a>~ SchedulerPolicy

終結排程器原則。

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a>SetConcurrencyLimits

同時設定 `SchedulerPolicy` 物件的 `MinConcurrency` 和 `MaxConcurrency` 原則。

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>參數

*_MinConcurrency*<br/>
`MinConcurrency` 原則索引鍵的值。

*_MaxConcurrency*<br/>
`MaxConcurrency` 原則索引鍵的值。

### <a name="remarks"></a>備註

如果為 `MinConcurrency` 原則指定的值大於為 `MaxConcurrency` 原則指定的值，方法將會擲回[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) 。

方法也可以擲回其他無效值的[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 。

## <a name="setpolicyvalue"></a>SetPolicyValue

將提供的原則金鑰值設定為 `key` 參數，並傳回舊值。

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>參數

*key*<br/>
要為其設定值的原則索引鍵。

*value*<br/>
要設定原則索引鍵的值。

### <a name="return-value"></a>傳回值

如果支援 `key` 參數所指定的索引鍵，則會將索引鍵的舊原則值轉換成 `unsigned int`。

### <a name="remarks"></a>備註

方法將會擲回無效原則金鑰的[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) ，或 `SetPolicyValue` 方法無法設定其值的任何原則索引鍵。

方法將會針對 `key` 參數所指定的索引鍵不支援的值擲回[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 。

請注意，此方法不允許設定 `MinConcurrency` 或 `MaxConcurrency` 原則。 若要設定這些值，請使用[SetConcurrencyLimits](#setconcurrencylimits)方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler 類別](currentscheduler-class.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
