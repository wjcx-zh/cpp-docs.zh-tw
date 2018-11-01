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
ms.openlocfilehash: a021ac833bfdb0dd0da1a585d141e477232fc645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505374"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 介面

這個介面會提供方法，以設定執行緒集區。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetSize](#getsize)|呼叫這個方法來取得集區中的執行緒數目。|
|[GetTimeout](#gettimeout)|呼叫這個方法，以取得最長的時間，以毫秒為單位，執行緒集區會等待關閉執行緒。|
|[SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|
|[SetTimeout](#settimeout)|呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。|

## <a name="remarks"></a>備註

此介面由實作[CThreadPool](../../atl/reference/cthreadpool-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

呼叫這個方法來取得集區中的執行緒數目。

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>參數

*pnNumThreads*<br/>
[out]成功時，執行緒數目的集區中接收變數的位址。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

呼叫這個方法，以取得最長的時間，以毫秒為單位，執行緒集區會等待關閉執行緒。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>參數

*pdwMaxWait*<br/>
[out]變數的位址，成功時，收到的最長時間的執行緒集區會關閉執行緒等候的毫秒數。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPoolConfig::GetSize](#getsize)。

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

呼叫此方法以設定集區中的執行緒數目。

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>參數

*nNumThreads*<br/>
執行緒集區中的要求的數目。

如果*nNumThreads*是負數，其絕對值將會乘以中取得的執行緒總數機器的處理器數目。

如果*nNumThreads*為零，若要取得的執行緒總數機器中的處理器數目將會乘以 ATLS_DEFAULT_THREADSPERPROC。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPoolConfig::GetSize](#getsize)。

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
以毫秒為單位，執行緒集區會等待關閉執行緒要求的最大時間。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPoolConfig::GetSize](#getsize)。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)
