---
title: "IThreadPoolConfig 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATL::IThreadPoolConfig
- ATL.IThreadPoolConfig
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: e10885373442890978feff42cda99309692a21d0
ms.lasthandoff: 02/24/2017

---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 介面
這個介面會提供設定執行緒集區的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetSize](#getsize)|呼叫這個方法來取得集區中的執行緒數目。|  
|[GetTimeout](#gettimeout)|呼叫這個方法，以毫秒為單位，執行緒集區會等待關閉執行緒取得的最長時間。|  
|[SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|  
|[SetTimeout](#settimeout)|呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。|  
  
## <a name="remarks"></a>備註  
 這個介面由實作[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="a-namegetsizea--ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>參數  
 `pnNumThreads`  
 [out]接收的變數，成功時，執行緒數目的集區中的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&134;](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="a-namegettimeouta--ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 呼叫這個方法，以毫秒為單位，執行緒集區會等待關閉執行緒取得的最長時間。  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>參數  
 `pdwMaxWait`  
 [out]接收的變數，成功時，最長的時間以毫秒為單位，執行緒集區會等待執行緒關閉的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="a-namesetsizea--ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize  
 呼叫此方法以設定集區中的執行緒數目。  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>參數  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)將乘以取得的執行緒總數機器的處理器數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="a-namesettimeouta--ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區會等待執行緒關閉要求的最大時間。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 請參閱[IThreadPoolConfig::GetSize](#getsize)。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CThreadPool 類別](../../atl/reference/cthreadpool-class.md)

