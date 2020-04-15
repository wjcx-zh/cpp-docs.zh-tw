---
title: IWorkerThread用戶端介面
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326305"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThread用戶端介面

`IWorkerThreadClient`是[CWorkerThread](../../atl/reference/cworkerthread-class.md)類的用戶端實現的介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
__interface IWorkerThreadClient
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[關閉手柄](#closehandle)|實現此方法以關閉與此物件關聯的句柄。|
|[執行](#execute)|實現此方法,當與此物件關聯的句柄發出信號時執行代碼。|

## <a name="remarks"></a>備註

當您有代碼需要在工作線程上執行以回應變為信號的句柄時,實現此介面。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThread用戶端::關閉句柄

實現此方法以關閉與此物件關聯的句柄。

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
要關閉的句柄。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時出現錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給此方法的句柄以前通過調用[CWorkerThread::addHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

以下代碼顯示了`IWorkerThreadClient::CloseHandle`的簡單實現。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThread用戶端:執行

實現此方法,當與此物件關聯的句柄發出信號時執行代碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*德帕拉姆*<br/>
用戶參數。

*hObject*<br/>
已發出信號的句柄。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時出現錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給此方法的句柄和 DWORD/指標以前通過調用[CWorkerThread::addHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

以下代碼顯示了`IWorkerThreadClient::Execute`的簡單實現。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)
