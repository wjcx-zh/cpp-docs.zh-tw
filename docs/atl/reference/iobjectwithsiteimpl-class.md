---
title: "IObjectWithSiteImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IObjectWithSiteImpl
- ATL.IObjectWithSiteImpl<T>
- IObjectWithSiteImpl
- ATL.IObjectWithSiteImpl
- ATL::IObjectWithSiteImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 49c52810417650c3d80fe4d0c09ccb2b67208ad4
ms.lasthandoff: 02/24/2017

---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 類別
這個類別會提供方法讓其站台通訊的物件。  
  
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
  
|名稱|描述|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|查詢的介面指標的站台。|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|提供的物件與站台的**IUnknown**指標。|  
|[IObjectWithSiteImpl::SetSite](#setsite)|提供的物件與站台的**IUnknown**指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站台的**IUnknown**指標。|  
  
## <a name="remarks"></a>備註  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)介面可讓其站台通訊的物件。 類別`IObjectWithSiteImpl`提供此介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 `IObjectWithSiteImpl`指定兩個方法。 用戶端會先呼叫`SetSite`，傳遞站台的**IUnknown**指標。 這個指標會儲存在物件中，並稍後可以透過呼叫擷取`GetSite`。  
  
 一般而言，您衍生您的類別，從`IObjectWithSiteImpl`當您建立物件，並不是控制項。 對控制項而言，衍生您的類別，從[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，這也會提供站台的指標。 不會同時從衍生類別`IObjectWithSiteImpl`和`IOleObjectImpl`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namegetsitea--iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite  
 查詢所識別的介面指標的站台`riid`。  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>備註  
 如果站台支援此介面，會透過傳回指標`ppvSite`。 否則，`ppvSite`設為**NULL**。  
  
 請參閱[IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemspunksitea--iobjectwithsiteimplmspunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite  
 管理站台的**IUnknown**指標。  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>備註  
 `m_spUnkSite`一開始會接收這個指標透過呼叫[SetSite](#setsite)。  
  
##  <a name="a-namesetchildsitea--iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite  
 提供的物件與站台的**IUnknown**指標。  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>參數  
 *pUnkSite*  
 [in]指標**IUnknown**管理此物件的站台的介面指標。 如果是 NULL，物件應該呼叫`IUnknown::Release`任何時間點的物件不再知道其站台的現有站台上。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="a-namesetsitea--iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite  
 提供的物件與站台的**IUnknown**指標。  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

