---
title: CAtlPreviewCtrlimpl 類別
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
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321361"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlimpl 類別

此類是放置在「豐富預覽」的 Shell 提供的主機視窗中的視窗的 ATL 實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlimpl::_CatlPreviewCtrlimpl](#dtor)|析構預覽控件物件。|
|[CAtlPreviewCtrlimpl::CAtlPreviewCtrlimpl](#catlpreviewctrlimpl)|構造預覽控件物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlimpl::建立](#create)|由「豐富預覽」處理程式呼叫以創建 Windows 視窗。|
|[CAtlPreviewCtrlImpl::D](#destroy)|當需要銷毀此控件時,由富預覽處理程序調用。|
|[CAtlPreviewCtrlimpl::聚焦](#focus)|對這個控制項設定輸入焦點。|
|[CAtlPreviewCtrlimpl::在油漆上](#onpaint)|處理WM_PAINT消息。|
|[CAtlPreviewCtrlImpl::重繪](#redraw)|告訴此控制件重繪。|
|[CAtlPreviewCtrlimpl::SetHost](#sethost)|為此控件設置新父級。|
|[CAtlPreviewCtrlImpl::設定預覽視覺物件](#setpreviewvisuals)|當需要設置富預覽內容的可視物件時,由"豐富預覽"處理程序調用。|
|[CAtlPreviewCtrlimpl::Setrect](#setrect)|為此控件設置一個新的邊界矩形。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlimpl::DoPaint](#dopaint)|由框架調用以呈現預覽。|

### <a name="protected-constants"></a>受保護的常量

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|用於在預覽視窗中顯示文本的字型。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|預覽視窗的背景顏色。|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|預覽視窗的文字顏色。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::C視窗,CAtlPreviewCtrlimpl>\<](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>需求

**標題:** atlpreviewctrlimpl.h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlimpl::CAtlPreviewCtrlimpl

構造預覽控件物件。

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlimpl::_CatlPreviewCtrlimpl

析構預覽控件物件。

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlimpl::建立

由「豐富預覽」處理程式呼叫以創建 Windows 視窗。

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
用於富預覽的 Shell 提供的主機視窗的句柄。

*中國*<br/>
指定視窗的初始大小和位置。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::D

當需要銷毀此控件時,由富預覽處理程序調用。

```
virtual void Destroy();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlimpl::DoPaint

由框架調用以呈現預覽。

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>參數

*hdc*<br/>
用於繪製的設備上下文的句柄。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlimpl::聚焦

對這個控制項設定輸入焦點。

```
virtual void Focus();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

預覽視窗的背景顏色。

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

預覽視窗的文字顏色。

```
COLORREF m_clrText;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

用於在預覽視窗中顯示文本的字型。

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlimpl::在油漆上

處理WM_PAINT消息。

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
設置為WM_PAINT。

*wParam*<br/>
不使用這個參數。

*lParam*<br/>
不使用這個參數。

*bHandled*<br/>
當此函數返回時,它包含 TRUE。

### <a name="return-value"></a>傳回值

永遠傳回 0。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::重繪

告訴此控制件重繪。

```
virtual void Redraw();
```

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlimpl::SetHost

為此控件設置新父級。

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
新父視窗的句柄。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::設定預覽視覺物件

當需要設置富預覽內容的可視物件時,由"豐富預覽"處理程序調用。

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>參數

*clrBack*<br/>
預覽視窗的背景顏色。

*clrText*<br/>
預覽視窗的文字顏色。

*plf*<br/>
用於在預覽視窗中顯示文本的字型。

### <a name="remarks"></a>備註

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlimpl::Setrect

為此控件設置一個新的邊界矩形。

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>參數

*中國*<br/>
指定預覽控制件的新大小和位置。

*bredraw*<br/>
指定是否應重繪控制件。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
