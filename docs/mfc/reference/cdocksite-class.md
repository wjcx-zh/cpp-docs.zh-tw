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
ms.openlocfilehash: 08acf9e47a26d4cbc5bcb96cbff086b19768e972
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486303"
---
# <a name="cdocksite-class"></a>CDockSite Class

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

提供可將衍生自 [CPane Class](../../mfc/reference/cpane-class.md) 的窗格排列成資料列集合的功能。

## <a name="syntax"></a>語法

```
class CDockSite: public CBasePane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(覆寫[cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)。)|
|[CDockSite::AdjustLayout](#adjustlayout)|(覆寫[cbasepane:: Adjustlayout](../../mfc/reference/cbasepane-class.md#adjustlayout)。)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(覆寫[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(覆寫[cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)。)|
|[CDockSite::CreateEx](#createex)|(覆寫[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(覆寫[cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#dockpane)。)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(覆寫[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(覆寫 `CBasePane::IsAccessibilityCompatible`。)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(覆寫[cbasepane:: Isresizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|
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

此架構會建立`CDockSite`當您呼叫自動物件[cframewndex:: Enabledocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 停駐位置視窗位於主框架視窗上用戶端區域的邊緣。

您通常不必呼叫停駐位置提供，因為服務[CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)會處理這些服務。

## <a name="example"></a>範例

下列範例示範如何建立 `CDockSite` 類別的物件。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>需求

**標頭：** afxDockSite.h

##  <a name="addrow"></a>  CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>參數

[in]*pos*<br/>

[in]*nHeight*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>備註

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>備註

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>參數

[in]*rectToAlignBy*<br/>

[in]*rectResult*<br/>

[in]*bMoveImmediately*<br/>

### <a name="remarks"></a>備註

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[in]*bStretch*<br/>

[in]*bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

[in]*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createex"></a>  CDockSite::CreateEx

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

[in]*dwStyleEx*<br/>

[in]*cheaderctrl:: Create*<br/>

[in]*rect*<br/>

[in]*pParentWnd*<br/>

[in]*dwControlBarStyle*<br/>

[in]*pContext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createrow"></a>  CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>參數

[in]*pParentDockBar*<br/>

[in]*nOffset*<br/>

[in]*nRowHeight*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="dockpane"></a>  CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

[in]*pWnd*<br/>

[in]*dockMethod*<br/>

[in]*lpRect*<br/>

### <a name="remarks"></a>備註

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

將窗格停駐於另一個窗格的左邊。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>參數

*pBarToDock*<br/>
[in、 out]左邊的停駐窗格的指標*pTargetBar*。

*pTargetBar*<br/>
[in、 out]對 [目標] 窗格的指標。

### <a name="return-value"></a>傳回值

如果已成功; 停駐窗格中，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID

傳回具有指定 ID 的窗格

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
[in]要尋找窗格的命令識別碼。

### <a name="return-value"></a>傳回值

窗格中，使用指定的命令 ID 或如果找不到 [] 窗格中，則為 NULL 指標。

### <a name="remarks"></a>備註

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[in]*pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>備註

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

傳回一份停駐在停駐位置的窗格。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>傳回值

窗格的清單的唯讀參考目前停駐在停駐列中。

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isdragmode"></a>  CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="islastrow"></a>  CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>參數

[in]*pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>參數

[in]*rect*<br/>

[in]*ptDelta*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isresizable"></a>  CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="movepane"></a>  CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>參數

[in]*pWnd*<br/>

[in]*nFlags*<br/>

[in]*ptOffset*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>參數

[in]*pos*<br/>

### <a name="remarks"></a>備註

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>參數

[in]*pos*<br/>

[in]*bByShow*<br/>

### <a name="remarks"></a>備註

##  <a name="onresizerow"></a>  CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>參數

[in]*pRowToResize*<br/>

[in]*nOffset*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>參數

[in]*rectAvailable*<br/>

[in]*nSide*<br/>

[in]*bExpand*<br/>

[in]*nOffset*<br/>

### <a name="remarks"></a>備註

##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

[in]*pWndInsertAfter*<br/>

[in]*rectWnd*<br/>

[in]*nFlags*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onshowrow"></a>  CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>參數

[in]*pos*<br/>

[in]*bShow*<br/>

### <a name="remarks"></a>備註

##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint

由給定參數指定時，傳回停駐於停駐位置的窗格。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
[in]中的 [擷取] 窗格的螢幕座標的點。

### <a name="return-value"></a>傳回值

指向 [] 窗格中位於指定的點，或如果沒有窗格已存在於指定的點，則為 NULL。

### <a name="remarks"></a>備註

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>參數

[in]*rect*<br/>

[in]*點*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="removepane"></a>  CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>參數

[in]*pWnd*<br/>

[in]*dockMethod*<br/>

### <a name="remarks"></a>備註

##  <a name="removerow"></a>  CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[in]*pRow*<br/>

### <a name="remarks"></a>備註

##  <a name="replacepane"></a>  CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>參數

[in]*pOldBar*<br/>

[in]*pNewBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>參數

[in]*rectNewClientArea*<br/>

### <a name="remarks"></a>備註

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>參數

[in]*nNewWidth*<br/>

[in]*nNewHeight*<br/>

### <a name="remarks"></a>備註

##  <a name="resizerow"></a>  CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>參數

[in]*pRow*<br/>

[in]*nNewSize*<br/>

[in]*bAdjustLayout*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="showpane"></a>  CDockSite::ShowPane

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
[in、 out]指標，要顯示或隱藏窗格。

*bShow*<br/>
[in]TRUE 表示指定的窗格是顯示;如果為 false，則指定要隱藏窗格。

*bDelay*<br/>
[in]若要指定，版面配置 窗格應該會延遲到之後會顯示該窗格;，則為 TRUE否則為 FALSE。

*bActivate*<br/>
[in]未使用此參數。

### <a name="return-value"></a>傳回值

如果窗格已顯示或隱藏成功，則為 TRUE。 如果指定的窗格不屬於此停駐站台，則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法來顯示或隱藏停駐的窗格。 一般來說，您就不必呼叫`CDockSite::ShowPane`直接，因為它會呼叫父框架視窗或 [基本] 窗格。

##  <a name="showrow"></a>  CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>參數

[in]*pRow*<br/>

[in]*bShow*<br/>

[in]*bAdjustLayout*<br/>

### <a name="remarks"></a>備註

##  <a name="swaprows"></a>  CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>參數

[in]*pFirstRow*<br/>

[in]*pSecondRow*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane 類別](../../mfc/reference/cbasepane-class.md)
