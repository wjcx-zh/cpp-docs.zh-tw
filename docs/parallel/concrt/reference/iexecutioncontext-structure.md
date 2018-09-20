---
title: IExecutionContext 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecb07238fbe3648c857520cce5658b8d2897ee2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384269"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 結構

執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。

## <a name="syntax"></a>語法

```
struct IExecutionContext;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IExecutionContext::Dispatch](#dispatch)|執行緒 proxy 會開始執行的特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。|
|[IExecutionContext::GetId](#getid)|傳回的執行內容的唯一識別碼。|
|[IExecutionContext::GetProxy](#getproxy)|讓介面返回正在執行此內容的執行緒 proxy。|
|[IExecutionContext::GetScheduler](#getscheduler)|此執行內容所屬的介面傳回給排程器。|
|[IExecutionContext::SetProxy](#setproxy)|將與此執行內容，相關聯的執行緒 proxy。 相關聯的執行緒 proxy 在它開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。|

## <a name="remarks"></a>備註

如果您正在實作介面使用並行執行階段的 Resource Manager 的自訂排程器，您必須實作`IExecutionContext`介面。 在 Resource Manager 所建立的執行緒執行工作，代表您的排程器藉由執行`IExecutionContext::Dispatch`方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`IExecutionContext`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="dispatch"></a>  Iexecutioncontext:: Dispatch 方法

執行緒 proxy 會開始執行的特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。

```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>參數

*pDispatchState*<br/>
此執行內容會分派在其下的狀態指標。 如需有關分派狀態的詳細資訊，請參閱[DispatchState](dispatchstate-structure.md)。

##  <a name="getid"></a>  Iexecutioncontext:: Getid 方法

傳回的執行內容的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

的唯一整數識別碼。

### <a name="remarks"></a>備註

您應該使用的方法`GetExecutionContextId`以取得實作之物件的唯一識別碼`IExecutionContext`介面，才能使用此介面做為方法的參數提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。

從不同來源取得的識別碼可能會導致未定義的行為。

##  <a name="getproxy"></a>  Iexecutioncontext:: Getproxy 方法

讓介面返回正在執行此內容的執行緒 proxy。

```
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>傳回值

`IThreadProxy` 介面。 如果尚未初始化的執行內容的執行緒 proxy 藉由呼叫`SetProxy`，函式必須傳回`NULL`。

### <a name="remarks"></a>備註

Resource Manager 將會叫用`SetProxy`上執行內容，方法與`IThreadProxy`介面做為參數，再輸入`Dispatch`方法內容上。 您應該儲存此引數，並將它傳回呼叫`GetProxy()`。

##  <a name="getscheduler"></a>  Iexecutioncontext:: Getscheduler 方法

此執行內容所屬的介面傳回給排程器。

```
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>傳回值

`IScheduler` 介面。

### <a name="remarks"></a>備註

您必須初始化使用有效的執行內容`IScheduler`介面，才能使用它做為方法的參數提供資源管理員。

##  <a name="setproxy"></a>  Iexecutioncontext:: Setproxy 方法

將與此執行內容，相關聯的執行緒 proxy。 相關聯的執行緒 proxy 在它開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。

```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>參數

*pThreadProxy*<br/>
即將進入的執行緒 proxy 介面`Dispatch`上此執行內容的方法。

### <a name="remarks"></a>備註

您應該儲存參數`pThreadProxy`並將它傳回呼叫`GetProxy`方法。 Resource Manager 可保證執行緒 proxy 正在執行時不會變更執行內容相關聯的執行緒 proxy`Dispatch`方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)
