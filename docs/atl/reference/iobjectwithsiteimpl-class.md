---
title: "IObjectWithSiteImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs: C++
helpviewer_keywords: IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a591e7970aa21e6846700570cdf27cefececa1c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 類別
這個類別會提供讓物件與其站台通訊的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IObjectWithSiteImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|查詢的介面指標的站台。|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|提供的物件與站台的**IUnknown**指標。|  
|[IObjectWithSiteImpl::SetSite](#setsite)|提供的物件與站台的**IUnknown**指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站台的**IUnknown**指標。|  
  
## <a name="remarks"></a>備註  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)介面讓物件與其站台通訊。 類別`IObjectWithSiteImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 `IObjectWithSiteImpl`指定兩種方法。 用戶端會先呼叫`SetSite`，傳遞站台的**IUnknown**指標。 此指標會儲存在物件內，稍後可以透過呼叫擷取`GetSite`。  
  
 一般而言，衍生您的類別從`IObjectWithSiteImpl`當您建立的物件，不是控制項。 控制項，衍生您的類別從[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，這樣也會提供站台的指標。 不是您的類別衍生自`IObjectWithSiteImpl`和`IOleObjectImpl`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getsite"></a>IObjectWithSiteImpl::GetSite  
 查詢所識別的介面指標的站台`riid`。  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>備註  
 如果站台支援這個介面，指標會傳回透過`ppvSite`。 否則，`ppvSite`設**NULL**。  
  
 請參閱[IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) Windows SDK 中。  
  
##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite  
 管理站台的**IUnknown**指標。  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>備註  
 `m_spUnkSite`一開始會接收這個指標透過呼叫[SetSite](#setsite)。  
  
##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite  
 提供的物件與站台的**IUnknown**指標。  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>參數  
 *pUnkSite*  
 [in]指標**IUnknown**管理此物件的站台的介面指標。 如果是 NULL，應該呼叫物件`IUnknown::Release`任何時間點的物件不會再知道其站台的現有站台上。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="setsite"></a>IObjectWithSiteImpl::SetSite  
 提供的物件與站台的**IUnknown**指標。  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
