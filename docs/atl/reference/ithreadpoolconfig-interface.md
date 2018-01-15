---
title: "IThreadPoolConfig 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs: C++
helpviewer_keywords: IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d967720778305eace4eff9ad8b2163456fb4bb46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 介面
這個介面會提供設定執行緒集區的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
|[GetTimeout](#gettimeout)|呼叫這個方法，以毫秒為單位，執行緒集區將會等到關閉執行緒取得最大時間。|  
|[SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|  
|[SetTimeout](#settimeout)|呼叫此方法以設定以毫秒為單位，執行緒集區關閉執行緒的等候時間上限。|  
  
## <a name="remarks"></a>備註  
 這個介面由實作[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
##  <a name="getsize"></a>IThreadPoolConfig::GetSize  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>參數  
 `pnNumThreads`  
 [out]此變數會在成功時，接收的執行緒數目位址集區中的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 呼叫這個方法，以毫秒為單位，執行緒集區將會等到關閉執行緒取得最大時間。  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>參數  
 `pdwMaxWait`  
 [out]位址之變數的成功時，收到的最長時間的執行緒集區會關閉執行緒等候的毫秒數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="setsize"></a>IThreadPoolConfig::SetSize  
 呼叫此方法以設定集區中的執行緒數目。  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>參數  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)將會乘以取得的執行緒總數機器的處理器數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 呼叫此方法以設定以毫秒為單位，執行緒集區關閉執行緒的等候時間上限。  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區將會等到關閉執行緒要求的最大時間。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CThreadPool 類別](../../atl/reference/cthreadpool-class.md)
