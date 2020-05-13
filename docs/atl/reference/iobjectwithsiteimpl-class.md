---
title: IObject 與 Siteimpl 類別
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
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329649"
---
# <a name="iobjectwithsiteimpl-class"></a>IObject 與 Siteimpl 類別

此類提供允許物件與其網站通信的方法。

## <a name="syntax"></a>語法

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IObjectWithSiteImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IObject 與網站impl::取得網站](#getsite)|查詢介面指標的網站。|
|[IObject 與網站impl::設定兒童網站](#setchildsite)|使用網站的`IUnknown`指標向物件提供。|
|[IObject 與網站impl::設定網站](#setsite)|使用網站的`IUnknown`指標向物件提供。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IObject 與 Siteimpl::m_spUnkSite](#m_spunksite)|管理網站的`IUnknown`指標。|

## <a name="remarks"></a>備註

[IObject WithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)介面允許物件與其網站通信。 類`IObjectWithSiteImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

`IObjectWithSiteImpl`指定兩種方法。 用戶端首先調用`SetSite`,傳遞網站的`IUnknown`指標。 此指標存儲在物件中,以後可以通過調用`GetSite`來檢索。

通常,在創建不是控制項的物件`IObjectWithSiteImpl`時,派生類。 對於控件,從[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)派生類 ,該函數還提供網站指標。 不要從`IObjectWithSiteImpl`和`IOleObjectImpl`派生類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObject 與網站impl::取得網站

查詢網站的指向 標識的介面的`riid`指標。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>備註

如果網站支援此介面,則通過`ppvSite`返回指標。 否則,`ppvSite`設定為 NULL。

請參閱[IObject 與網站::在](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite)Windows SDK 中獲取網站。

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObject 與 Siteimpl::m_spUnkSite

管理網站的`IUnknown`指標。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>備註

`m_spUnkSite`最初通過調用[SetSite](#setsite)接收此指標。

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObject 與網站impl::設定兒童網站

使用網站的`IUnknown`指標向物件提供。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>參數

*pUnkSite*<br/>
[在]指向管理此`IUnknown`物件的網站的介面指標。 如果 NULL,則物件`IUnknown::Release`應 呼叫物件不再知道其網站的任何現有網站。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObject 與網站impl::設定網站

使用網站的`IUnknown`指標向物件提供。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>備註

請參閱[IObject 與網站::在](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)Windows SDK 中設置網站。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
