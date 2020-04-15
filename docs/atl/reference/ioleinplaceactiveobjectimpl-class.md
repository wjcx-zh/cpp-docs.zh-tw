---
title: IOleInplace 主動物件內普爾類
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
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326592"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInplace 主動物件內普爾類

此類提供了協助就地控件與其容器之間通信的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IOleInPlaceActiveObjectImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleInPlace 主動物件impl::上下文敏感説明](#contextsensitivehelp)|啟用上下文相關的説明。 ATL 實現返回E_NOTIMPL。|
|[IOleInPlace 主動物件impl::啟用無模式](#enablemodeless)|啟用無模式對話方塊。 ATL 實現返回S_OK。|
|[IOleinPlace 主動物件impl::取得視窗](#getwindow)|獲取視窗句柄。|
|[IOleinplace 主動物件impl::在DocWindow啟動](#ondocwindowactivate)|啟動或停用容器的文件視窗時通知控制項。 ATL 實現返回S_OK。|
|[IOleinPlace 主動物件impl::在框架視窗啟動](#onframewindowactivate)|啟動或停用容器的頂層框架視窗時通知控制項。 ATL 實現傳回|
|[IOleInPlace 主動物件impl::調整邊框](#resizeborder)|通知控件需要調整其邊框的大小。 ATL 實現返回S_OK。|
|[IOleInPlace主動物件impl::翻譯加速器](#translateaccelerator)|處理來自容器的功能表快捷鍵消息。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)介面可説明就地控制件與其容器之間的通信;例如,通信控制件和容器的活動狀態,並通知控制項需要調整自身大小。 類`IOleInPlaceActiveObjectImpl`通過在調試生成中`IOleInPlaceActiveObject`向 轉`IUnknown`儲設備 發送資訊,提供和的默認實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlace 主動物件impl::上下文敏感説明

啟用上下文相關的説明。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleWindow:Windows](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) SDK 中的上下文敏感説明。

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlace 主動物件impl::啟用無模式

啟用無模式對話方塊。

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleInPlace 活動物件::](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)在 Windows SDK 中啟用無模式。

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleinPlace 主動物件impl::取得視窗

容器呼叫此函數以獲取控制項的視窗句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>備註

某些容器不適用於無視窗控制項,即使它當前是視窗的。 在 ATL 的`CComControl::m_bWasOnceWindowless`實現中 ,如果數據成員為 TRUE,則函數返回E_FAIL。 否則,如果\**phwnd*不是`GetWindow`NULL,則將*phwnd*分配`m_hWnd`給控制項類的數據 成員並返回S_OK。

請參閱[IOleWindow:在](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow)Windows SDK 中獲取視窗。

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleinplace 主動物件impl::在DocWindow啟動

啟動或停用容器的文件視窗時通知控制項。

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleInPlace 活動物件:在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)Windows SDK 中啟動 OnDocWindow。

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleinPlace 主動物件impl::在框架視窗啟動

啟動或停用容器的頂層框架視窗時通知控制項。

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleInPlace 活動物件:在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)Windows SDK 中啟動 FrameWindow。

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlace 主動物件impl::調整邊框

通知控件需要調整其邊框的大小。

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleInPlace 活動物件::在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)Windows SDK 中調整邊框大小。

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlace主動物件impl::翻譯加速器

處理來自容器的功能表快捷鍵消息。

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>傳回值

這個方法支援下列傳回值：

S_OK郵件是否已成功翻譯。

如果未翻譯郵件,S_FALSE。

### <a name="remarks"></a>備註

請參閱[IOleInPlace 活動物件::在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)Windows SDK 中翻譯加速器。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別概觀](../../atl/atl-class-overview.md)
