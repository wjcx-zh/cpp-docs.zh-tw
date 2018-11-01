---
title: CPaneFrameWnd 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
dev_langs:
- C++
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb6e87d9deac7a6d0082480196b7dbeecf5a85b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081075"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd 類別

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

實作包含一個窗格的迷你框架視窗。 窗格會填滿視窗的工作區。

## <a name="syntax"></a>語法

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|加入窗格。|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|從全域清單中加入或移除窗格。|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|調整迷你框架視窗的配置。|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|計算迷你框架視窗的框線大小。|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|計算預期的固定視窗矩形。|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|決定目前的窗格是否可以固定到另一個窗格或框架視窗。|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|決定迷你框架視窗是否可以固定到窗格。|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|將窗格轉換為索引標籤式文件。|
|[CPaneFrameWnd::Create](#create)|建立迷你框架視窗，並將其附加至 `CPaneFrameWnd` 物件。|
|[CPaneFrameWnd::CreateEx](#createex)|建立迷你框架視窗，並將其附加至 `CPaneFrameWnd` 物件。|
|[CPaneFrameWnd::DockPane](#dockpane)|固定窗格。|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|在浮動窗格的全域清單中尋找具有指定控制項 ID 的窗格。|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|尋找包含使用者提供之點的迷你框架視窗。|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|傳回迷你框架視窗標題的高度。|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|傳回迷你框架視窗標題的週框。|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|傳回標題文字。|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|傳回固定模式。|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|傳回包含在迷你框架視窗中的第一個可見窗格。|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|傳回包含在迷你框架視窗中的窗格。|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|傳回包含在迷你框架視窗中的窗格數目。|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|傳回包含在迷你框架視窗中的可見窗格數目。|
|[CPaneFrameWnd::HitTest](#hittest)|判斷迷你框架視窗的哪個部分位於給定的點上。|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|決定是否應展開迷你框架視窗。|
|[CPaneFrameWnd::IsRollUp](#isrollup)|決定是否應縮合迷你框架視窗。|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|停止固定計時器。|
|[CPaneFrameWnd::LoadState](#loadstate)|從登錄載入窗格的狀態。|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|判斷是否可固定。|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|將迷你框架視窗固定在其最近的位置上。|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|停止彙總計時器。|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|以指定的位移移動迷你框架視窗。|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|調整所含窗格的配置。|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|設定彙總計時器。|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|在隱藏或顯示迷你框架視窗中的窗格時，由架構呼叫。|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|如果在迷你框架視窗內包含使用者提供的點，則會傳回一個窗格。|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。|
|[CPaneFrameWnd::RedrawAll](#redrawall)|重新繪製所有的迷你框架視窗。|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|由架構呼叫以移除無效窗格。|
|[CPaneFrameWnd::RemovePane](#removepane)|從迷你框架視窗中移除窗格。|
|[CPaneFrameWnd::ReplacePane](#replacepane)|以一個窗格取代另一個。|
|[CPaneFrameWnd::SaveState](#savestate)|將窗格的狀態儲存至登錄。|
|`CPaneFrameWnd::Serialize`|從封存中讀取或寫入此物件。|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|動作標題按鈕。|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|設定固定計時器。|
|[CPaneFrameWnd::SetDockState](#setdockstate)|設定固定狀態。|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|由架構呼叫以設定預先固定狀態。|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|調整迷你框架視窗的大小，使其大小等同於所含窗格的大小。|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|清除功能表。|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|決定應縮合還是展開迷你框架視窗。|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|繪製迷你框架視窗的框線。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|指定是否要向 CS_SAVEBITS 類別樣式的視窗類別。|

## <a name="remarks"></a>備註

當窗格從固定狀態切換至浮動狀態時，此架構會自動建立 `CPaneFrameWnd` 物件。

迷你框架視窗可在其內容可見的情況下進行拖曳 (即時固定)，或使用拖曳矩形 (標準固定)。 迷你框架容器窗格的固定模式會決定迷你框架的拖曳行為。 如需詳細資訊，請參閱 < [cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。

迷你框架視窗會根據包含的窗格樣式顯示標題的按鈕。 如果窗格可以關閉 ( [cbasepane:: Canbeclosed](../../mfc/reference/cbasepane-class.md#canbeclosed))，它會顯示 [關閉] 按鈕。 如果窗格具有 AFX_CBRS_AUTO_ROLLUP 樣式，它會顯示 pin。

如果您從 `CPaneFrameWnd` 衍生類別，您必須向架構指出如何建立該類別。 建立類別藉由覆寫[cpane:: Createdefaultminiframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)，或設定`CPane::m_pMiniFrameRTC`成員使其指向您的類別的執行階段類別資訊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>需求

**標頭：** afxPaneFrameWnd.h

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

加入窗格。

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]將窗格。

##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList

從全域清單中加入或移除窗格。

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]若要新增或移除窗格。

*bAdd*<br/>
[in]如果不是零，新增 [] 窗格。 如果為 0，移除窗格。

### <a name="return-value"></a>傳回值

如果方法成功，為非零否則為 0。

##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout

調整迷你框架視窗的配置。

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>  CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>備註

##  <a name="calcbordersize"></a>  CPaneFrameWnd::CalcBorderSize

計算迷你框架的框線大小。

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>參數

*rectBorderSize*<br/>
[out]包含大小，單位為像素的迷你框架的框線。

### <a name="remarks"></a>備註

呼叫這個方法是由架構計算迷你框架的框線大小。 傳回的大小取決於迷你框架包含工具列還是[CDockablePane](../../mfc/reference/cdockablepane-class.md)。

##  <a name="calcexpecteddockedrect"></a>  CPaneFrameWnd::CalcExpectedDockedRect

計算預期的固定視窗矩形。

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>參數

*pWndToDock*<br/>
[in]若要停駐視窗的指標。

*ptMouse*<br/>
[in]滑鼠位置。

*rectResult*<br/>
[out]導出的矩形。

*bDrawTab*<br/>
[out]如果為 TRUE，繪製索引標籤。如果為 FALSE，不繪製索引標籤。

*ppTargetBar*<br/>
[out]對 [目標] 窗格的指標。

### <a name="remarks"></a>備註

這個方法會計算如果使用者拖曳到所指定的點的視窗，視窗會佔據的矩形*ptMouse*而那里將它停駐。

##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached

決定目前的窗格是否可以固定到另一個窗格或框架視窗。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>傳回值

如果另一個窗格或框架視窗，可以停駐窗格中，則為 TRUE。否則為 FALSE。

##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane

決定迷你框架視窗是否可以固定到窗格。

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>參數

*pDockingBar*<br/>
[in]窗格中。

### <a name="return-value"></a>傳回值

如果可以停駐迷你框架為非零*pDockingBar*，否則為 0。

##  <a name="checkgrippervisibility"></a>  CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>備註

##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument

將窗格轉換為索引標籤式文件。

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>  CPaneFrameWnd::Create

建立迷你視窗，並將它附加至[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)物件。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*lpszWindowName*<br/>
[in]指定要顯示在迷你框架上的文字。

*cheaderctrl:: Create*<br/>
[in]指定的視窗樣式。 如需詳細資訊，請參閱 <<c0> [ 的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
[in]指定的初始大小和位置的迷你框架。

*pParentWnd*<br/>
[in、 out]指定父框架的迷你框架。 此值必須不是 NULL。

*pContext*<br/>
[in、 out]指定使用者定義的內容。

### <a name="return-value"></a>傳回值

如果視窗已成功; 建立，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

迷你框架會建立兩個步驟。 首先，此架構會建立`CPaneFrameWnd`物件。 第二，它會呼叫`Create`建立 Windows 迷你框架，並將其附加至`CPaneFrameWnd`物件。

##  <a name="createex"></a>  CPaneFrameWnd::CreateEx

建立迷你視窗，並將它附加至[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)物件。

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>參數

*dwStyleEx*<br/>
[in]指定延伸的視窗樣式。 如需詳細資訊，請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
[in]指定要顯示在迷你框架上的文字。

*cheaderctrl:: Create*<br/>
[in]指定的視窗樣式。 如需詳細資訊，請參閱 <<c0> [ 的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
[in]指定的初始大小和位置的迷你框架。

*pParentWnd*<br/>
[in、 out]指定父框架的迷你框架。 此值必須不是 NULL。

*pContext*<br/>
[in、 out]指定使用者定義的內容。

### <a name="return-value"></a>傳回值

如果視窗已成功; 建立，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

迷你框架會建立兩個步驟。 首先，此架構會建立`CPaneFrameWnd`物件。 第二，它會呼叫`Create`建立 Windows 迷你框架，並將其附加至`CPaneFrameWnd`物件。

##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane

固定窗格。

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>參數

*bWasDocked*<br/>
[out]如果窗格已停駐;，則為 TRUE。否則為 FALSE。

### <a name="return-value"></a>傳回值

如果作業成功，`CDockablePane`窗格已停駐於，否則為 NULL。

##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID

在浮動窗格的全域清單中尋找具有指定控制項 ID 的窗格。

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
[in]表示要尋找窗格的控制項 ID。

### <a name="return-value"></a>傳回值

使用指定的控制項 ID; 窗格否則為 NULL，如果沒有窗格就會有指定的控制項 id。

##  <a name="framefrompoint"></a>  CPaneFrameWnd::FrameFromPoint

尋找包含指定的點的迷你框架視窗。

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
[in]螢幕座標中的點。

*nSensitivity*<br/>
[in]增加這個大小的迷你框架視窗的 [搜尋] 區域。 如果指定的點落在增加的區域，迷你框架視窗會符合搜尋準則。

*pFrameToExclude*<br/>
[in]指定的迷你框架視窗，從搜尋結果中排除。

*bFloatMultiOnly*<br/>
[in]如果為 TRUE，只會搜尋具有 CBRS_FLOAT_MULTI 樣式的迷你框架視窗。 如果為 FALSE，搜尋所有的迷你框架視窗。

### <a name="return-value"></a>傳回值

包含的迷你框架視窗的指標*pt*，否則為 NULL。

##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight

傳回迷你框架視窗標題的高度。

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>傳回值

高度，單位為像素的迷你框架視窗。

### <a name="remarks"></a>備註

呼叫這個方法來決定迷你框架視窗的高度。 根據預設，高度設為 SM_CYSMCAPTION。 如需詳細資訊，請參閱 < [GetSystemMetrics 函式](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics)。

##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect

傳回迷你框架視窗標題的週框。

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>參數

*rectCaption*<br/>
[out]包含的迷你框架視窗標題，螢幕座標中的位置與大小。

### <a name="remarks"></a>備註

計算迷你框架視窗標題的週框矩形的架構會呼叫這個方法。

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

傳回標題文字。

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>傳回值

迷你框架視窗的標題文字。

### <a name="remarks"></a>備註

顯示的標題文字時，這個方法是由架構呼叫。

##  <a name="getdockingmanager"></a>  CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode

傳回固定模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>傳回值

停駐的模式。 下列其中一個值：

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane

傳回包含在迷你框架視窗中的第一個可見窗格。

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>傳回值

迷你框架視窗中或 NULL，如果在迷你框架視窗不包含任何窗格中的第一個窗格。

##  <a name="gethotpoint"></a>  CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpane"></a>  CPaneFrameWnd::GetPane

傳回包含在迷你框架視窗中的窗格。

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>傳回值

如果在迷你框架視窗不包含任何窗格包含在迷你框架，則為 NULL 的窗格。

### <a name="remarks"></a>備註

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

傳回包含在迷你框架視窗中的窗格數目。

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>傳回值

在迷你框架視窗的窗格數目。 這個值可以是零。

### <a name="remarks"></a>備註

##  <a name="getparent"></a>  CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getrecentfloatingrect"></a>  CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount

傳回包含在迷你框架視窗中的可見窗格數目。

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>傳回值

可見窗格數目。

### <a name="remarks"></a>備註

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

判斷迷你框架視窗的哪個部分位於給定的點上。

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>參數

*點*<br/>
[in]要測試的點。

*bDetectCaption*<br/>
[in]如果為 TRUE，請檢查針對標題的點。 如果為 FALSE，會忽略的標題。

### <a name="return-value"></a>傳回值

下列其中一個值：

|值|意義|
|-----------|-------------|
|HTNOWHERE|重點是外部的迷你框架視窗。|
|HTCLIENT|重點是工作區中。|
|HTCAPTION|重點是標題。|
|HTTOP|重點是在最上方。|
|HTTOPLEFT|重點是在左上方。|
|HTTOPRIGHT|重點是右上方。|
|HTLEFT|重點是左邊。|
|HTRIGHT|重點是在右邊。|
|HTBOTTOM|重點是在底部。|
|HTBOTTOMLEFT|重點是左下方。|
|HTBOTTOMRIGHT|重點是右下方。|

##  <a name="iscaptured"></a>  CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown

決定是否應展開迷你框架視窗。

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>傳回值

如果在迷你框架視窗必須復原關閉;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

由架構決定迷你框架視窗是否應該關閉復原，會呼叫這個方法。 如果它包含已 AFX_CBRS_AUTO_ROLLUP 旗標的至少一個窗格的迷你框架視窗啟用彙總套件/用功能。 建立一個窗格時，會設定這個旗標。 如需詳細資訊，請參閱 < [cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

根據預設，架構會檢查是否將滑鼠指標位於迷你框架視窗周框，以判斷視窗是否具有向下復原。 您可以覆寫此行為在衍生類別中。

##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp

決定是否應縮合迷你框架視窗。

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>傳回值

如果在迷你框架視窗必須將彙總;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法是由架構來判斷是否應縮合迷你框架視窗。 如果它包含已 AFX_CBRS_AUTO_ROLLUP 旗標的至少一個窗格的迷你框架視窗啟用彙總套件/用功能。 建立一個窗格時，會設定這個旗標。 如需詳細資訊，請參閱 < [cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

根據預設，架構會檢查是否將滑鼠指標位於迷你框架視窗周框，以判斷視窗是否具有彙總。 您可以覆寫此行為在衍生類別中。

##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer

停止固定計時器。

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState

從登錄載入窗格的狀態。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]設定檔名稱。

*uiID*<br/>
[in]窗格中的識別碼。

### <a name="return-value"></a>傳回值

如果窗格狀態載入成功，則為 TRUE否則為 FALSE。

##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits

指定是否要註冊具有 CS_SAVEBITS 類別樣式的視窗類別。

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>備註

設定這個靜態成員，以 true 登錄 CS_SAVEBITS 樣式的迷你框架視窗類別。 這可能有助於減少閃爍當使用者拖曳迷你框架視窗。

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

判斷是否可固定。

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>傳回值

如果停駐是可行的;，則為 TRUE。否則為 FALSE。

##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState

決定應縮合還是展開迷你框架視窗。

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>備註

判斷迷你框架視窗是否應該在增加或相應減少復原架構會呼叫這個方法。

根據預設，架構會呼叫[CPaneFrameWnd::IsRollUp](#isrollup)並[CPaneFrameWnd::IsRollDown](#isrolldown)就會自動縮放或還原迷你框架視窗。 您可以覆寫這個方法在衍生類別使用不同的視覺效果中。

##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos

將迷你框架視窗固定在其最近的位置上。

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder

繪製迷你框架視窗的框線。

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容，用來繪製框線。

### <a name="remarks"></a>備註

呼叫這個方法是由架構在繪製迷你框架視窗的框線。

##  <a name="onkillrolluptimer"></a>  CPaneFrameWnd::OnKillRollUpTimer

停止彙總計時器。

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane

以指定的位移移動迷你框架視窗。

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in]指標 （忽略） 窗格。

*ptOffset*<br/>
[in]用來移動窗格位移。

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

調整迷你框架視窗中窗格的配置。

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>備註

當它必須調整迷你框架視窗內的窗格的配置時，架構會呼叫這個方法。

根據預設，[] 窗格位於以涵蓋完整的工作區的迷你框架視窗。

##  <a name="onsetrolluptimer"></a>  CPaneFrameWnd::OnSetRollUpTimer

設定彙總計時器。

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane

在隱藏或顯示迷你框架視窗中的窗格時，由架構呼叫。

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in][] 窗格所顯示或隱藏。

*bShow*<br/>
[in]如果正在顯示] 窗格;，則為 TRUE。如果隱藏的窗格中，則為 FALSE。

### <a name="remarks"></a>備註

迷你框架視窗中的窗格會顯示或隱藏時由架構呼叫。 預設實作不做任何動作。

##  <a name="pin"></a>  CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>參數

[in]*bPin*<br/>

### <a name="remarks"></a>備註

##  <a name="panefrompoint"></a>  CPaneFrameWnd::PaneFromPoint

如果在迷你框架視窗內包含使用者提供的點，則會傳回一個窗格。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>參數

*點*<br/>
[in]點使用者點選，以螢幕座標。

*nSensitivity*<br/>
[in]未使用此參數。

*bCheckVisibility*<br/>
[in]TRUE 會指定代表不應傳回只有可見窗格;否則為 FALSE。

### <a name="return-value"></a>傳回值

窗格中按一下使用者或如果該位置的任何窗格不則為 NULL。

### <a name="remarks"></a>備註

呼叫這個方法來取得包含指定的點的窗格。

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

重新繪製所有的迷你框架視窗。

```
static void RedrawAll();
```

### <a name="remarks"></a>備註

這個方法會更新所有的迷你框架視窗呼叫[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)針對每個視窗。

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

由架構呼叫以移除無效窗格。

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane

從迷你框架視窗中移除窗格。

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]若要移除窗格指標。

*bDestroy*<br/>
[in]指定迷你框架視窗會發生什麼事。 如果*bDestroy*為 TRUE 時，這個方法會立即終結迷你框架視窗。 如果是 FALSE，則這個方法會在特定的延遲之後終結迷你框架視窗。

*bNoDelayedDestroy*<br/>
[in]如果為 TRUE，則會停用延遲的解構。 如果為 FALSE，則會啟用延遲的解構。

### <a name="remarks"></a>備註

立即或在特定的延遲之後，架構會損毀的迷你框架視窗。 如果您想要延遲解構的迷你框架視窗，則會傳遞 FALSE *bNoDelayedDestroy*參數。 當處理 AFX_WM_CHECKEMPTYMINIFRAME 訊息架構時，就會發生延遲的解構。

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

以一個窗格取代另一個。

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>參數

*pBarOrg*<br/>
[in]到 [原始] 窗格的指標。

*pBarReplaceWith*<br/>
[in]指標，會取代原始的窗格的窗格。

##  <a name="savestate"></a>  CPaneFrameWnd::SaveState

將窗格的狀態儲存至登錄。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]設定檔名稱。

*uiID*<br/>
[in]窗格中的識別碼。

### <a name="return-value"></a>傳回值

如果已成功; 儲存窗格狀態，則為 TRUE。否則為 FALSE。

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

動作標題按鈕。

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>參數

*dwButtons*<br/>
[in]下列值的位元 OR 組合：

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>參數

[in]*bDelayShow*<br/>

### <a name="remarks"></a>備註

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>參數

[in]*pManager*<br/>

### <a name="remarks"></a>備註

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

設定固定計時器。

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>參數

*nTimeOut*<br/>
[in]以毫秒為單位的逾時值。

##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState

設定固定狀態。

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>參數

*pDockManager*<br/>
[in]停駐的管理員指標。

##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>參數

[in]*ptNew*<br/>

### <a name="remarks"></a>備註

##  <a name="setpredockstate"></a>  CPaneFrameWnd::SetPreDockState

由架構呼叫以設定預先固定狀態。

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>參數

*preDockState*<br/>
[in]可能的值：

- PDS_NOTHING，

- PDS_DOCK_REGULAR，

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
[in]若要停駐窗格的指標。

*dockMethod*<br/>
[in]停駐的方法。 （會忽略這個參數）。

### <a name="return-value"></a>傳回值

如果未停駐; 迷你框架視窗，則為 TRUE。如果停駐，則為 FALSE。

##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent

調整迷你框架視窗的大小，使它就相當於所含的窗格。

```
virtual void SizeToContent();
```

### <a name="remarks"></a>備註

呼叫這個方法來調整大小所含窗格的迷你框架視窗的大小。

##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff

清除功能表。

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
[in]功能表指標。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>參數

[in]*pBar*<br/>

### <a name="remarks"></a>備註

##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>參數

[in]*pDockingBar*<br/>
[in]*pTabbedBar*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
