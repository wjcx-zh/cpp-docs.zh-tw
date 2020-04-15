---
title: IViewObjectEximpl 類別
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
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326348"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectEximpl 類別

`IUnknown`此類實現並提供[IViewObject、IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject)[IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)介面的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IViewObjectExImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IViewObjectEximpl::D原始](#draw)|將控制項的表示形式繪製到設備上下文中。|
|[IViewObjectEximpl::凍結](#freeze)|凍結控件的繪製表示形式,使其直到不會`Unfreeze`更改。 ATL 實現返回E_NOTIMPL。|
|[IViewObjectEximpl::取得建議](#getadvise)|檢索控件上的現有通知接收器連接(如果有)。|
|[IViewObjectEximpl::取得顏色集](#getcolorset)|返回控制項用於繪圖的邏輯調色板。 ATL 實現返回E_NOTIMPL。|
|[IViewObjectEximpl::取得範圍](#getextent)|從控制類數據成員[CComControlBase:m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)檢索控件的顯示大小(以 HIMETRIC 單位(單位 0.01 毫米為單位)。|
|[IViewObjectEximpl::取得自然範圍](#getnaturalextent)|提供容器的大小調整提示,供物件在使用者調整大小時使用。|
|[IViewObjectEximpl::取得 Rect](#getrect)|返回描述請求的繪圖方面的矩形。 ATL 實現返回E_NOTIMPL。|
|[IViewObjectEximpl::取得查看狀態](#getviewstatus)|返回有關物件的不一性以及支援哪些繪圖方面的資訊。|
|[IViewObjectEximpl::查詢HitPoint](#queryhitpoint)|檢查指定點是否位於指定的矩形中,並在中`pHitResult`返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。|
|[IViewObjectEximpl::查詢希特](#queryhitrect)|檢查控制項的顯示矩形是否與指定位置矩形中的任何點重疊,並在`pHitResult`中返回 HITRESULT 值。|
|[IViewObjectEximpl::設定建議](#setadvise)|在控制項和通知接收器之間設定連接,以便通知接收器有關控制件檢視中的更改。|
|[IViewObjectEximpl::解凍](#unfreeze)|解凍控件的繪製表示形式。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

[IViewObject、IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)介面使控制項能夠直接顯示自身,並創建和管理建議接收器,以通知容器控制項顯示中的更改。 該`IViewObjectEx`介面支援擴展控制功能,如無閃爍繪圖、非矩形和透明控制件以及命中測試(例如,必須在控制項上考慮滑鼠按一下的接近程度)。 類`IViewObjectExImpl`通過在調試版本中向轉儲設備發送資訊`IUnknown`來 提供這些介面和實現的默認實現。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectEximpl::D原始

將控制項的表示形式繪製到設備上下文中。

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

此方法調用`CComControl::OnDrawAdvanced`控件`OnDraw`類 的方法,進而調用控件類的方法。 使用`OnDraw`ATL 控制件精靈建立控制項時,方法將自動添加到控制項類別中。 嚮導的預設值`OnDraw`繪製一個帶有「ATL 3.0」標籤的矩形。

請參閱[IViewObject::D原始](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)在 Windows SDK 中。

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectEximpl::凍結

凍結控件的繪製表示形式,使其直到不會`Unfreeze`更改。 ATL 實現返回E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>備註

請參閱[IViewObject:凍結](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze)在 Windows SDK 中。

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectEximpl::取得建議

檢索控件上的現有通知接收器連接(如果有)。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>備註

通知接收器儲存在控制類別資料成員[CComControlBase:m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。

請參閱[IViewObject:在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise)Windows SDK 中獲取建議。

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectEximpl::取得顏色集

返回控制項用於繪圖的邏輯調色板。 ATL 實現返回E_NOTIMPL。

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

請參閱[IViewObject:在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset)Windows SDK 中獲取ColorSet。

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectEximpl::取得範圍

從控制類數據成員[CComControlBase:m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)檢索控件的顯示大小(以 HIMETRIC 單位(單位 0.01 毫米為單位)。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>備註

請參閱[IViewObject2::在](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent)Windows SDK 中獲取範圍。

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectEximpl::取得自然範圍

提供容器的大小調整提示,供物件在使用者調整大小時使用。

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

如果`dwAspect`DVASPECT_CONTENT和*pAandinfo->dwAAndMode*是`psizel`DVEXTENT_CONTENT,則將 * 設定到控制類的資料成員[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否則,返回錯誤 HRESULT。

請參閱[IViewObjectEx:在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent)Windows SDK 中獲取自然範圍。

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectEximpl::取得 Rect

返回描述請求的繪圖方面的矩形。 ATL 實現返回E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>備註

請參閱[IViewObjectEx:在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect)Windows SDK 中獲取 Rect。

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectEximpl::取得查看狀態

返回有關物件的不一性以及支援哪些繪圖方面的資訊。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

默認情況下,ATL設置`pdwStatus`以指示控制項支援VIEWSTATUS_OPAQUE(可能的值位於["視圖狀態](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚舉"中)。

請參閱[IViewObjectEx:在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus)Windows SDK 中獲取查看狀態。

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectEximpl::查詢HitPoint

檢查指定點是否位於指定的矩形中,並在中`pHitResult`返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

該值可以是HITRESULT_HIT,也可以是HITRESULT_OUTSIDE。

如果`dwAspect`等於[DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)則該方法將返回S_OK。 否則,該方法將返回E_FAIL。

請參閱[IViewObjectEx:在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint)Windows SDK 中查詢 HitPoint。

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectEximpl::查詢希特

檢查控制項的顯示矩形是否與指定位置矩形中的任何點重疊,並在`pHitResult`中返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

該值可以是HITRESULT_HIT,也可以是HITRESULT_OUTSIDE。

如果`dwAspect`等於[DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)則該方法將返回S_OK。 否則,該方法將返回E_FAIL。

請參閱[IViewObjectEx:在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect)Windows SDK 中查詢Hitrect。

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectEximpl::設定建議

在控制項和通知接收器之間設定連接,以便通知接收器有關控制件檢視中的更改。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>備註

指向建議接收器上的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面的指標儲存在控制類資料成員[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。

請參閱[IViewObject:在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise)Windows SDK 中設置建議。

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectEximpl::解凍

解凍控件的繪製表示形式。 ATL 實現返回E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>備註

請參閱[IViewObject:在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)Windows SDK 中解凍。

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThread用戶端::關閉句柄

實現此方法以關閉與此物件關聯的句柄。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
要關閉的句柄。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時出現錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給此方法的句柄以前通過調用[CWorkerThread::addHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

以下代碼顯示了`IWorkerThreadClient::CloseHandle`的簡單實現。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThread用戶端:執行

實現此方法,當與此物件關聯的句柄發出信號時執行代碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*德帕拉姆*<br/>
用戶參數。

*hObject*<br/>
已發出信號的句柄。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時出現錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給此方法的句柄和 DWORD/指標以前通過調用[CWorkerThread::addHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

以下代碼顯示了`IWorkerThreadClient::Execute`的簡單實現。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制介面](/windows/win32/com/activex-controls-interfaces)<br/>
[教學課程](../../atl/active-template-library-atl-tutorial.md)<br/>
[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
