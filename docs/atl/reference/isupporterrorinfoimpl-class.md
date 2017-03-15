---
title: "ISupportErrorInfoImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::ISupportErrorInfoImpl<piid>
- ATL::ISupportErrorInfoImpl
- ISupportErrorInfoImpl
- ATL.ISupportErrorInfoImpl<piid>
- ATL.ISupportErrorInfoImpl
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
caps.latest.revision: 23
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
ms.openlocfilehash: 320cb27d1d22a5e4240861c934e9bcfabd731bad
ms.lasthandoff: 02/24/2017

---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 類別
這個類別提供的預設實作[ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)和產生的物件上的錯誤，只有單一介面時，可以使用。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>參數  
 `piid`  
 支援介面的 IID 指標[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指出介面是否由識別`riid`支援[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)介面。|  
  
## <a name="remarks"></a>備註  
 [ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)可確保資訊時發生錯誤，可以傳回至用戶端。 物件，使用**IErrorInfo**必須實作**ISupportErrorInfo**。  
  
 類別`ISupportErrorInfoImpl`提供的預設實作**ISupportErrorInfo**和產生的物件上的錯誤，只有單一介面時，可以使用。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#48;](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameinterfacesupportserrorinfoa--isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 指出介面是否由識別`riid`支援[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)介面。  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 [!code-cpp[NVC_ATL_Utilities #&134;](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
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
 [類別概觀](../../atl/atl-class-overview.md)

