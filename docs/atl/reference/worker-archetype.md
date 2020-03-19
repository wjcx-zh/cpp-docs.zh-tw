---
title: 背景工作原型
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 2e57c575ed778184cf319bb84e61f585fcfa2111
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509337"
---
# <a name="worker-archetype"></a>背景工作原型

符合背景*工作*原型的類別會提供程式碼來處理執行緒集區上排入佇列的工作專案。

**實作**

若要執行符合此原型的類別，類別必須提供下列功能：

|方法|描述|
|------------|-----------------|
|[Initialize](#initialize)|呼叫以初始化背景工作物件，然後將任何要求傳遞至[執行](#execute)。|
|[執行](#execute)|呼叫以處理工作專案。|
|[Terminate](#terminate)|呼叫以在所有要求都已傳遞給[執行](#execute)之後，解除初始化背景工作物件。|

|Typedef|描述|
|-------------|-----------------|
|[RequestType](#requesttype)|可由 worker 類別處理之工作專案類型的 typedef。|

典型的背景*工作*類別看起來像這樣：

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**現有的實現**

這些類別符合此原型：

|類別|描述|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|接收來自執行緒集區的要求，並將它們傳遞至針對每個要求所建立和終結的背景工作物件。|

**使用**

這些範本參數會預期類別符合此原型：

|參數名稱|使用者|
|--------------------|-------------|
|*工作*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*工作*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="execute"></a>WorkerArchetype：： Execute

呼叫以處理工作專案。

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>參數

*要求*<br/>
要處理的工作專案。 工作專案與 `RequestType`的類型相同。

*pvWorkerParam*<br/>
背景工作類別所瞭解的自訂參數。 也會傳遞至 `WorkerArchetype::Initialize` 並 `Terminate`。

*pOverlapped*<br/>
用來建立工作專案排入佇列之重[迭結構的](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)指標。

## <a name="initialize"></a>WorkerArchetype：： Initialize

呼叫以初始化背景工作物件，然後將要求傳遞給 `WorkerArchetype::Execute`。

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
背景工作類別所瞭解的自訂參數。 也會傳遞至 `WorkerArchetype::Terminate` 並 `WorkerArchetype::Execute`。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

## <a name="requesttype"></a>WorkerArchetype：： RequestType

可由 worker 類別處理之工作專案類型的 typedef。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>備註

此類型必須當做 `WorkerArchetype::Execute` 的第一個參數使用，而且必須能夠在 ULONG_PTR 之間進行來回轉換。

## <a name="terminate"></a>WorkerArchetype：： Terminate

呼叫以在所有要求都傳遞給 `WorkerArchetype::Execute`之後，將背景工作物件解除初始化。

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
背景工作類別所瞭解的自訂參數。 也會傳遞至 `WorkerArchetype::Initialize` 並 `WorkerArchetype::Execute`。

## <a name="see-also"></a>另請參閱

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
