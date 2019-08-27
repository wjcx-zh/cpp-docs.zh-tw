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
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495840"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 類別

這個類別提供的方法可讓物件與網站進行通訊。

## <a name="syntax"></a>語法

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IObjectWithSiteImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|查詢網站中的介面指標。|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|提供具有網站`IUnknown`指標的物件。|
|[IObjectWithSiteImpl::SetSite](#setsite)|提供具有網站`IUnknown`指標的物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理網站的`IUnknown`指標。|

## <a name="remarks"></a>備註

[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)介面可讓物件與其網站進行通訊。 類別`IObjectWithSiteImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

`IObjectWithSiteImpl`指定兩個方法。 用戶端會先`SetSite`呼叫, 並傳遞網站`IUnknown`的指標。 這個指標會儲存在物件中, 稍後可透過對的呼叫來`GetSite`抓取。

一般而言, 當您建立非控制項`IObjectWithSiteImpl`的物件時, 會從衍生您的類別。 針對控制項, 從[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)衍生您的類別, 這也會提供網站指標。 請勿從`IObjectWithSiteImpl`和`IOleObjectImpl`衍生您的類別。

## <a name="inheritance-hierarchy"></a>繼承階層

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getsite"></a>IObjectWithSiteImpl::GetSite

查詢網站以取得所識別`riid`之介面的指標。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>備註

如果網站支援此介面, 則會透過傳回`ppvSite`指標。 否則, `ppvSite`會設定為 Null。

請參閱 Windows SDK 中的[IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) 。

##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

管理網站的`IUnknown`指標。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>備註

`m_spUnkSite`一開始會透過呼叫[SetSite](#setsite)來接收此指標。

##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

提供具有網站`IUnknown`指標的物件。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>參數

*pUnkSite*<br/>
在管理此物件之網站介面指標的指標。`IUnknown` 如果是 Null, 物件應該在`IUnknown::Release`任何現有的網站上呼叫, 而物件不會再知道其網站。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="setsite"></a>IObjectWithSiteImpl:: SetSite

提供具有網站`IUnknown`指標的物件。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
