---
title: CMultiPaneFrameWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
ms.openlocfilehash: 047dd5ca2ca6705549e8f92de1550248e348ff52
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752798"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd 類別

該`CMultiPaneFrameWnd`類別延伸[CPaneFramewnd 類別](../../mfc/reference/cpaneframewnd-class.md)。 這可以支援多個窗格。 包含一個[CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md)`CMultiPaneFrameWnd`物件,該物件允許使用者將一個句柄停靠到`CMultiPaneFrameWnd`另一個,並動態創建多個浮動的選項卡式視窗,而不是控制件欄的單個嵌入句柄。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 多窗格框架::新增窗格](#addpane)|加入窗格。 (覆蓋[CPaneFramewnd::添加窗格](../../mfc/reference/cpaneframewnd-class.md#addpane).)|
|[C 多窗格框架::新增最新窗格](#addrecentpane)||
|[C 多窗格框架::調整佈局](#adjustlayout)|調整迷你框架視窗的配置。 (覆蓋[CPaneFramewnd::調整佈局](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|
|[C 多窗格框架::調整窗格框架](#adjustpaneframes)|(覆蓋[CPaneFramewnd:調整窗格幀](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes)。|
|[C 多窗格框架::鈣化物多克](#calcexpecteddockedrect)|計算停靠視窗的預期矩形。 (覆蓋[CPaneFramewnd::Calc預期多克已重新](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect)使用 .)|
|[C 多窗格框架::可附加](#canbeattached)|確定當前窗格是否可以停靠到另一個窗格或框架視窗。 (覆蓋[CPaneFramewnd::可以附加](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|
|[C 多窗格框架::可多克托帕](#canbedockedtopane)|確定微型框架視窗是否可以停靠到窗格。 (覆蓋[CPaneframewnd::可以裝對窗格](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|
|[C 多窗格框架::檢查夾持可見性](#checkgrippervisibility)|(覆蓋[CPaneFramewnd::檢查夾持可見度](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|
|[C 多窗格框架:關閉迷你框架](#closeminiframe)|(覆寫 `CPaneFrameWnd::CloseMiniFrame`。)|
|[C 多窗格框架::轉換到選項卡文件](#converttotabbeddocument)|將窗格轉換為索引標籤式文件。 (覆蓋[CPaneframewnd::轉換到 Tabbed 文檔](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|
|[C 多窗格框架::DockFrame](#dockframe)||
|[C 多窗格框架::Dockpane](#dockpane)|固定窗格。 (覆蓋[CPaneFramewnd::Dockpane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|
|[C 多窗格框架::D最近窗格到大型框架](#dockrecentpanetomainframe)||
|[C 多窗格框架::取得字幕文字](#getcaptiontext)|傳回標題文字。 (覆蓋[CPaneFramewnd:取得字幕文字](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|
|[C 多窗格框架::抓取窗格容器管理員](#getpanecontainermanager)|返回對內部容器管理員物件的引用。|
|[C 多窗格框架::取得第一個可見窗格](#getfirstvisiblepane)|傳回包含在迷你框架視窗中的第一個可見窗格。 (覆蓋[CPaneFramewnd:取得第一個可見窗格](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane)。)|
|[C 多窗格框架::取得窗格](#getpane)|傳回包含在迷你框架視窗中的窗格。 (覆蓋[CPaneFramewnd:getPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|
|[C 多窗格框架::取得窗格計數](#getpanecount)|傳回包含在迷你框架視窗中的窗格數目。 (覆蓋[CPaneFramewnd:取得窗格計數](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|
|[C 多窗格框架::取得可見窗格計數](#getvisiblepanecount)|傳回包含在迷你框架視窗中的可見窗格數目。 (覆蓋[CPaneFramewnd:取得可見窗格計數](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount)。|
|[C 多窗格框架::插入窗格](#insertpane)||
|[C 多窗格框架::載入狀態](#loadstate)|從登錄載入窗格的狀態。 (覆蓋[CPaneFramewnd::載入狀態](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|
|[C 多窗格框架::在多克到最新Pos](#ondocktorecentpos)|將迷你框架視窗固定在其最近的位置上。 (覆蓋[CPaneframewnd:ondock 到最新Pos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos). )|
|[C 多窗格框架::在基基爾羅普普計時器上](#onkillrolluptimer)|停止彙總計時器。 (覆蓋[CPaneframewnd::在 KillrollupTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer)上。|
|[C 多窗格框架::在窗格Recalc佈局上](#onpanerecalclayout)|調整小型框架視窗中窗格的佈局。 (覆蓋[CPaneFramewnd:onPaneRecalclayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|
|[C 多窗格框架::打開捲動計時器](#onsetrolluptimer)|設定彙總計時器。 (覆蓋[CPaneframewnd:onSetrolluptimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|
|[C 多窗格框架::在顯示窗格上](#onshowpane)|在隱藏或顯示迷你框架視窗中的窗格時，由架構呼叫。 (覆蓋[CPaneFramewnd:上顯示窗格](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|
|[C 多窗格框架::P從點](#panefrompoint)|如果在迷你框架視窗內包含使用者提供的點，則會傳回一個窗格。 (覆蓋[CPaneFramewnd::P從點](../../mfc/reference/cpaneframewnd-class.md#panefrompoint). )|
|[C 多窗格框架::刪除非有效窗格](#removenonvalidpanes)|由架構呼叫以移除無效窗格。 (覆蓋[CPaneFramewnd::刪除 NonValidPane.)](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes)|
|[C 多窗格框架::刪除窗格](#removepane)|從迷你框架視窗中移除窗格。 (覆蓋[CPaneFramewnd::刪除窗格](../../mfc/reference/cpaneframewnd-class.md#removepane).)|
|[C 多窗格框架::取代窗格](#replacepane)|以一個窗格取代另一個。 (覆蓋[CPaneFramewnd::取代窗格](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|
|[C 多窗格框架::儲存狀態](#savestate)|將窗格的狀態儲存至登錄。 (覆蓋[CPaneFramewnd::保存狀態](../../mfc/reference/cpaneframewnd-class.md#savestate).)|
|[C 多窗格框架::序列化](#serialize)|(覆寫 `CPaneFrameWnd::Serialize`。)|
|[C 多窗格框架::SetDockstate](#setdockstate)|設定固定狀態。 (覆蓋[CPaneFramewnd:setDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|
|[C 多窗格框架::設定最後聚焦窗格](#setlastfocusedpane)||
|[C 多窗格框架::設置前塢州](#setpredockstate)|設置預停靠狀態。 (覆蓋[CPaneFramewnd:設定 PreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|
|[C 多窗格框架::儲存最新網站資訊](#storerecentdocksiteinfo)|(覆蓋[CPaneFramewnd::存儲最近網站網站資訊](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|
|[C 多窗格框架::儲存最新標籤相關資訊](#storerecenttabrelatedinfo)|(覆蓋[CPaneFramewnd::存儲最近標籤相關資訊](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|

## <a name="remarks"></a>備註

此類中的大多數方法重寫[CPaneFrameWnd 類](../../mfc/reference/cpaneframewnd-class.md)中的方法。

如果窗格使用AFX_CBRS_AUTO_ROLLUP樣式,並且使用者將該窗格停靠到多窗格框架視窗,則無論其他停靠窗格的樣式設置如何,使用者都可以向上滾動視窗。

當使用者浮動使用CBRS_FLOAT_MULTI樣式`CMultiPaneFrameWnd`的窗格時,框架會自動創建一個物件。

有關從`CPaneFrameWnd`類派生類並動態創建類的資訊,請參閱[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。

## <a name="example"></a>範例

下面的示例演示如何檢索指向`CMultiPaneFrameWnd`物件的指標。 此程式碼段是[「設定窗格大小」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>需求

**標題:** afx 多窗格框架.h

## <a name="cmultipaneframewndaddpane"></a><a name="addpane"></a>C 多窗格框架::新增窗格

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndaddrecentpane"></a><a name="addrecentpane"></a>C 多窗格框架::新增最新窗格

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndadjustlayout"></a><a name="adjustlayout"></a>C 多窗格框架::調整佈局

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>C 多窗格框架::調整窗格框架

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>C 多窗格框架::鈣化物多克

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>參數

[在]*普恩德托多克*<br/>
[在]*ptMouse*<br/>
[在]*rectResult*<br/>
[在]*bDrawTab*<br/>
[在]*ppTargetBar*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndcanbeattached"></a><a name="canbeattached"></a>C 多窗格框架::可附加

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>C 多窗格框架::可多克托帕

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>參數

[在]*pDockingBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>C 多窗格框架::檢查夾持可見性

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndcloseminiframe"></a><a name="closeminiframe"></a>C 多窗格框架:關閉迷你框架

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>C 多窗格框架::轉換到選項卡文件

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewnddockframe"></a><a name="dockframe"></a>C 多窗格框架::DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>參數

[在]*pDocked 框架*<br/>
[在]*基方法*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewnddockpane"></a><a name="dockpane"></a>C 多窗格框架::Dockpane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>參數

[在]*pDockedBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewnddockrecentpanetomainframe"></a><a name="dockrecentpanetomainframe"></a>C 多窗格框架::D最近窗格到大型框架

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>C 多窗格框架::取得字幕文字

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>C 多窗格框架::取得第一個可見窗格

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndgetpane"></a><a name="getpane"></a>C 多窗格框架::取得窗格

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndgetpanecontainermanager"></a><a name="getpanecontainermanager"></a>C 多窗格框架::抓取窗格容器管理員

返回對內部容器管理員物件的引用。

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>傳回值

對內部容器管理員物件的引用。

### <a name="remarks"></a>備註

此方法可用於訪問內部[CPane 容器管理員類別](../../mfc/reference/cpanecontainermanager-class.md)。

## <a name="cmultipaneframewndgetpanecount"></a><a name="getpanecount"></a>C 多窗格框架::取得窗格計數

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>C 多窗格框架::取得可見窗格計數

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndinsertpane"></a><a name="insertpane"></a>C 多窗格框架::插入窗格

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>參數

[在]*p控制列*<br/>
[在]*p 目標*<br/>
[在]*b 後*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndloadstate"></a><a name="loadstate"></a>C 多窗格框架::載入狀態

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

[在]*lpsz 設定檔名稱*<br/>
[在]*uiID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>C 多窗格框架::在多克到最新Pos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>C 多窗格框架::在基基爾羅普普計時器上

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>C 多窗格框架::在窗格Recalc佈局上

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>C 多窗格框架::打開捲動計時器

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndonshowpane"></a><a name="onshowpane"></a>C 多窗格框架::在顯示窗格上

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>
[在]*b 顯示*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndpanefrompoint"></a><a name="panefrompoint"></a>C 多窗格框架::P從點

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>參數

[在]*點*<br/>
[在]*nSensitivity*<br/>
[在]*b 檢查可見度*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>C 多窗格框架::刪除非有效窗格

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndremovepane"></a><a name="removepane"></a>C 多窗格框架::刪除窗格

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>
[在]*b破壞*<br/>
[在]*b 無延遲銷毀*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndreplacepane"></a><a name="replacepane"></a>C 多窗格框架::取代窗格

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>參數

[在]*pBarOrg*<br/>
[在]*pbar 取代與*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndsavestate"></a><a name="savestate"></a>C 多窗格框架::儲存狀態

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

[在]*lpsz 設定檔名稱*<br/>
[在]*uiID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndserialize"></a><a name="serialize"></a>C 多窗格框架::序列化

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

[在]*阿爾*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndsetdockstate"></a><a name="setdockstate"></a>C 多窗格框架::SetDockstate

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>參數

[在]*pDock 管理員*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndsetlastfocusedpane"></a><a name="setlastfocusedpane"></a>C 多窗格框架::設定最後聚焦窗格

```cpp
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>參數

[在]*霍恩德*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndsetpredockstate"></a><a name="setpredockstate"></a>C 多窗格框架::設置前塢州

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>參數

[在]*前DockState*<br/>
[在]*pBartodock*<br/>
[在]*基方法*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>C 多窗格框架::儲存最新網站資訊

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="cmultipaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>C 多窗格框架::儲存最新標籤相關資訊

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>參數

[在]*pDockingBar*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)
