---
title: IWorkerThreadClient 介面
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: aa72f090a006d6936339582a919b0faf5cab6b03
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835346"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 介面

`IWorkerThreadClient` 是由 [CWorkerThread](../../atl/reference/cworkerthread-class.md) 類別的用戶端所執行的介面。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
__interface IWorkerThreadClient
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[CloseHandle](#closehandle)|請執行此方法來關閉與此物件相關聯的控制碼。|
|[執行](#execute)|當與這個物件相關聯的控制碼變成信號時，請執行此方法來執行程式碼。|

## <a name="remarks"></a>備註

當您的程式碼需要在背景工作執行緒上執行，以回應控制碼變成信號時，請執行這個介面。

## <a name="requirements"></a>規格需求

**標頭：** atlutil。h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a> IWorkerThreadClient：： CloseHandle

請執行此方法來關閉與此物件相關聯的控制碼。

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
要關閉的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給這個方法的控制碼先前藉由呼叫 [CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)與這個物件相關聯。

### <a name="example"></a>範例

下列程式碼顯示的簡單執行 `IWorkerThreadClient::CloseHandle` 。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a> IWorkerThreadClient：： Execute

當與這個物件相關聯的控制碼變成信號時，請執行此方法來執行程式碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*dwParam*<br/>
使用者參數。

*hObject*<br/>
已變成信號的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞至這個方法的控制碼和 DWORD/指標，之前是透過呼叫 [CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)來與這個物件相關聯。

### <a name="example"></a>範例

下列程式碼顯示的簡單執行 `IWorkerThreadClient::Execute` 。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)
