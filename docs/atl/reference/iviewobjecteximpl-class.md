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
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495495"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 類別

這個`IUnknown`類別會執行並提供[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)介面的預設執行。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IViewObjectExImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|在裝置內容上繪製控制項的標記法。|
|[IViewObjectExImpl::Freeze](#freeze)|凍結控制項的繪製表示，使其不會變更到`Unfreeze`。 ATL 執行會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetAdvise](#getadvise)|抓取控制項上的現有諮詢接收連接（如果有的話）。|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|傳回控制項用於繪製的邏輯調色板。 ATL 執行會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetExtent](#getextent)|從控制項類別資料成員[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)，以 HIMETRIC 單位（每單位0.01 毫米）抓取控制項的顯示大小。|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供容器的調整大小提示，讓物件在使用者調整其大小時使用。|
|[IViewObjectExImpl::GetRect](#getrect)|傳回描述要求的繪圖外觀的矩形。 ATL 執行會傳回 E_NOTIMPL。|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|傳回物件不透明度和支援之繪圖層面的相關資訊。|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|檢查指定的點是否在指定的矩形中，並在中`pHitResult`傳回 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|檢查控制項的顯示矩形是否與指定之位置矩形中的任何點重迭，並傳回中`pHitResult`的 HITRESULT 值。|
|[IViewObjectExImpl::SetAdvise](#setadvise)|設定控制項和通知接收之間的連接，讓接收可以收到有關控制項視圖中變更的通知。|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes 控制項的繪製標記法。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)介面可讓控制項直接顯示本身，以及建立和管理通知接收，以通知容器控制項顯示中的變更。 `IViewObjectEx`介面提供延伸控制功能的支援，例如不具閃爍的繪圖、非矩形和透明控制項，以及點擊測試（例如，在控制項上按一下滑鼠按鍵的方式）。 類別`IViewObjectExImpl`提供這些介面的預設執行，並藉`IUnknown`由將資訊傳送至偵錯工具中的傾印裝置來實現。

## <a name="inheritance-hierarchy"></a>繼承階層

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="draw"></a>IViewObjectExImpl：:D raw

在裝置內容上繪製控制項的標記法。

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

這個方法會`CComControl::OnDrawAdvanced`呼叫，進而呼叫控制項類別的`OnDraw`方法。 當您使用 ATL 控制項嚮導來建立控制項時，方法會自動加入至您的控制項類別。`OnDraw` Wizard 的預設`OnDraw`會繪製一個具有 "ATL 3.0" 標籤的矩形。

請參閱 Windows SDK 中的[IViewObject：:D raw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) 。

##  <a name="freeze"></a>IViewObjectExImpl：：凍結

凍結控制項的繪製表示，使其不會變更到`Unfreeze`。 ATL 執行會傳回 E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IViewObject：：凍結](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze)。

##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise

抓取控制項上的現有諮詢接收連接（如果有的話）。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>備註

諮詢接收會儲存在控制項類別資料成員[CComControlBase：： m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中。

請參閱 Windows SDK 中的[IViewObject：： GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) 。

##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

傳回控制項用於繪製的邏輯調色板。 ATL 執行會傳回 E_NOTIMPL。

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

請參閱 Windows SDK 中的[IViewObject：： GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) 。

##  <a name="getextent"></a>IViewObjectExImpl：： GetExtent

從控制項類別資料成員[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)，以 HIMETRIC 單位（每單位0.01 毫米）抓取控制項的顯示大小。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IViewObject2：： GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) 。

##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

提供容器的調整大小提示，讓物件在使用者調整其大小時使用。

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

如果`dwAspect`為 DVASPECT_CONTENT，而*pExtentInfo > dwExtentMode*為 DVEXTENT_CONTENT，則會`psizel`將 * 設定為控制項類別的資料成員[CComControlBase：： m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否則，會傳回錯誤 HRESULT。

請參閱 Windows SDK 中的[IViewObjectEx：： GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) 。

##  <a name="getrect"></a>IViewObjectExImpl::GetRect

傳回描述要求的繪圖外觀的矩形。 ATL 執行會傳回 E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IViewObjectEx：： GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) 。

##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

傳回物件不透明度和支援之繪圖層面的相關資訊。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

根據預設，ATL 會`pdwStatus`設定以指出控制項支援 VIEWSTATUS_OPAQUE （可能的值位於[VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus)列舉中）。

請參閱 Windows SDK 中的[IViewObjectEx：： GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) 。

##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

檢查指定的點是否在指定的矩形中，並在中`pHitResult`傳回 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

此值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等於[DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)，方法會傳回 S_OK。 否則，方法會傳回 E_FAIL。

請參閱 Windows SDK 中的[IViewObjectEx：： QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) 。

##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

檢查控制項的顯示矩形是否與指定之位置矩形中的任何點重迭，並傳回中`pHitResult`的 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>備註

此值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等於[DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)，方法會傳回 S_OK。 否則，方法會傳回 E_FAIL。

請參閱 Windows SDK 中的[IViewObjectEx：： QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) 。

##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise

設定控制項和通知接收之間的連接，讓接收可以收到有關控制項視圖中變更的通知。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>備註

建議接收上[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面的指標會儲存在控制項類別資料成員[CComControlBase：： m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)中。

請參閱 Windows SDK 中的[IViewObject：： SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) 。

##  <a name="unfreeze"></a>IViewObjectExImpl：：解凍

Unfreezes 控制項的繪製標記法。 ATL 執行會傳回 E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IViewObject：：解凍](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)。

##  <a name="closehandle"></a>IWorkerThreadClient：： CloseHandle

執行這個方法，以關閉與此物件相關聯的控制碼。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
要關閉的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給這個方法的控制碼先前已藉由呼叫[CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

下列程式碼顯示的簡單執行`IWorkerThreadClient::CloseHandle`。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>IWorkerThreadClient：： Execute

當與這個物件相關聯的控制碼變成信號時，請執行這個方法來執行程式碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*dwParam*<br/>
User 參數。

*hObject*<br/>
已收到信號的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳遞給這個方法的控制碼和 DWORD/指標先前已藉由呼叫[CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)與此物件相關聯。

### <a name="example"></a>範例

下列程式碼顯示的簡單執行`IWorkerThreadClient::Execute`。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制項介面](/windows/win32/com/activex-controls-interfaces)<br/>
[教學課程](../../atl/active-template-library-atl-tutorial.md)<br/>
[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
