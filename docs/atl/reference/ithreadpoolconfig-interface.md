---
title: IThreadPool 設定介面
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
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326349"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPool 設定介面

此介面提供了配置線程池的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetSize](#getsize)|調用此方法獲取池中的線程數。|
|[取得逾時](#gettimeout)|調用此方法,獲取線程池將等待線程關閉的最大時間(以毫秒為單位)。|
|[設定大小](#setsize)|調用此方法以設置池中的線程數。|
|[設定逾時](#settimeout)|調用此方法以設置線程池將等待線程關閉的最大時間(以毫秒為單位)。|

## <a name="remarks"></a>備註

此介面由[CThreadPool](../../atl/reference/cthreadpool-class.md)實現。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPool 配置::取得 Size

調用此方法獲取池中的線程數。

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>參數

*pnNumThreads*<br/>
[出]變數的位址,在成功時,接收池中的線程數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPool 配置::獲取超時

調用此方法,獲取線程池將等待線程關閉的最大時間(以毫秒為單位)。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>參數

*pdwMaxWait*<br/>
[出]變數的位址,在成功時,接收線程池將等待線程關閉的最大時間(以毫秒為單位)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPool 設定::取得 Size](#getsize)。

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPool 設定::設定大小

調用此方法以設置池中的線程數。

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>參數

*nNumThreads*<br/>
池中請求的線程數。

如果*nNumThreads*為負值,則其絕對值將乘以電腦中的處理器數,以獲得線程總數。

如果*nNumThreads*為零,ATLS_DEFAULT_THREADSPERPROC將乘以計算機中的處理器數,以獲得線程總數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPool 設定::取得 Size](#getsize)。

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPool 配置::設置超時

調用此方法以設置線程池將等待線程關閉的最大時間(以毫秒為單位)。

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
請求的最大時間(以毫秒為單位)用於線程池將等待線程關閉。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[IThreadPool 設定::取得 Size](#getsize)。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)
