---
title: IObjectWithSiteImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: ad27c4288d7e16949fe38ea6b8a686e3d6916ee6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296965"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 類別

這個類別提供方法讓其站台與通訊的物件。

## <a name="syntax"></a>語法

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IObjectWithSiteImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|查詢的介面指標的站台。|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|物件提供站台的`IUnknown`指標。|
|[IObjectWithSiteImpl::SetSite](#setsite)|物件提供站台的`IUnknown`指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站台的`IUnknown`指標。|

## <a name="remarks"></a>備註

[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite)介面允許其站台與通訊的物件。 類別`IObjectWithSiteImpl`提供此介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

`IObjectWithSiteImpl` 指定兩個方法。 用戶端會先呼叫`SetSite`，將站台的`IUnknown`指標。 此指標會儲存在物件中，並稍後可以透過呼叫來擷取`GetSite`。

一般而言，您衍生您的類別，從`IObjectWithSiteImpl`當您建立物件，並不是控制項。 對於控制項，衍生您的類別，從[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，這也會提供站台的指標。 不是您的類別衍生自兩者`IObjectWithSiteImpl`和`IOleObjectImpl`。

## <a name="inheritance-hierarchy"></a>繼承階層

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

查詢所識別之介面指標的站台`riid`。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>備註

如果站台支援這個介面，透過傳回的指標`ppvSite`。 否則，`ppvSite`設為 NULL。

請參閱[IObjectWithSite::GetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-getsite) Windows SDK 中。

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

管理站台的`IUnknown`指標。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>備註

`m_spUnkSite` 一開始會收到這個指標，透過呼叫[SetSite](#setsite)。

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

物件提供站台的`IUnknown`指標。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>參數

*pUnkSite*<br/>
[in]指標`IUnknown`管理此物件的站台的介面指標。 如果是 NULL，應呼叫物件`IUnknown::Release`上任何現有的站台，屆時物件不再知道其站台。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

物件提供站台的`IUnknown`指標。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>備註

請參閱[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
