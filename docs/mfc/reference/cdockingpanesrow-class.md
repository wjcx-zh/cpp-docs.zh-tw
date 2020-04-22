---
title: CDockingPanesRow 類別
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: d7535ae6c5246a372fd1a48573716bb166991d4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753307"
---
# <a name="cdockingpanesrow-class"></a>CDockingPanesRow 類別

管理與停駐位置位於相同水平或垂直列 (欄) 之窗格的清單。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDocking 窗格列::排列窗格](#arrangepanes)|根據指定的邊界和間距參數排列資料列中的窗格。|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Create](#create)||
|[CDockingPanesRow::ExpandStretchedPanes](#expandstretchedpanes)||
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||
|[CDockingPanesRow::GetClientRect](#getclientrect)||
|[CDockingPanesRow::GetDockSite](#getdocksite)||
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||
|[CDockingPanesRow::GetID](#getid)||
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanesRow::GetPaneList](#getpanelist)||
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||
|[CDockingPanesRow::GetRowHeight](#getrowheight)||
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||
|[CDockingPanesRow::IsVisible](#isvisible)||
|[CDockingPanesRow::Move](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::RedrawAll](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Resize](#resize)||
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>備註

`CDockingPanesRow` 物件會由固定站台物件在內部建立。

## <a name="example"></a>範例

下列範例示範如何從 `CMFCAutoHideBar` 物件取得 `CDockingPanesRow` 物件。

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>需求

**標題:** afxDockingPanesRow.h

## <a name="cdockingpanesrowaddpane"></a><a name="addpane"></a>CDockingPaneRow::添加窗格

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

[在]*基方法*<br/>

[在]*lpRect*<br/>

[在]*bAddLast*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowaddpanefromrow"></a><a name="addpanefromrow"></a>CDockingPanerow::從行添加窗格

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

[在]*基方法*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowarrangepanes"></a><a name="arrangepanes"></a>CDocking 窗格列::排列窗格

根據指定的邊距和間距參數排列列中的停靠窗格。

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>參數

*nMargin*<br/>
[在]從該行的左上角指定第一個窗格的偏移量(以像素為單位)。

*N間距*<br/>
[在]指定窗格之間的間距(以像素為單位)。

### <a name="remarks"></a>備註

調用此方法以排列行中的窗格,這些窗格將停靠在該行中。 呼叫此方法後,必須呼叫`CDockingPanesRow::FixupVirtualRects(FALSE, NULL)`。

## <a name="cdockingpanesrowcalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockingPanesRow::鈣固定佈局

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

## <a name="cdockingpanesrowcdockingpanesrow"></a><a name="cdockingpanesrow"></a>CDocking 窗格行::CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>參數

[在]*p 父塢列*<br/>

[在]*n位移*<br/>

[在]*nHeight*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowcreate"></a><a name="create"></a>CDocking 窗格行::建立

```
virtual BOOL Create();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowexpandstretchedpanes"></a><a name="expandstretchedpanes"></a>CDocking 窗格行::展開拉伸窗格

```cpp
void ExpandStretchedPanes();
```

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowexpandstretchedpanesrect"></a><a name="expandstretchedpanesrect"></a>CDocking 窗格行::展開拉伸窗格 Rect

```cpp
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingPanesRow:修復虛擬重新

```cpp
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>參數

[在]*b 移至虛擬rect*<br/>

[在]*pBarto 排除*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetavailablelength"></a><a name="getavailablelength"></a>CDockingPanerow::獲取可用長度

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>參數

[在]*bUse 虛擬重新*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetavailablespace"></a><a name="getavailablespace"></a>CDockingPanerow:獲取可用空間

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetclientrect"></a><a name="getclientrect"></a>CDockingPanerow::獲取客戶

```cpp
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetdocksite"></a><a name="getdocksite"></a>CDockingPanerow::獲取DockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetextraspace"></a><a name="getextraspace"></a>CDockingPanerow:獲取額外空間

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetgroupfrompane"></a><a name="getgroupfrompane"></a>CDockingPanerow:從窗格獲取群組

```cpp
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

[在]*奧斯特*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetid"></a><a name="getid"></a>CDockingPanesRow:GetID

```
int GetID() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetmaxpanesize"></a><a name="getmaxpanesize"></a>CDocking 窗格行::取得最大窗格大小

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>參數

[在]*b 跳過隱藏列*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetpanecount"></a><a name="getpanecount"></a>CDockingPanerow::獲取窗格計數

```
int GetPaneCount() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetpanelist"></a><a name="getpanelist"></a>CDockingPanerow::獲取窗格清單

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetrowalignment"></a><a name="getrowalignment"></a>CDockingPanesRow::獲取行調

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetrowheight"></a><a name="getrowheight"></a>CDockingPanesRow::獲取羅高

```
int GetRowHeight() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetrowoffset"></a><a name="getrowoffset"></a>CDockingPanesRow::獲取羅比

```
int GetRowOffset() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetvisiblecount"></a><a name="getvisiblecount"></a>CDockingPanesRow::獲取可見計數

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowgetwindowrect"></a><a name="getwindowrect"></a>CDockingPanesRow::取得視窗重新

```cpp
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowhaspane"></a><a name="haspane"></a>CDockingPanerow::哈斯帕內

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowisempty"></a><a name="isempty"></a>CDockingPanerow::空

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowisexclusiverow"></a><a name="isexclusiverow"></a>CDockingPanesRow:是排他性的

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowishorizontal"></a><a name="ishorizontal"></a>CDockingPanerow::是水準的

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowisvisible"></a><a name="isvisible"></a>CDockingPanesRow:可明顯

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowmove"></a><a name="move"></a>CDockingPanesRow::移動

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>參數

[在]*n位移*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowmovepane"></a><a name="movepane"></a>CDockingPaneRow::移動窗格

```cpp
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

[在]*pt 位移*<br/>

[在]*bSwap 控制列*<br/>

[在]*hdwp*<br/>

[在]*rectTarget*<br/>

[在]*n位移*<br/>

[在]*b 前進*<br/>

[在]*nAbsolut位移*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowonresizepane"></a><a name="onresizepane"></a>CDocking 窗格行::在重新調整窗格上

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowredrawall"></a><a name="redrawall"></a>CDockingPanerow::重新繪製所有

```cpp
void RedrawAll();
```

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowremovepane"></a><a name="removepane"></a>CDocking 窗格行::刪除窗格

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowreplacepane"></a><a name="replacepane"></a>CDocking 窗格行::取代窗格

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>參數

[在]*普巴爾Old*<br/>

[在]*pBar New*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowrepositionpanes"></a><a name="repositionpanes"></a>CDocking 窗格行::重新置放窗格

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>參數

[在]*重新家長欄區域*<br/>

[在]*n側*<br/>

[在]*b 延伸*<br/>

[在]*n位移*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowresize"></a><a name="resize"></a>CDockingPanerow::調整大小

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>參數

[在]*n位移*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowresizebypanedivider"></a><a name="resizebypanedivider"></a>CDockingPanerow::調整大小,由窗格轉換器

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>參數

[在]*忽略*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowscreentoclient"></a><a name="screentoclient"></a>CDockingPanerow::螢幕到用戶端

```cpp
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowsetextra"></a><a name="setextra"></a>CDockingPanerow::設置額外

```cpp
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>參數

[在]*n 額外空間*<br/>

[在]*列額外對齊*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowshowdocksiterow"></a><a name="showdocksiterow"></a>CDockingPanesRow::顯示DockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>參數

[在]*b 顯示*<br/>

[在]*bDelay*<br/>

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowshowpane"></a><a name="showpane"></a>CDocking 窗格行::顯示窗格

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>

[在]*b 顯示*<br/>

[在]*bDelay*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockingpanesrowupdatevisiblestate"></a><a name="updatevisiblestate"></a>CDockingPanesRow::更新可見狀態

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>參數

[在]*bDelay*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
