---
title: IOleInPlace 無視窗函數類別
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
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326571"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlace 無視窗函數類別

此類實現`IUnknown`並提供了使無視窗控制項能夠接收視窗訊息和參與拖放操作的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IOleInPlaceObjectWindowlessImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleInPlace 無視窗::上下文敏感説明](#contextsensitivehelp)|啟用上下文相關的説明。 ATL 實現返回E_NOTIMPL。|
|[IOleInPlace 無視窗::取得刪除目標](#getdroptarget)|為支援拖`IDropTarget`放的就地活動、無視窗物件提供介面。 ATL 實現返回E_NOTIMPL。|
|[IOleInPlace 無視窗::抓取視窗](#getwindow)|獲取視窗句柄。|
|[IOleinplace 無視窗::原位停用](#inplacedeactivate)|停用活動就地控件。|
|[IOleInPlace 無視窗::在視窗訊息](#onwindowmessage)|將消息從容器調度到處於活動位置的無視窗控制項。|
|[IOleInPlace 無視窗::重新啟動和Undo](#reactivateandundo)|重新啟動以前停用的控制項。 ATL 實現返回E_NOTIMPL。|
|[IOleInPlace 無視窗::設定物件重新物件](#setobjectrects)|指示就地控件的哪一部分可見。|
|[IOleInPlace 無視窗::UIdede](#uideactivate)|停用並刪除支援就地啟動的用戶介面。|

## <a name="remarks"></a>備註

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)介面管理就地控制項重新啟動和停用,並確定該控制項應可見的數量。 [IOleInPlace 無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)介面使無視窗控制項能夠接收視窗訊息並參與拖放操作。 類`IOleInPlaceObjectWindowlessImpl`通過在調試生成中`IOleInPlaceObject`向`IOleInPlaceObjectWindowless`轉儲`IUnknown`設備發送 資訊來提供 和和實現的預設實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlace 無視窗::上下文敏感説明

返回E_NOTIMPL。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>備註

請參閱[IOleWindow:Windows](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) SDK 中的上下文敏感説明。

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlace 無視窗::取得刪除目標

返回E_NOTIMPL。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>備註

請參閱[IOleInPlace 無視窗::在](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget)Windows SDK 中獲取 DropTarget。

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlace 無視窗::抓取視窗

容器呼叫此函數以獲取控制項的視窗句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>備註

某些容器不適用於無視窗控制項,即使它當前是視窗的。 在 ATL 的實現中,如果控制類`m_bWasOnceWindowless`的數據成員 為 TRUE,則函數返回E_FAIL。 否則,如果*phwnd*不是`GetWindow`NULL,則\*將*phwnd*設置到控制項`m_hWnd`類的數據成員並返回S_OK。

請參閱[IOleWindow:在](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow)Windows SDK 中獲取視窗。

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleinplace 無視窗::原位停用

容器調用以停用就地活動控制件。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>備註

此方法執行完全或部分停用,具體取決於控件的狀態。 如有必要,將停用控制項的使用者介面,並銷毀控制件的視窗(如果有)。 將通知容器控件不再處於活動狀態。 容器`IOleInPlaceUIWindow`用於協商功能表和邊框空間的介面被釋放。

請參閱[IOleInPlace 物件:在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate)Windows SDK 中原地停用。

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlace 無視窗::在視窗訊息

將消息從容器調度到處於活動位置的無視窗控制項。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>備註

請參閱[IOleInPlace 無視窗:Windows](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) SDK 中的「視窗訊息」。

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlace 無視窗::重新啟動和Undo

返回E_NOTIMPL。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>備註

請參閱[IOleInPlace 物件::在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo)Windows SDK 中重新啟動並撤銷。

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlace 無視窗::設定物件重新物件

容器調用以通知控制項其大小和/或位置已更改。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>備註

更新控制項`m_rcPos`的數據成員和控制顯示。 僅顯示與剪輯區域相交的控制部分。 如果控件的顯示以前已剪切,但剪切已被刪除,則可以調用此功能以重繪控制件的完整視圖。

請參閱[IOleInPlace 物件:在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects)Windows SDK 中設置物件重新物件。

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlace 無視窗::UIdede

停用並刪除控制項支援就地啟動的用戶介面。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>備註

將控制類的數據成員`m_bUIActive`設置為 FALSE。 此函數的 ATL 實現始終返回S_OK。

請參閱[IOleInPlace 物件::在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate)Windows SDK 中啟動 UI。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
