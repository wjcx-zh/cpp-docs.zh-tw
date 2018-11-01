---
title: CNonStatelessWorker 類別
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 7aaae3728113cfd91c0655d2eac445cdd4b34246
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619618"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 類別

會從執行緒集區接收要求，並將其傳遞至會建立並終結背景工作物件中每個要求。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>參數

*背景工作角色*<br/>
若要符合的背景工作執行緒類別[背景工作原型](../../atl/reference/worker-archetype.md)適當的處理要求排入佇列[CThreadPool](../../atl/reference/cthreadpool-class.md)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|實作[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|實作[WorkerArchetype::Execute](worker-archetype.md#execute)。|
|[CNonStatelessWorker::Initialize](#initialize)|實作[WorkerArchetype::Initialize](worker-archetype.md#initialize)。|
|[CNonStatelessWorker::Terminate](#terminate)|實作[WorkerArchetype::Terminate](worker-archetype.md#terminate)。|

## <a name="remarks"></a>備註

這個類別是用於簡單的背景工作執行緒[CThreadPool](../../atl/reference/cthreadpool-class.md)。 此類別不提供自己的任何要求處理功能。 相反地，它會具現化一個執行個體*背景工作角色*每個要求並委派至該執行個體，其方法的實作。

這個類別的優點是，它會提供便利的方式，若要變更現有的背景工作執行緒類別的狀態模型。 `CThreadPool` 將會建立單一背景工作的存留期間的執行緒，因此如果背景工作類別保存狀態，它會保留它跨多個要求。 藉由直接包裝在該類別`CNonStatelessWorker`範本，然後再將它與`CThreadPool`、 背景工作角色和狀態會是限制為單一要求的存留期。

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

實作[WorkerArchetype::Execute](worker-archetype.md#execute)。

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>備註

這個方法建立的執行個體*背景工作角色*類別上呼叫與堆疊[初始化](worker-archetype.md#initialize)該物件。 如果初始化成功，這個方法也會呼叫[Execute](worker-archetype.md#execute)並[終止](worker-archetype.md#terminate)相同的物件。

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

實作[WorkerArchetype::Initialize](worker-archetype.md#initialize)。

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>傳回值

一律會傳回 TRUE。

### <a name="remarks"></a>備註

這個類別不會執行任何初始設定`Initialize`。

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

實作[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>備註

這個類別會處理相同類型的工作項目類別會用來作為*背景工作角色*樣板參數。 請參閱[CNonStatelessWorker 概觀](../../atl/reference/cnonstatelessworker-class.md)如需詳細資訊。

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

實作[WorkerArchetype::Terminate](worker-archetype.md#terminate)。

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>備註

這個類別不會執行任何清除作業`Terminate`。

## <a name="see-also"></a>另請參閱

[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)<br/>
[背景工作原型](../../atl/reference/worker-archetype.md)<br/>
[類別](../../atl/reference/atl-classes.md)
