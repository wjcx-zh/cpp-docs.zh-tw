---
title: ISupportErrorInfoImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e226f66d6ddd20181f083f723568acb1cc647c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 類別
這個類別提供的預設實作[ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)和單一介面會產生錯誤的物件上時才能使用。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>參數  
 `piid`  
 支援介面 IID 的指標[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指出介面是否由識別`riid`支援[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)介面。|  
  
## <a name="remarks"></a>備註  
 [ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)可確保錯誤資訊可傳回至用戶端。 物件，使用**IErrorInfo**必須實作**ISupportErrorInfo**。  
  
 類別`ISupportErrorInfoImpl`提供的預設實作**ISupportErrorInfo**和單一介面會產生錯誤的物件上時才能使用。 例如:   
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 指出介面是否由識別`riid`支援[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)介面。  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a) Windows SDK 中。  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
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
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
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
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
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
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
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
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
