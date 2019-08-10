---
title: CMFCReBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: ccd500547bdcf65e922f7b5e5ca8d30e0423933d
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866175"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 類別

`CMFCReBar`物件是一種控制列, 可提供 Rebar 控制項的版面配置、持續性和狀態資訊。
如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。
## <a name="syntax"></a>語法

```
class CMFCReBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|將寬線加入至 Rebar。|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(覆寫[CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CMFCReBar::CanFloat](#canfloat)|(覆寫[CBasePane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|
|[CMFCReBar::Create](#create)|建立 Rebar 控制項並將其附加至`CMFCReBar`物件。|
|[CMFCReBar::EnableDocking](#enabledocking)|(覆寫[CBasePane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|提供基礎[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)通用控制項的直接存取權。|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(覆寫[CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(覆寫[CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)。)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(覆寫[CBasePane:: OnUpdateCmdUI](cbasepane-class.md)。)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(覆寫[CBasePane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)。)|

## <a name="remarks"></a>備註

`CMFCReBar`物件可以包含各種不同的子視窗。 這包括編輯方塊、工具列和清單方塊。 您可以透過程式設計的方式調整 Rebar 的大小, 或者使用者可以拖曳其移駐列來手動調整 Rebar 大小。 您也可以將 Rebar 物件的背景設定為您所選擇的點陣圖。

Rebar 物件的行為類似工具列物件。 Rebar 控制項可以包含一個或多個群組, 而且每個寬線都可以包含移駐夾列、點陣圖、文字標籤和子視窗。

## <a name="example"></a>範例

下例示範如何在 `CMFCReBar` 類別中使用各種方法。 這個範例會示範如何建立 Rebar 控制項, 並在其中加入一個寬線。 寬頻功能會當做內部工具列。 此程式碼片段是[Rebar 測試範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>需求

**標頭:** afxRebar。h

##  <a name="addbar"></a>CMFCReBar::AddBar

將寬線加入至 Rebar。

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in、out]要插入至 Rebar 之子視窗的指標。 參考的物件必須具有**WS_CHILD**視窗樣式。

*pszText*<br/>
在指定要出現在 Rebar 上的文字。 文字不是子視窗的一部分。 相反地, 它會顯示在 Rebar 本身。

*pbmp*<br/>
[in、out]指定要在 Rebar 背景上顯示的點陣圖。

*dwStyle*<br/>
在包含要套用至寬線的樣式。 如需頻外樣式的完整清單, 請參閱 Windows SDK `fStyle`檔中[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)結構的描述。

*clrFore*<br/>
在代表 Rebar 的前景色彩。

*clrBack*<br/>
在代表 Rebar 的背景色彩。

### <a name="return-value"></a>傳回值

如果已成功將寬線加入至 Rebar, 則為 TRUE;否則為 FALSE。

##  <a name="create"></a>CMFCReBar:: Create

建立 Rebar 控制項, 並將它附加至[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)物件。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
[in、out]這個 Rebar 控制項的父視窗指標。

*dwCtrlStyle*<br/>
在指定 Rebar 控制項的樣式。 預設的樣式值為**RBS_BANDBORDERS**, 它會顯示窄行來分隔 Rebar 控制項上的相鄰群組。 如需有效樣式的清單, 請參閱 Windows SDK 檔中的[Rebar 控制項樣式](/windows/desktop/Controls/rebar-control-styles)。

*dwStyle*<br/>
在Rebar 控制項的視窗樣式。 如需有效樣式的清單, 請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
在Rebar 的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果已成功建立 Rebar, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="getrebarctrl"></a>CMFCReBar:: GetReBarCtrl

提供`CMFCReBar`物件之基礎`CReBarCtrl`通用控制項的直接存取權。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

基礎`CReBarCtrl`物件的參考。

### <a name="remarks"></a>備註

呼叫此方法可在自訂 Rebar 時, 利用 Windows Rebar 通用控制項功能。

##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

在*bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="canfloat"></a>CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="enabledocking"></a>CMFCReBar:: EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

[in] *dwDockStyle*<br/>

### <a name="remarks"></a>備註

##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>參數

在*CPoint*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ontoolhittest"></a>CMFCReBar:: OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>參數

在*點*<br/>
[in] *pTI*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onupdatecmdui"></a>CMFCReBar:: OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

[in] *pTarget*<br/>
[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>備註

##  <a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>參數

在*dwAlignment*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl 類別](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane 類別](../../mfc/reference/cpane-class.md)
