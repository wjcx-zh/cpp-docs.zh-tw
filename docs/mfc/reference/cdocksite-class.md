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
ms.openlocfilehash: 471d68ead1bc5a11ace29f572647c4a7f2406b4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753279"
---
# <a name="cdocksite-class"></a>CDockSite Class

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

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
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(覆蓋[CBasePane::調整停靠佈局](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(覆蓋[CBasePane::調整佈局](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(覆蓋[CBasePane::CalcFixed 佈局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(覆蓋[CBasePane::接受窗格](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(覆蓋[CBasePane:createEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(覆蓋[CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(覆蓋[CBasePane::DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(覆寫 `CBasePane::IsAccessibilityCompatible`。)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(覆蓋[CBasePane:可調整大小](../../mfc/reference/cbasepane-class.md#isresizable).|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|由給定參數指定時，傳回停駐於停駐位置的窗格。|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐於另一個窗格的左邊。|
|[CDockSite::查找PaneByID](#findpanebyid)|傳回給定識別碼所識別的窗格。|
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

當您調用`CDockSite`[CFramewndEx::啟用停靠](../../mfc/reference/cframewndex-class.md#enabledocking)時,框架會自動創建物件。 停駐位置視窗位於主框架視窗上用戶端區域的邊緣。

您通常不必調用銜接站網站提供的服務,因為[CFrameWndEx 類](../../mfc/reference/cframewndex-class.md)處理這些服務。

## <a name="example"></a>範例

下列範例示範如何建立 `CDockSite` 類別的物件。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目標](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>需求

**標題:** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDock 網站:新增行

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>參數

[在]*pos*<br/>

[在]*nHeight*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite::調整停靠佈局

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>備註

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite::調整佈局

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>備註

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDock網站:對齊Dock網站

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>參數

[在]*整流比*<br/>

[在]*rectResult*<br/>

[在]*b 立即移動*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDock網站::卡爾卡固定佈局

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

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDock網站::接受窗格

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDock 網站:建立Ex

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

[在]*dwStyleEx*<br/>

[在]*dwStyle*<br/>

[在]*rect*<br/>

[在]*pparentwnd*<br/>

[在]*dwControlBar 樣式*<br/>

[在]*pContext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDock 網站:建立行

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>參數

[在]*p 父塢列*<br/>

[在]*n位移*<br/>

[在]*n 羅高地*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

[在]*基方法*<br/>

[在]*lpRect*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>克多克網站::D奧克帕內左

將窗格停駐於另一個窗格的左邊。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>參數

*pBartodock*<br/>
[進出]指向要停靠在*pTargetBar*左側的窗格的指標。

*p 目標列*<br/>
[進出]指向目標窗格的指標。

### <a name="return-value"></a>傳回值

如果窗格已成功停靠,則為 TRUE;如果窗格已成功停靠。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsert之前

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockSite::查找PaneByID

返回具有給定 ID 的窗格。

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]要找到的窗格的命令 ID。

### <a name="return-value"></a>傳回值

指向具有指定命令 ID 的窗格的指標,如果未找到窗格,則指向 NULL。

### <a name="remarks"></a>備註

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDock網站:尋找羅索引

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[在]*pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite:修復虛擬Rects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>備註

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDockSite::取得DockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDock 網站:取得Dock網站清單

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDock 網站:抓取窗格清單

返回停靠在停靠網站中的窗格的清單。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>傳回值

對當前停靠欄中停靠的窗格列表的唯讀引用。

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite:可存取性相容

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite::是德拉格模式

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CDockSite:是最後一個

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>參數

[在]*pRow*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite:isrect在DockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

[在]*ptDelta*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite:可調整大小

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDock 網站:移動窗格

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

[在]*nFlags*<br/>

[在]*pt 位移*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite:插入器

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>參數

[在]*pos*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite::在刪除行

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>參數

[在]*pos*<br/>

[在]*bByShow*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite:在重新大小行上

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>參數

[在]*prowtoresize*<br/>

[在]*n位移*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite::在大小父

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>參數

[在]*重新提供*<br/>

[在]*n側*<br/>

[在]*b 延伸*<br/>

[在]*n位移*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDock 網站:開啟視窗Pos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

[在]*pWndInsert 後*<br/>

[在]*雷克溫德*<br/>

[在]*nFlags*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDock網站:在ShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>參數

[在]*pos*<br/>

[在]*b 顯示*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite::P從點

由給定參數指定時，傳回停駐於停駐位置的窗格。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
[在]要檢索的窗格的點,位於螢幕座標中。

### <a name="return-value"></a>傳回值

指向位於指定點的窗格的指標,或 NULL 的指標,如果指定點上不存在窗格。

### <a name="remarks"></a>備註

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite::從點

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

[在]*點*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDock 網站:移除窗格

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

[在]*基方法*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDock 網站:刪除行

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>參數

[在]*pRow*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite::取代窗格

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>參數

[在]*pOldBar*<br/>

[在]*pNewBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockSite::重新置放窗格

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>參數

[在]*rectNewClient區域*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDock 網站:調整Dock網站

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>參數

[在]*n 新寬度*<br/>

[在]*n 新高度*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite::調整大小

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>參數

[在]*pRow*<br/>

[在]*n 新尺寸*<br/>

[在]*b 調整佈局*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDock網站::顯示窗格

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
[進出]指向要顯示或隱藏的窗格的指標。

*b 顯示*<br/>
[在]TRUE 以指定要顯示的窗格;FALSE 以指定要隱藏的窗格。

*bDelay*<br/>
[在]TRUE 指定窗格的佈局應延遲到顯示窗格之後;否則,請將窗格的佈局延遲到否則,FALSE。

*b 啟動*<br/>
[在]不使用此參數。

### <a name="return-value"></a>傳回值

如果窗格已顯示或已成功隱藏,則為 TRUE。 如果指定的窗格不屬於此銜接站站點,則FALSE。

### <a name="remarks"></a>備註

呼叫此方法以顯示或隱藏停靠的窗格。 通常,您不必直接調用`CDockSite::ShowPane`,因為它由父框架視窗或基窗格調用。

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDock 網站:顯示行

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>參數

[在]*pRow*<br/>

[在]*b 顯示*<br/>

[在]*b 調整佈局*<br/>

### <a name="remarks"></a>備註

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDock網站::交換

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>參數

[在]*pFirstRow*<br/>

[在]*p 秒羅*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane 類別](../../mfc/reference/cbasepane-class.md)
