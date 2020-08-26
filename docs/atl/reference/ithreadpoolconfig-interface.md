---
title: IThreadPoolConfig 介面
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: cba82055c292fc966dc2328773cce4aa64d45a64
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835424"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 介面

這個介面會提供方法來設定執行緒集區。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[GetSize](#getsize)|呼叫這個方法以取得集區中的執行緒數目。|
|[GetTimeout](#gettimeout)|呼叫這個方法，取得執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。|
|[SetSize](#setsize)|呼叫這個方法來設定集區中的執行緒數目。|
|[SetTimeout](#settimeout)|呼叫這個方法來設定執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。|

## <a name="remarks"></a>備註

此介面是由 [CThreadPool](../../atl/reference/cthreadpool-class.md)所執行。

## <a name="requirements"></a>規格需求

**標頭：** atlutil。h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a> IThreadPoolConfig：： GetSize

呼叫這個方法以取得集區中的執行緒數目。

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>參數

*pnNumThreads*<br/>
擴展在成功時收到集區中的執行緒數目之變數的位址。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a> IThreadPoolConfig：： GetTimeout

呼叫這個方法，取得執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>參數

*pdwMaxWait*<br/>
擴展在成功的情況下，會收到執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）的變數位址。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱 [IThreadPoolConfig：： GetSize](#getsize)。

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a> IThreadPoolConfig：： SetSize

呼叫這個方法來設定集區中的執行緒數目。

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>參數

*nNumThreads*<br/>
集區中要求的執行緒數目。

如果 *nNumThreads* 為負數，則其絕對值將乘以電腦中的處理器數目，以取得執行緒總數。

如果 *nNumThreads* 為零，ATLS_DEFAULT_THREADSPERPROC 將乘以電腦中的處理器數目，以取得執行緒總數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱 [IThreadPoolConfig：： GetSize](#getsize)。

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a> IThreadPoolConfig：： SetTimeout

呼叫這個方法來設定執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱 [IThreadPoolConfig：： GetSize](#getsize)。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)
