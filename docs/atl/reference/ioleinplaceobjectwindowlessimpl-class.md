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
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495740"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 類別

這個類別`IUnknown`會執行並提供方法, 以啟用無視窗控制項來接收視窗訊息, 以及參與拖放作業。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IOleInPlaceObjectWindowlessImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|為支援拖放功能的就地作用中的無視窗物件提供介面。`IDropTarget` ATL 執行會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|取得視窗控制碼。|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用現用的就地控制項。|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|將來自容器的訊息分派至就地作用中的無視窗控制項。|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新啟動先前停用的控制項。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|表示可以看到就地控制項的哪個部分。|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用並移除支援就地啟用的使用者介面。|

## <a name="remarks"></a>備註

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)介面會管理就地控制項的重新開機和停用, 並決定應顯示多少控制項。 [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)介面可讓無視窗控制項接收視窗訊息, 以及參與拖放作業。 類別`IOleInPlaceObjectWindowlessImpl`提供`IOleInPlaceObject`和`IUnknown`的預設執行, 並在偵錯工具中將資訊傳送至傾印裝置。 `IOleInPlaceObjectWindowless`

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

傳回 E_NOTIMPL。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleWindow:: CoNtextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 。

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

傳回 E_NOTIMPL。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) 。

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

容器會呼叫這個函式, 以取得控制項的視窗控制碼。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>備註

某些容器無法與沒有視窗的控制項搭配使用, 即使它目前是視窗型也一樣。 在 ATL 的執行中, 如果控制項類別的資料成員`m_bWasOnceWindowless`為 TRUE, 則函數會傳回 E_FAIL。 否則, 如果*phwnd*不是 Null, `GetWindow`會\*將*phwnd*設定為控制項類別的資料`m_hWnd`成員, 並傳回 S_OK。

請參閱 Windows SDK 中的[IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 。

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

由容器呼叫以停用就地現用控制項。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>備註

視控制項的狀態而定, 這個方法會執行完整或部分停用。 如有必要, 會停用控制項的使用者介面, 並終結控制項的視窗 (如果有的話)。 容器會收到通知, 指出控制項已不再作用中。 已`IOleInPlaceUIWindow`釋放容器用來協調功能表和邊界空間的介面。

請參閱 Windows SDK 中的[IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) 。

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

將來自容器的訊息分派至就地作用中的無視窗控制項。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) 。

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

傳回 E_NOTIMPL。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) 。

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

由容器呼叫, 以通知控制項其大小和/或位置已變更。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>備註

更新控制項的`m_rcPos`資料成員和控制項顯示。 只會顯示與剪輯區域相交的控制項部分。 如果控制項的顯示先前已裁剪, 但已移除裁剪, 則可以呼叫此函式來重繪控制項的完整視圖。

請參閱 Windows SDK 中的[IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) 。

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

停用並移除支援就地啟用的控制項使用者介面。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>備註

將控制項類別的資料成員`m_bUIActive`設定為 FALSE。 此函式的 ATL 實作為一律會傳回 S_OK。

請參閱 Windows SDK 中的[IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) 。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
