---
title: 無狀態工人類
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
ms.openlocfilehash: 6264bb6bc9070b5ce170b294f9db0d371e7b6b71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747661"
---
# <a name="cnonstatelessworker-class"></a>無狀態工人類

從線程池接收請求,並將它們傳遞到在每個請求上創建和銷毀的工作物件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>參數

*工人*<br/>
符合工作[原型](../../atl/reference/worker-archetype.md)的工作線程類,適合處理在[CThreadPool](../../atl/reference/cthreadpool-class.md)上排隊的請求。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[無狀態工作人員::請求類型](#requesttype)|[workerArche 類型的實作:請求類型](worker-archetype.md#requesttype)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[無狀態工作人員:執行](#execute)|[工作Arche類型的實作:執行](worker-archetype.md#execute)。|
|[無狀態工作人員:初始化](#initialize)|[工作Arche類型的實作:初始化](worker-archetype.md#initialize)。|
|[無狀態工作人員::終止](#terminate)|[workerArche 類型的實作:終止](worker-archetype.md#terminate)。|

## <a name="remarks"></a>備註

此類是一個簡單的工作線程,用於[CThreadPool。](../../atl/reference/cthreadpool-class.md) 此類不提供其自己的任何請求處理功能。 相反,它實例化每個請求的一個*Worker*實例,並將其方法的實現委託給該實例。

此類的好處是它提供了一種更改現有輔助線程類的狀態模型的便捷方法。 `CThreadPool`將為線程的存留期創建單個輔助角色,因此,如果輔助角色類保持狀態,它將跨多個請求保留該工作線程。 只需在`CNonStatelessWorker`範本中包裝該類,即可`CThreadPool`使用 ,輔助角色的存留期及其保留狀態僅限於單個請求。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>無狀態工作人員:執行

[工作Arche類型的實作:執行](worker-archetype.md#execute)。

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>備註

此方法在堆疊上建立*輔助角色*類別的實體,並在該物件上調使用[初始化](worker-archetype.md#initialize)。 如果初始化成功,此方法也會在同一對象上調用[「執行](worker-archetype.md#execute)」與[「終止](worker-archetype.md#terminate)」。。

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>無狀態工作人員:初始化

[工作Arche類型的實作:初始化](worker-archetype.md#initialize)。

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

此類不會在`Initialize`中 執行任何初始化。

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>無狀態工作人員::請求類型

[workerArche 類型的實作:請求類型](worker-archetype.md#requesttype)。

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>備註

此類處理的工作項類型與用於*輔助角色*範本參數的類相同。 有關詳細資訊,請參閱[無狀態工作人員概述](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>無狀態工作人員::終止

[workerArche 類型的實作:終止](worker-archetype.md#terminate)。

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>備註

此類不會在中`Terminate`進行任何清理。

## <a name="see-also"></a>另請參閱

[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)<br/>
[工人原型](../../atl/reference/worker-archetype.md)<br/>
[類別](../../atl/reference/atl-classes.md)
