---
title: CNoWorkerThread 類別
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326700"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 類別

如果要關閉動態緩存維護,`MonitorClass`請使用此類作為範本參數的參數來緩存類。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CNoWorkerThread
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CNoWorker 執行緒:新增句柄](#addhandle)|CWorkerThread 的非功能等效項目[:addHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|
|[CNoWorkerThread::新增計時器](#addtimer)|CWorkerThread 的非功能等效項目[:addTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|
|[CNoWorker 線程:取得線程句柄](#getthreadhandle)|CWorkerThread 的非功能等效項目[:取得線程句柄](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|
|[CNoWorker 執行緒:抓取緒 Id](#getthreadid)|CWorkerThread 的非功能等效項目[:getThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|
|[CNoWorkerThread:初始化](#initialize)|CWorkerThread 的非功能等效項目[::初始化](../../atl/reference/cworkerthread-class.md#initialize)。|
|[CNoWorker 執行緒::刪除句柄](#removehandle)|CWorkerThread 的非功能等效項目[::刪除句柄](../../atl/reference/cworkerthread-class.md#removehandle)。|
|[CNoWorker 執行緒:關閉](#shutdown)|CWorkerThread 的非功能等效項目[::關機](../../atl/reference/cworkerthread-class.md#shutdown)。|

## <a name="remarks"></a>備註

此類提供與[CWorkerThread](../../atl/reference/cworkerthread-class.md)相同的公共介面。 此介面預期由`MonitorClass`範本參數提供給緩存類。

類中的方法實現不執行任何操作。 返回 HRESULT 的方法始終返回S_OK,返回 HANDLE 或線程 ID 的方法始終返回 0。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorker 執行緒:新增句柄

CWorkerThread 的非功能等效項目[:addHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>傳回值

始終返回S_OK。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::新增計時器

CWorkerThread 的非功能等效項目[:addTimer](../../atl/reference/cworkerthread-class.md#addtimer)。

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>傳回值

始終返回S_OK。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorker 線程:取得線程句柄

CWorkerThread 的非功能等效項目[:取得線程句柄](../../atl/reference/cworkerthread-class.md#getthreadhandle)。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>傳回值

一律傳回 NULL。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorker 執行緒:抓取緒 Id

CWorkerThread 的非功能等效項目[:getThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>傳回值

永遠傳回 0。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread:初始化

CWorkerThread 的非功能等效項目[::初始化](../../atl/reference/cworkerthread-class.md#initialize)。

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>傳回值

始終返回S_OK。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorker 執行緒::刪除句柄

CWorkerThread 的非功能等效項目[::刪除句柄](../../atl/reference/cworkerthread-class.md#removehandle)。

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>傳回值

始終返回S_OK。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorker 執行緒:關閉

CWorkerThread 的非功能等效項目[::關機](../../atl/reference/cworkerthread-class.md#shutdown)。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>傳回值

始終返回S_OK。

### <a name="remarks"></a>備註

此類提供的實現不執行任何操作。
