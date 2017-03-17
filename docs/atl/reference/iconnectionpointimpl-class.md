---
title: "IConnectionPointImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: 19
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
ms.openlocfilehash: c9788496bbed3734b959d0ab4c49c89a176ea199
ms.lasthandoff: 02/24/2017

---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 類別
這個類別會實作連接點。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IConnectionPointImpl`。  
  
 `piid`  
 連線點物件所代表之介面的 IID 指標。  
  
 `CDV`  
 管理連接類別。 預設值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，這允許無限制的連線。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，以指定固定的數目的連線。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|建立連接點與接收器之間的連線。|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|建立列舉值，可逐一查看的連接點的連線。|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|擷取連接點所表示之介面的 IID。|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|擷取可連接物件的介面指標。|  
|[IConnectionPointImpl::Unadvise](#unadvise)|終止透過先前建立的連線`Advise`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|管理連接點的連線。|  
  
## <a name="remarks"></a>備註  
 `IConnectionPointImpl`實作連接點，讓物件公開給用戶端的輸出介面。 用戶端呼叫接收的物件上實作這個介面。  
  
 使用 ATL [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)實作可連接物件。 可連接物件內的每一個連接點代表所識別的連出介面`piid`。 類別*CDV*管理連接點與接收器之間的連線。 每個連接會識別 「 cookie 」。  
  
 如需在 ATL 中使用的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="advise"></a>IConnectionPointImpl::Advise  
 建立連接點與接收器之間的連線。  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>備註  
 使用[Unadvise](#unadvise)終止連線呼叫。  
  
 請參閱[IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="enumconnections"></a>IConnectionPointImpl::EnumConnections  
 建立列舉值，可逐一查看的連接點的連線。  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface  
 擷取連接點所表示之介面的 IID。  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer  
 擷取可連接物件的介面指標。  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_vec"></a>IConnectionPointImpl::m_vec  
 管理連接點物件與接收器之間的連線。  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>備註  
 根據預設，`m_vec`的型別[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)。  
  
##  <a name="unadvise"></a>IConnectionPointImpl::Unadvise  
 終止透過先前建立的連線[Advise](#advise)。  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [類別概觀](../../atl/atl-class-overview.md)

