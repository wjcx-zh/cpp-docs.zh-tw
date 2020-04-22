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
ms.openlocfilehash: 409c97aba64c97ecf0443d14a70848cc298a44ba
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749996"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 類別

對`CMFCReBar`像是一個控件欄,它為鋼筋控件提供佈局、持久性和狀態資訊。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCReBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCReBar:addBar](#addbar)|將帶添加到鋼筋。|
|[CMFCReBar::鈣固定佈局](#calcfixedlayout)|(覆蓋[CBasePane::CalcFixed 佈局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar:可以浮動](#canfloat)|(覆蓋[CBasePane::可以浮動](../../mfc/reference/cbasepane-class.md#canfloat). )|
|[CMFCReBar:建立](#create)|創建鋼筋控件並將其附加到`CMFCReBar`物件。|
|[CMFCReBar:啟用停靠](#enabledocking)|(覆蓋[CBasePane:啟用停靠](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar:取得雷巴班德資訊大小](#getrebarbandinfosize)||
|[CMFCReBar:GetReBarCtrl](#getrebarctrl)|提供對基礎[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)公共控制項的直接存取。|
|[CMFCReBar:在顯示控制列選單](#onshowcontrolbarmenu)|(覆蓋[CPane:在顯示控制欄選單](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCRebar::在工具命中測試](#ontoolhittest)|(覆蓋[Cwnd:onToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest))|
|[CMFCReBar:關於更新CmdUI](#onupdatecmdui)|(覆蓋[CBasePane::更新 CmdUI](cbasepane-class.md).)|
|[CMFCReBar::設定窗格對齊](#setpanealignment)|(覆蓋[CBasePane:設定窗格對齊](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>備註

物件`CMFCReBar`可以包含各種子視窗。 這包括編輯框、工具列和列表框。 您可以以程式設計方式調整鋼筋的大小,或者使用者可以通過拖動鋼筋來手動調整鋼筋的大小。 您還可以將鋼筋物件的背景設置為您選擇的點陣圖。

鋼筋對象的行為與工具欄對象類似。 鋼筋控件可以包含一個或多個波段,每個波段可以包含夾持條、位圖、文本標籤和子視窗。

## <a name="example"></a>範例

下例示範如何在 `CMFCReBar` 類別中使用各種方法。 該示例演示如何創建鋼筋控件並將其添加帶。 波段用作內部工具列。 此代碼段是[鋼筋測試示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目標](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>需求

**標題:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar:addBar

將帶添加到鋼筋。

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
[進出]指向要插入鋼筋的子視窗的指標。 引用的物件必須具有**WS_CHILD**視窗樣式。

*pszText*<br/>
[在]指定要顯示在鋼筋上的文本。 文字不是子視窗的一部分。 相反,它顯示在鋼筋本身。

*pbmp*<br/>
[進出]指定要顯示在鋼筋背景上的點陣圖。

*dwStyle*<br/>
[在]包含要應用於波段的樣式。 有關波段樣式的完整清單,請參閱 Windows SDK`fStyle`文件中的[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構中的說明。

*clrFore*<br/>
[在]表示鋼筋的前景顏色。

*clrBack*<br/>
[在]表示鋼筋的背景顏色。

### <a name="return-value"></a>傳回值

如果頻帶已成功添加到鋼筋中,則為 TRUE;否則,FALSE。

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar:建立

創建鋼筋控制程式並將其附加到[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)物件。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
[進出]指向此鋼筋控件的父窗口的指標。

*dwCtrl風格*<br/>
[在]指定鋼筋控件的樣式。 默認樣式值為**RBS_BANDBORDERS**,它顯示窄線以分隔鋼筋控件上的相鄰波段。 有關有效樣式的清單,請參閱 Windows SDK 文件中的[鋼筋控制樣式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
[在]鋼筋控件的視窗樣式。 關於有效樣式的清單,請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
[在]鋼筋的子窗口 ID。

### <a name="return-value"></a>傳回值

如果成功創建鋼筋,則為 TRUE;如果鋼筋已成功創建,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar:GetReBarCtrl

提供對`CReBarCtrl`物件基礎公共控件的`CMFCReBar`直接訪問。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

對基礎`CReBarCtrl`物件的引用。

### <a name="remarks"></a>備註

調用此方法以在自定義鋼筋時利用 Windows 鋼筋通用控制功能。

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::鈣固定佈局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[在]*b 伸*<br/>
[在]*布霍茲*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar:可以浮動

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar:啟用停靠

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

[在]*dwDock 風格*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar:取得雷巴班德資訊大小

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar:在顯示控制列選單

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>參數

[在]*CPoint*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCRebar::在工具命中測試

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>參數

[在]*點*<br/>
[在]*pTI*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar:關於更新CmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

[在]*p 目標*<br/>
[在]*b 關閉IfNoHndler*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar::設定窗格對齊

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>參數

[在]*dwalignment*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl 類別](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
