---
title: IViewObjectExImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 4ed7a7e4a6070ba52c54c4dace687111cf7d33d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301931"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 類別

這個類別會實作`IUnknown`並提供的預設實作[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，和[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)介面。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IViewObjectExImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|繪製至裝置內容控制的表示法。|
|[IViewObjectExImpl::Freeze](#freeze)|凍結的控制項繪製的表示法，因此它不會變更之前`Unfreeze`。 ATL 實作會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果有的話，請擷取現有的通知接收連接在控制項上。|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|傳回用於繪製控制項的邏輯調色盤。 ATL 實作會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetExtent](#getextent)|控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐） 擷取控制項的類別資料成員[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供的容器使用，因為在使用者調整物件大小的提示。|
|[IViewObjectExImpl::GetRect](#getrect)|傳回矩形，描述要求的繪圖外觀。 ATL 實作會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|傳回物件和繪圖外觀所支援的不透明度的相關資訊。|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|檢查指定的點是否位於指定的矩形，並傳回[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|檢查是否在控制項的顯示矩形重疊的指定的位置的矩形中的任何時間點，並傳回在 HITRESULT 值`pHitResult`。|
|[IViewObjectExImpl::SetAdvise](#setadvise)|設定控制項和通知接收之間的連線以便接收要收到在控制項的檢視中的變更。|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes 控制項的繪製表示法。 ATL 實作會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，並[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)介面可讓控制項直接顯示本身也可以建立和管理通知接收通知變更控制項顯示的容器。 `IViewObjectEx`介面的支援擴充的控制項的功能，例如無重繪閃動的繪圖、 非矩形和透明的控制項，和點擊測試 （例如，如何關閉按下滑鼠必須視為在控制項上）。 類別`IViewObjectExImpl`提供這些介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

## <a name="inheritance-hierarchy"></a>繼承階層

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

繪製至裝置內容控制的表示法。

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>備註

這個方法會呼叫`CComControl::OnDrawAdvanced`接著呼叫您的控制項類別`OnDraw`方法。 `OnDraw`方法會自動加入至您的控制項類別使用 ATL 控制項精靈建立您的控制項時。 精靈的預設`OnDraw`標籤"ATL 3.0 」 以繪製一個矩形。

請參閱[iviewobject:: Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) Windows SDK 中。

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

凍結的控制項繪製的表示法，因此它不會變更之前`Unfreeze`。 ATL 實作會傳回 E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>備註

請參閱[IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) Windows SDK 中。

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

如果有的話，請擷取現有的通知接收連接在控制項上。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>備註

通知接收會儲存在控制項類別資料成員[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。

請參閱[IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) Windows SDK 中。

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

傳回用於繪製控制項的邏輯調色盤。 ATL 實作會傳回 E_NOTIMPL。

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>備註

請參閱[IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) Windows SDK 中。

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐） 擷取控制項的類別資料成員[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>備註

請參閱[IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) Windows SDK 中。

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

提供的容器使用，因為在使用者調整物件大小的提示。

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>備註

如果`dwAspect`是 DVASPECT_CONTENT 並*pExtentInfo]-> [dwExtentMode* DVEXTENT_CONTENT，設定 *`psizel`控制項類別的資料成員[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否則，會傳回錯誤 HRESULT。

請參閱[IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) Windows SDK 中。

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

傳回矩形，描述要求的繪圖外觀。 ATL 實作會傳回 E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>備註

請參閱[IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) Windows SDK 中。

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

傳回物件和繪圖外觀所支援的不透明度的相關資訊。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

根據預設，設定 ATL`pdwStatus`表示此控制項支援 VIEWSTATUS_OPAQUE (可能的值位於[forced VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus)列舉型別)。

請參閱[IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) Windows SDK 中。

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

檢查指定的點是否位於指定的矩形，並傳回[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`equals [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)，此方法會傳回 S_OK。 否則，這個方法會傳回 E_FAIL。

請參閱[IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) Windows SDK 中。

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

檢查是否在控制項的顯示矩形重疊的指定的位置的矩形中的任何時間點，並傳回[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`equals [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)，此方法會傳回 S_OK。 否則，這個方法會傳回 E_FAIL。

請參閱[IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) Windows SDK 中。

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

設定控制項和通知接收之間的連線以便接收要收到在控制項的檢視中的變更。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>備註

將指標[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)通知接收上的介面會儲存在控制項類別資料成員[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。

請參閱[IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) Windows SDK 中。

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Unfreezes 控制項的繪製表示法。 ATL 實作會傳回 E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>備註

請參閱[IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) Windows SDK 中。

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

實作此方法以關閉這個物件相關聯的控制代碼。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
關閉控制代碼。

### <a name="return-value"></a>傳回值

在成功或失敗的錯誤 HRESULT 傳回 S_OK。

### <a name="remarks"></a>備註

控制代碼傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>範例

下列程式碼顯示的簡單實作`IWorkerThreadClient::CloseHandle`。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

實作這個方法，這個物件相關聯的控制代碼會變成收到訊號時執行程式碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*dwParam*<br/>
User 參數。

*hObject*<br/>
變成已收到訊號的控制代碼。

### <a name="return-value"></a>傳回值

在成功或失敗的錯誤 HRESULT 傳回 S_OK。

### <a name="remarks"></a>備註

控制代碼和 DWORD/指標傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>範例

下列程式碼顯示的簡單實作`IWorkerThreadClient::Execute`。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制項介面](/windows/desktop/com/activex-controls-interfaces)<br/>
[教學課程](../../atl/active-template-library-atl-tutorial.md)<br/>
[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
