---
title: CAtlPreviewCtrlImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167873"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 類別

這個類別是視窗的 ATL 實作為，其放在 Shell 提供供豐富預覽的主機視窗上。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 預覽控制項物件。|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|構造預覽控制項物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： Create](#create)|由豐富的預覽處理常式呼叫以建立 Windows 視窗。|
|[CAtlPreviewCtrlImpl：:D estroy](#destroy)|當需要終結此控制項時，由豐富的預覽處理常式呼叫。|
|[CAtlPreviewCtrlImpl：： Focus](#focus)|對這個控制項設定輸入焦點。|
|[CAtlPreviewCtrlImpl：： OnPaint](#onpaint)|處理 WM_PAINT 訊息。|
|[CAtlPreviewCtrlImpl：：重繪](#redraw)|告訴此控制項重繪。|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|設定這個控制項的新父系。|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|當需要設定豐富預覽內容的視覺效果時，由豐富的預覽處理常式呼叫。|
|[CAtlPreviewCtrlImpl：： SetRect](#setrect)|為這個控制項設定新的周框。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：:D oPaint](#dopaint)|由架構呼叫以呈現預覽。|

### <a name="protected-constants"></a>受保護的常數

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： m_plf](#m_plf)|用來在 [預覽] 視窗中顯示文字的字型。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： m_clrBack](#m_clrback)|預覽視窗的背景色彩。|
|[CAtlPreviewCtrlImpl：： m_clrText](#m_clrtext)|預覽視窗的文字色彩。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL：： CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>需求

**標頭：** atlpreviewctrlimpl。h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

構造預覽控制項物件。

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl：： ~ CAtlPreviewCtrlImpl

Destructs 預覽控制項物件。

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl：： Create

由豐富的預覽處理常式呼叫以建立 Windows 視窗。

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
適用于 Rich Preview 的 Shell 所提供的主機視窗控制碼。

*臺灣*<br/>
指定視窗的初始大小和位置。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl：:D estroy

當需要終結此控制項時，由豐富的預覽處理常式呼叫。

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl：:D oPaint

由架構呼叫以呈現預覽。

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>參數

*hdc*<br/>
用於繪製之裝置內容的控制碼。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl：： Focus

對這個控制項設定輸入焦點。

```cpp
virtual void Focus();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl：： m_clrBack

預覽視窗的背景色彩。

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl：： m_clrText

預覽視窗的文字色彩。

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl：： m_plf

用來在 [預覽] 視窗中顯示文字的字型。

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl：： OnPaint

處理 WM_PAINT 訊息。

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
設定為 WM_PAINT。

*wParam*<br/>
不使用這個參數。

*lParam*<br/>
不使用這個參數。

*bHandled*<br/>
當此函式傳回時，它會包含 TRUE。

### <a name="return-value"></a>傳回值

永遠傳回 0。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl：：重繪

告訴此控制項重繪。

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

設定這個控制項的新父系。

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
新父視窗的控制碼。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

當需要設定豐富預覽內容的視覺效果時，由豐富的預覽處理常式呼叫。

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>參數

*clrBack*<br/>
預覽視窗的背景色彩。

*clrText*<br/>
預覽視窗的文字色彩。

*plf*<br/>
用來在 [預覽] 視窗中顯示文字的字型。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl：： SetRect

為這個控制項設定新的周框。

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>參數

*臺灣*<br/>
指定預覽控制項的新大小和位置。

*bRedraw*<br/>
指定是否應該重新繪製控制項。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
