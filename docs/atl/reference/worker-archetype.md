---
title: 背景工作原型
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 790cf064fcffe1f0cd3c191c28ed0a0614062406
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274495"
---
# <a name="worker-archetype"></a>背景工作原型

符合類別*背景工作角色*原型提供程式碼以處理程序的工作項目排入佇列，執行緒集區。

**實作**

若要實作符合此原型的類別，類別必須提供下列功能：

|方法|描述|
|------------|-----------------|
|[Initialize](#initialize)|呼叫以初始化背景工作角色的物件之前的任何要求會傳遞至, [Execute](#execute)。|
|[Execute](#execute)|呼叫以處理工作項目。|
|[Terminate](#terminate)|呼叫以取消初始化背景工作物件之後的所有要求都傳遞至, [Execute](#execute)。|

|Typedef|描述|
|-------------|-----------------|
|[RequestType](#requesttype)|可處理的背景工作角色類別的工作項目類型的 typedef。|

典型*背景工作角色*類別看起來像這樣：

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**現有的實作**

這些類別會符合此原型：

|類別|描述|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|會從執行緒集區接收要求，並將其傳遞至背景工作物件，會建立並終結針對每個要求。|

**使用**

這些範本參數預期要符合此原型的類別：

|參數名稱|使用對象|
|--------------------|-------------|
|*Worker*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Worker*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>需求

**標頭：** atlutil.h

## <a name="execute"></a>WorkerArchetype::Execute

呼叫以處理工作項目。

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>參數

*request*<br/>
處理工作項目。 工作項目屬於相同的型別`RequestType`。

*pvWorkerParam*<br/>
了解的背景工作角色類別的自訂參數。 也會傳遞給`WorkerArchetype::Initialize`和`Terminate`。

*pOverlapped*<br/>
指標[OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)結構，用來建立在哪一個工作項目已排入佇列的佇列。

## <a name="initialize"></a> WorkerArchetype::Initialize

呼叫以初始化背景工作角色的物件之前的任何要求會傳遞至, `WorkerArchetype::Execute`。
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
了解的背景工作角色類別的自訂參數。 也會傳遞給`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。

### <a name="return-value"></a>傳回值

傳回 TRUE，如果成功，失敗則為 FALSE。

## <a name="requesttype"></a> WorkerArchetype::RequestType

可處理的背景工作角色類別的工作項目類型的 typedef。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>備註

這個類型必須做的第一個參數`WorkerArchetype::Execute`和必須能夠從 ULONG_PTR 來回轉換。

## <a name="terminate"></a> WorkerArchetype::Terminate

停止背景工作物件的初始化之後的所有要求都傳遞至, 呼叫`WorkerArchetype::Execute`)。

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
了解的背景工作角色類別的自訂參數。 也會傳遞給`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。

## <a name="see-also"></a>另請參閱

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
