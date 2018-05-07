---
title: CDockSite 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a374496c731e33d13de3ece893fe2ff046d38e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdocksite-class"></a>CDockSite Class
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
 架構會建立`CDockSite`自動物件，當您呼叫[cframewndex:: Enabledocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 停駐位置視窗位於主框架視窗上用戶端區域的邊緣。  
  
 您通常不必呼叫停駐因為提供的服務[CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)會處理這些服務。  
  
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
 [輸入] `pos`  
 [輸入] `nHeight`  
  
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
 [輸入] `rectToAlignBy`  
 [輸入] `rectResult`  
 [輸入] `bMoveImmediately`  
  
### <a name="remarks"></a>備註  
  
##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bStretch`  
 [輸入] `bHorz`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane  

  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
  
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
 [輸入] `dwStyleEx`  
 [輸入] `dwStyle`  
 [輸入] `rect`  
 [輸入] `pParentWnd`  
 [輸入] `dwControlBarStyle`  
 [輸入] `pContext`  
  
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
 [輸入] `pParentDockBar`  
 [輸入] `nOffset`  
 [輸入] `nRowHeight`  
  
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
 [輸入] `pWnd`  
 [輸入] `dockMethod`  
 [輸入] `lpRect`  
  
### <a name="remarks"></a>備註  
  
##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf  
 將窗格停駐於另一個窗格的左邊。  
  
```  
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pBarToDock`  
 要左邊的停駐窗格的指標`pTargetBar`。  
  
 [in][out] `pTargetBar`  
 [目標] 窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 停駐窗格，否則， `FALSE`。  
  
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
 [輸入] `nID`  
 要尋找窗格的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 使用指定的命令 ID，窗格的指標或`NULL`如果找不到的窗格。  
  
### <a name="remarks"></a>備註  
  
##  <a name="findrowindex"></a>  CDockSite::FindRowIndex  

  
```  
int FindRowIndex(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRow`  
  
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
 傳回停駐在停駐位置的窗格的清單。  
  
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
 [輸入] `pRow`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite  

  
```  
BOOL IsRectWithinDockSite(
    CRect rect,  
    CPoint& ptDelta);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rect`  
 [輸入] `ptDelta`  
  
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
 [輸入] `pWnd`  
 [輸入] `nFlags`  
 [輸入] `ptOffset`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow  

  
```  
virtual void OnInsertRow(POSITION pos);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pos`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow  

  
```  
virtual void OnRemoveRow(
    POSITION pos,  
    BOOL bByShow = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pos`  
 [輸入] `bByShow`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onresizerow"></a>  CDockSite::OnResizeRow  

  
```  
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,  
    int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRowToResize`  
 [輸入] `nOffset`  
  
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
 [輸入] `rectAvailable`  
 [輸入] `nSide`  
 [輸入] `bExpand`  
 [輸入] `nOffset`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos  

  
```  
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,  
    const CRect& rectWnd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndInsertAfter`  
 [輸入] `rectWnd`  
 [輸入] `nFlags`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onshowrow"></a>  CDockSite::OnShowRow  

  
```  
virtual void OnShowRow(
    POSITION pos,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pos`  
 [輸入] `bShow`  
  
### <a name="remarks"></a>備註  
  
##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint  
 由給定參數指定時，傳回停駐於停駐位置的窗格。  
  
```  
virtual CPane* PaneFromPoint(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pt`  
 要擷取之窗格的螢幕座標中的點。  
  
### <a name="return-value"></a>傳回值  
 位於指定點的窗格的指標或`NULL`如果沒有窗格已存在於指定的點。  
  
### <a name="remarks"></a>備註  
  
##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint  

  
```  
static int __stdcall RectSideFromPoint(
    const CRect& rect,  
    const CPoint& point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rect`  
 [輸入] `point`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="removepane"></a>  CDockSite::RemovePane  

  
```  
virtual void RemovePane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 [輸入] `dockMethod`  
  
### <a name="remarks"></a>備註  
  
##  <a name="removerow"></a>  CDockSite::RemoveRow  

  
```  
void RemoveRow(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRow`  
  
### <a name="remarks"></a>備註  
  
##  <a name="replacepane"></a>  CDockSite::ReplacePane  

  
```  
BOOL ReplacePane(
    CPane* pOldBar,  
    CPane* pNewBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pOldBar`  
 [輸入] `pNewBar`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes  

  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rectNewClientArea`  
  
### <a name="remarks"></a>備註  
  
##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite  

  
```  
void ResizeDockSite(
    int nNewWidth,  
    int nNewHeight);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nNewWidth`  
 [輸入] `nNewHeight`  
  
### <a name="remarks"></a>備註  
  
##  <a name="resizerow"></a>  CDockSite::ResizeRow  

  
```  
int ResizeRow(
    CDockingPanesRow* pRow,  
    int nNewSize,  
    BOOL bAdjustLayout = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRow`  
 [輸入] `nNewSize`  
 [輸入] `bAdjustLayout`  
  
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
 [in][out] `pBar`  
 顯示或隱藏窗格指標。  
  
 [輸入] `bShow`  
 `TRUE` 若要指定窗格會顯示;`FALSE`指定窗格為隱藏。  
  
 [輸入] `bDelay`  
 `TRUE` 若要指定窗格的配置，應延遲窗格之後，才會顯示。否則， `FALSE`。  
  
 [輸入] `bActivate`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果窗格已顯示或隱藏成功。 `FALSE` 如果指定的窗格不屬於此停駐位置。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以顯示或隱藏停駐的窗格。 一般來說，您不需要呼叫`CDockSite::ShowPane`直接管理，因為它會呼叫父框架視窗或基底的窗格。  
  
##  <a name="showrow"></a>  CDockSite::ShowRow  

  
```  
void ShowRow(
    CDockingPanesRow* pRow,  
    BOOL bShow,  
    BOOL bAdjustLayout);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRow`  
 [輸入] `bShow`  
 [輸入] `bAdjustLayout`  
  
### <a name="remarks"></a>備註  
  
##  <a name="swaprows"></a>  CDockSite::SwapRows  

  
```  
void SwapRows(
    CDockingPanesRow* pFirstRow,  
    CDockingPanesRow* pSecondRow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pFirstRow`  
 [輸入] `pSecondRow`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBasePane 類別](../../mfc/reference/cbasepane-class.md)
