---
title: IOleInPlaceObjectWindowlessImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: df14c22f5cf4828b51bf03f6d0f0c4c20cf5a009
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267169"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 類別

這個類別會實作`IUnknown`，並提供啟用無視窗控制項接收視窗訊息，以及參與拖放作業的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IOleInPlaceObjectWindowlessImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供`IDropTarget`就地使用中的無視窗物件的支援拖放介面。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|取得視窗控制代碼。|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用作用中的現用控制項。|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|會從容器是就地啟用作用中的無視窗控制項的訊息分派。|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新啟動之前已停用的控制項。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|表示顯示就地控制項的哪個部分。|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用，並移除支援就地啟用的使用者介面。|

## <a name="remarks"></a>備註

[IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject)介面管理重新啟用和停用就地的控制，並決定控制項中有多少應該為可見的。 [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)介面，可讓 「 接收視窗訊息，以及參與拖放作業的無視窗控制項。 類別`IOleInPlaceObjectWindowlessImpl`提供的預設實作`IOleInPlaceObject`並`IOleInPlaceObjectWindowless`並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

傳回 E_NOTIMPL。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>備註

請參閱[IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) Windows SDK 中。

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

傳回 E_NOTIMPL。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>備註

請參閱[IOleInPlaceObjectWindowless::GetDropTarget](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) Windows SDK 中。

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

容器會呼叫此函式來取得控制項的視窗控制代碼。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>備註

某些容器無法運作，無視窗，即使它是目前的視窗型控制項。 在 ATL 的實作中，如果控制項類別的資料成員`m_bWasOnceWindowless`為 TRUE，則函數會傳回 E_FAIL。 否則，如果*phwnd*不是 NULL，`GetWindow`設定\* *phwnd*至控制項類別的資料成員`m_hWnd`，並傳回 S_OK。

請參閱[IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) Windows SDK 中。

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

呼叫所要停用就地使用中控制項的容器。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>備註

這個方法會執行完整或部分的停用，根據控制項的狀態。 如有必要，停用控制項的使用者介面，並終結控制項的視窗中，如果有的話。 容器會收到通知，控制項不再使用中的位置。 `IOleInPlaceUIWindow`協調功能表和框線空間的容器所使用的介面釋放。

請參閱[IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) Windows SDK 中。

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

會從容器是就地啟用作用中的無視窗控制項的訊息分派。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>備註

請參閱[IOleInPlaceObjectWindowless::OnWindowMessage](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) Windows SDK 中。

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

傳回 E_NOTIMPL。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>備註

請參閱[IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) Windows SDK 中。

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

呼叫以通知控制項已變更其大小和 （或） 位置的容器。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>備註

更新控制項的`m_rcPos`資料成員和控制項顯示。 顯示只控制項相交的裁剪區域的一部分。 如果先前已裁剪控制項的顯示，但已移除裁剪，您就可以呼叫此函式來重繪控制項的完整檢視。

請參閱[IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) Windows SDK 中。

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

停用，並移除支援就地啟用的控制項的使用者介面。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>備註

設定控制項類別的資料成員`m_bUIActive`為 FALSE。 此函式的 ATL 實作一律會傳回 S_OK。

請參閱[IOleInPlaceObject::UIDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
