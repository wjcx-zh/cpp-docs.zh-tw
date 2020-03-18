---
title: ScheduleGroup 類別
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417128"
---
# <a name="schedulegroup-class"></a>ScheduleGroup 類別

代表排程群組的抽象概念。 排程群組會將一組相關的工作組織在一起，以讓這些工作獲得暫時緊密排程在一起的優勢，其方法如下：透過在同一個群組中執行另一個工作再移至另一個群組；透過再同一個 NUMA 節點或實體通訊端的同一個群組內執行多個項目。

## <a name="syntax"></a>語法

```cpp
class ScheduleGroup;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[~ ScheduleGroup 的析構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Id](#id)|傳回排程群組的識別碼，這在群組所屬的排程器內是唯一的。|
|[參考](#reference)|遞增排程器群組的參考計數。|
|[版本](#release)|遞減排程器群組的參考計數。|
|[ScheduleTask](#scheduletask)|排定排程群組內的輕量工作。|

## <a name="inheritance-hierarchy"></a>繼承階層

`ScheduleGroup`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="id"></a>號

傳回排程群組的識別碼，這在群組所屬的排程器內是唯一的。

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>傳回值

排程群組的識別碼，在該群組所屬的排程器內是唯一的。

## <a name="operator_delete"></a>運算子 delete

執行時間會在釋放所有外部參考時，于內部終結 `ScheduleGroup` 物件。 它不可明確刪除。

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>參數

*_PObject*<br/>
要刪除之物件的指標。

## <a name="reference"></a>證明

遞增排程器群組的參考計數。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>傳回值

新遞增的參考計數。

### <a name="remarks"></a>備註

這通常用來管理組合之排程群組的存留期。 當排程群組的參考計數降至零時，執行時間就會刪除排程群組。 使用[CurrentScheduler：： CreateScheduleGroup](currentscheduler-class.md#createschedulegroup)方法建立的排程群組，或排程器[：： CreateScheduleGroup](scheduler-class.md#createschedulegroup)方法會從一個參考計數開始。

## <a name="release"></a>版本

遞減排程器群組的參考計數。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

新遞減的參考計數。

### <a name="remarks"></a>備註

這通常用來管理組合之排程群組的存留期。 當排程群組的參考計數降至零時，執行時間就會刪除排程群組。 在您呼叫 `Release` 方法特定次數以移除建立參考計數和任何使用 `Reference` 方法所進行的參考後，就不能進一步利用排程群組。 這麼做會導致未定義的行為。

排程群組會與特定的排程器實例相關聯。 您必須先確定已釋放排程群組的所有參考，才能釋放排程器的所有參考，因為後者可能會使排程器遭到終結。 否則，會導致未定義的行為。

## <a name="dtor"></a>~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask

排定排程群組內的輕量工作。

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>參數

*_Proc*<br/>
執行輕量工作主體的函式指標。

*_Data*<br/>
將當做參數傳遞至工作主體之資料的 void 指標。

### <a name="remarks"></a>備註

呼叫 `ScheduleTask` 方法會以隱含方式將參考計數放在排程群組上，而執行時間會在工作執行後，于適當的時間將其移除。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[CurrentScheduler 類別](currentscheduler-class.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
