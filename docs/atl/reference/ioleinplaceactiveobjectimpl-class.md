---
title: IOleInPlaceActiveObjectImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: f52638c8a28652cc958ebb3d774319ab37a3c46d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495765"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 類別

這個類別會提供方法來協助就地控制項與其容器之間的通訊。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IOleInPlaceActiveObjectImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|啟用非強制回應對話方塊。 ATL 實作為傳回 S_OK。|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|取得視窗控制碼。|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|當容器的文件視窗已啟用或停用時, 通知控制項。 ATL 實作為傳回 S_OK。|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|當容器的最上層框架視窗已啟用或停用時, 通知控制項。 ATL 執行會傳回|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控制項它需要調整其框線大小。 ATL 實作為傳回 S_OK。|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|處理功能表快速鍵-來自容器的索引鍵訊息。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)介面可協助就地控制項與其容器之間的通訊;例如, 傳達控制項和容器的作用中狀態, 並通知控制項它需要自行調整大小。 類別`IOleInPlaceActiveObjectImpl`會提供的`IOleInPlaceActiveObject`預設執行, 並`IUnknown`支援將資訊傳送至偵錯工具組建中的傾印裝置。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

啟用即時線上說明。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleWindow:: CoNtextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 。

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

啟用非強制回應對話方塊。

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) 。

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

容器會呼叫這個函式, 以取得控制項的視窗控制碼。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>備註

某些容器無法與沒有視窗的控制項搭配使用, 即使它目前是視窗型也一樣。 在 ATL 的實值中, `CComControl::m_bWasOnceWindowless`如果資料成員為 TRUE, 則函數會傳回 E_FAIL。 否則, 如果\* *phwnd*不是 Null, `GetWindow`則會將*phwnd*指派給控制項類別的`m_hWnd`資料成員, 並傳回 S_OK。

請參閱 Windows SDK 中的[IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 。

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

當容器的文件視窗已啟用或停用時, 通知控制項。

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceActiveObject:: ondocwindowactivate 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)。

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

當容器的最上層框架視窗已啟用或停用時, 通知控制項。

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceActiveObject:: onframewindowactivate 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。

##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder

通知控制項它需要調整其框線大小。

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceActiveObject:: resizeborder 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)。

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

處理功能表快速鍵-來自容器的索引鍵訊息。

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>傳回值

這個方法支援下列傳回值：

如果訊息轉譯成功, 則為 S_OK。

如果未轉譯訊息, 則為 S_FALSE。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) 。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制項介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別總覽](../../atl/atl-class-overview.md)
