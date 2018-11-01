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
ms.openlocfilehash: 6132ec6623a009c09a37b7d704ce683a58956a04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518712"
---
# <a name="schedulegroup-class"></a>ScheduleGroup 類別

代表排程群組的抽象概念。 排程群組會將一組相關的工作組織在一起，以讓這些工作獲得暫時緊密排程在一起的優勢，其方法如下：透過在同一個群組中執行另一個工作再移至另一個群組；透過再同一個 NUMA 節點或實體通訊端的同一個群組內執行多個項目。

## <a name="syntax"></a>語法

```
class ScheduleGroup;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[~ ScheduleGroup 解構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ID](#id)|傳回群組所屬的排程器中是唯一的排程群組的識別碼。|
|[參考資料](#reference)|遞增排程器群組的參考計數。|
|[發行](#release)|遞減排程器群組的參考計數。|
|[ScheduleTask](#scheduletask)|排程群組內的輕量級的排程工作。|

## <a name="inheritance-hierarchy"></a>繼承階層

`ScheduleGroup`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="id"></a> Id

傳回群組所屬的排程器中是唯一的排程群組的識別碼。

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>傳回值

排程群組中的群組所屬的排程器的唯一識別碼。

##  <a name="operator_delete"></a> 運算子 delete

A`ScheduleGroup`終結物件內部執行階段時，所有外部參考會釋出。 它不可明確刪除。

```
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
要刪除的物件指標。

##  <a name="reference"></a> 參考

遞增排程器群組的參考計數。

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>傳回值

新遞增的參考計數。

### <a name="remarks"></a>備註

這通常用來管理排程群組組合的存留期。 排程群組的參考計數降為零，當執行階段會刪除排程群組。 建立使用排程群組[currentscheduler:: Createschedulegroup](currentscheduler-class.md#createschedulegroup)方法，或有[scheduler:: createschedulegroup](scheduler-class.md#createschedulegroup)方法開始的其中一個的參考計數。

##  <a name="release"></a> 版本

遞減排程器群組的參考計數。

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

新遞減參考計數。

### <a name="remarks"></a>備註

這通常用來管理排程群組組合的存留期。 排程群組的參考計數降為零，當執行階段會刪除排程群組。 在您呼叫 `Release` 方法特定次數以移除建立參考計數和任何使用 `Reference` 方法所進行的參考後，就不能進一步利用排程群組。 如此一來，會導致未定義的行為。

排程群組是特定的排程器執行個體相關聯。 您必須先確定已釋放排程群組的所有參考，才能釋放排程器的所有參考，因為後者可能會使排程器遭到終結。 在進行其他方式導致未定義的行為。

##  <a name="dtor"></a> ~ ScheduleGroup

```
virtual ~ScheduleGroup();
```

##  <a name="scheduletask"></a> ScheduleTask

排程群組內的輕量級的排程工作。

```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>參數

*_Proc*<br/>
若要執行的輕量工作主體執行該函式指標。

*資料 （_d)*<br/>
將做為參數傳遞至工作的主體資料的 void 指標。

### <a name="remarks"></a>備註

呼叫`ScheduleTask`方法會隱含地將參考計數放上不再由執行階段在適當的時間之後會執行該工作的排程群組。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[CurrentScheduler 類別](currentscheduler-class.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

