---
title: CDockSite Class
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: 9c154fe621fb88a6dc96a9835fae95c4b86763de
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866198"
---
# <a name="cdocksite-class"></a>CDockSite Class

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

提供可將衍生自 [CPane Class](../../mfc/reference/cpane-class.md) 的窗格排列成資料列集合的功能。

## <a name="syntax"></a>語法

```
class CDockSite: public CBasePane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite:: AdjustDockingLayout](#adjustdockinglayout)|(覆寫[CBasePane:: AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)。)|
|[CDockSite:: AdjustLayout](#adjustlayout)|(覆寫[CBasePane:: AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout)。)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(覆寫[CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(覆寫[CBasePane:: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)。)|
|[CDockSite::CreateEx](#createex)|(覆寫[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(覆寫[CBasePane::D ockpane](../../mfc/reference/cbasepane-class.md#dockpane)。)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(覆寫[CBasePane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite:: FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(覆寫 `CBasePane::IsAccessibilityCompatible`。)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(覆寫[CBasePane:: IsResizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|由給定參數指定時，傳回停駐於停駐位置的窗格。|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐於另一個窗格的左邊。|
|[CDockSite::FindPaneByID](#findpanebyid)|傳回給定識別碼所識別的窗格。|
|[CDockSite::GetPaneList](#getpanelist)|傳回停駐於停駐位置的窗格清單。|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|顯示窗格。|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>備註

當您呼叫`CDockSite` [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)時, 架構會自動建立物件。 停駐位置視窗位於主框架視窗上用戶端區域的邊緣。

您通常不需要呼叫 dock 網站所提供的服務, 因為[CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)會處理這些服務。

## <a name="example"></a>範例

下列範例示範如何建立 `CDockSite` 類別的物件。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>需求

**標頭:** afxDockSite。h

##  <a name="addrow"></a>CDockSite:: AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>參數

在*pos*<br/>

[in] *nHeight*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="adjustdockinglayout"></a>CDockSite:: AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>備註

##  <a name="adjustlayout"></a>CDockSite:: AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>備註

##  <a name="aligndocksite"></a>CDockSite:: AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>參數

在*rectToAlignBy*<br/>

在*rectResult*<br/>

在*bMoveImmediately*<br/>

### <a name="remarks"></a>備註

##  <a name="calcfixedlayout"></a>CDockSite:: CalcFixedLayout

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

##  <a name="canacceptpane"></a>CDockSite:: CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

在*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createex"></a>CDockSite:: CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

在*dwStyleEx*<br/>

在*dwStyle*<br/>

在*rect*<br/>

[in] *pParentWnd*<br/>

[in] *dwControlBarStyle*<br/>

在*pCoNtext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createrow"></a>CDockSite:: CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>參數

[in] *pParentDockBar*<br/>

在*nOffset*<br/>

[in] *nRowHeight*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="dockpane"></a>CDockSite::D ockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

[in] *pWnd*<br/>

在*dockMethod*<br/>

[in] *lpRect*<br/>

### <a name="remarks"></a>備註

##  <a name="dockpaneleftof"></a>CDockSite::D ockPaneLeftOf

將窗格停駐於另一個窗格的左邊。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>參數

*pBarToDock*<br/>
[in、out]要停駐在*pTargetBar*左邊的窗格指標。

*pTargetBar*<br/>
[in、out]目標窗格的指標。

### <a name="return-value"></a>傳回值

如果窗格已成功停駐, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="doesallowdyninsertbefore"></a>CDockSite::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="findpanebyid"></a>CDockSite:: FindPaneByID

傳回具有指定識別碼的窗格。

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
在要尋找之窗格的命令識別碼。

### <a name="return-value"></a>傳回值

具有指定命令識別碼之窗格的指標, 如果找不到窗格, 則為 Null。

### <a name="remarks"></a>備註

##  <a name="findrowindex"></a>CDockSite:: FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[in] *pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="fixupvirtualrects"></a>CDockSite:: FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>備註

##  <a name="getdocksiteid"></a>CDockSite:: GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdocksiterowslist"></a>CDockSite:: GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanelist"></a>CDockSite:: GetPaneList

傳回固定在停駐網站中的窗格清單。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>傳回值

目前停駐在停駐列之窗格清單的唯讀參考。

##  <a name="isaccessibilitycompatible"></a>CDockSite:: IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isdragmode"></a>CDockSite:: IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="islastrow"></a>CDockSite:: IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>參數

[in] *pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isrectwithindocksite"></a>CDockSite:: IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>參數

在*rect*<br/>

[in] *ptDelta*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isresizable"></a>CDockSite:: IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="movepane"></a>CDockSite:: MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>參數

[in] *pWnd*<br/>

在*nFlags*<br/>

[in] *ptOffset*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="oninsertrow"></a>CDockSite:: OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>參數

在*pos*<br/>

### <a name="remarks"></a>備註

##  <a name="onremoverow"></a>CDockSite:: OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>參數

在*pos*<br/>

[in] *bByShow*<br/>

### <a name="remarks"></a>備註

##  <a name="onresizerow"></a>CDockSite:: OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>參數

[in] *pRowToResize*<br/>

在*nOffset*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onsizeparent"></a>CDockSite:: OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>參數

在*rectAvailable*<br/>

在*russinovich*<br/>

在*bExpand*<br/>

在*nOffset*<br/>

### <a name="remarks"></a>備註

##  <a name="onsetwindowpos"></a>CDockSite:: OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

[in] *pWndInsertAfter*<br/>

在*rectWnd*<br/>

在*nFlags*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onshowrow"></a>CDockSite:: OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>參數

在*pos*<br/>

在*bShow*<br/>

### <a name="remarks"></a>備註

##  <a name="panefrompoint"></a>CDockSite::P aneFromPoint

由給定參數指定時，傳回停駐於停駐位置的窗格。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
在螢幕座標中的點, 供窗格抓取。

### <a name="return-value"></a>傳回值

位於指定點之窗格的指標, 如果指定的點上沒有任何窗格, 則為 Null。

### <a name="remarks"></a>備註

##  <a name="rectsidefrompoint"></a>CDockSite:: RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>參數

在*rect*<br/>

在*點*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="removepane"></a>CDockSite:: RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>參數

[in] *pWnd*<br/>

在*dockMethod*<br/>

### <a name="remarks"></a>備註

##  <a name="removerow"></a>CDockSite:: RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[in] *pRow*<br/>

### <a name="remarks"></a>備註

##  <a name="replacepane"></a>CDockSite:: ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>參數

在*pOldBar*<br/>

[in] *pNewBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="repositionpanes"></a>CDockSite:: RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>參數

[in] *rectNewClientArea*<br/>

### <a name="remarks"></a>備註

##  <a name="resizedocksite"></a>CDockSite:: ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>參數

[in] *nNewWidth*<br/>

[in] *nNewHeight*<br/>

### <a name="remarks"></a>備註

##  <a name="resizerow"></a>CDockSite:: ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>參數

[in] *pRow*<br/>

[in] *nNewSize*<br/>

在*bAdjustLayout*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="showpane"></a>CDockSite:: ShowPane

顯示窗格。

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[in、out]要顯示或隱藏之窗格的指標。

*bShow*<br/>
在TRUE 表示要顯示窗格;FALSE 指定要隱藏窗格。

*bDelay*<br/>
[in]若要指定，版面配置窗格應該會延遲到之後會顯示該窗格;，則為 TRUE否則為 FALSE。

*bActivate*<br/>
在不使用這個參數。

### <a name="return-value"></a>傳回值

如果已成功顯示或隱藏窗格, 則為 TRUE。 如果指定的窗格不屬於此停駐網站, 則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法, 以顯示或隱藏停駐的窗格。 一般來說, 您不需要直接呼叫`CDockSite::ShowPane` , 因為父框架視窗或基底窗格會呼叫它。

##  <a name="showrow"></a>CDockSite:: ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>參數

[in] *pRow*<br/>

在*bShow*<br/>

在*bAdjustLayout*<br/>

### <a name="remarks"></a>備註

##  <a name="swaprows"></a>CDockSite:: SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>參數

[in] *pFirstRow*<br/>

[in] *pSecondRow*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane 類別](../../mfc/reference/cbasepane-class.md)
