---
title: CDockingManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
dev_langs:
- C++
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5dad441d2aa997a3e32d53f07683877442100a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdockingmanager-class"></a>CDockingManager 類別
實作控制配置停駐於主框架視窗中的核心功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CDockingManager : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](#adddocksite)|建立停駐窗格，並將它加入至控制列清單。|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|將控制代碼加入至列窗格，即可隱藏 MDI 索引標籤式窗格列的清單。|  
|[CDockingManager::AddMiniFrame](#addminiframe)|將框架加入迷你框架的清單。|  
|[CDockingManager::AddPane](#addpane)|使用停駐的管理員，註冊一個窗格。|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|重新計算，並調整框架視窗中的所有窗格的配置。|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|會導致`WM_NCCALCSIZE`訊息傳送至所有窗格和`CPaneFrameWnd`windows。|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|調整矩形的對齊方式。|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|調整大小，以自動隱藏模式中的停駐窗格所花費的整個寬度或高度的畫面格的工作區，以停駐的站台。|  
|[CDockingManager::AutoHidePane](#autohidepane)|建立自動隱藏工具列。|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|將有指定的對齊上方停駐的列。|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|將功能表中的停駐窗格和工具列的名稱。|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|計算預期的固定視窗矩形。|  
|[CDockingManager::Create](#create)|建立停駐的管理員。|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|決定包含指定的點和其銜接狀態的窗格。|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|啟用或停用停駐配置從登錄載入。|  
|[CDockingManager::DockPane](#dockpane)|另一個窗格或框架視窗停駐窗格。|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐於另一個窗格的左邊。|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|可讓主框架窗格的停駐、 建立停駐窗格中，並將它加入至控制列清單。|  
|[CDockingManager::EnableDocking](#enabledocking)|建立停駐窗格並啟用停駐窗格的主要畫面格。|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|顯示其他按鈕會開啟快顯功能表上的所有停駐窗格的標題。|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|告知要顯示一個特殊的內容功能表，使用者按一下滑鼠按鈕和程式庫會處理 WM_CONTEXTMENU 訊息時，有一份應用程式工具列和停駐窗格的程式庫。|  
|[CDockingManager::FindDockSite](#finddocksite)|擷取列窗格中，位於指定位置，且具有指定的對齊方式。|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|傳回列 id 為目標窗格的窗格。|  
|[CDockingManager::FindPaneByID](#findpanebyid)|尋找窗格中所指定的控制項 id。|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|認可所有目前工具列位置虛擬矩形。|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|傳回包含指定的點的框架。|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|取得包含界限的用戶端區域的矩形。|  
|[CDockingManager::GetDockingMode](#getdockingmode)|傳回目前的停駐模式。|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|取得父視窗框架指標。|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|傳回已啟用的對齊方式的窗格。|  
|[CDockingManager::GetMiniFrames](#getminiframes)|取得主機的清單。|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|取得包含外部的框架邊緣的矩形。|  
|[CDockingManager::GetPaneList](#getpanelist)|傳回屬於停駐的管理員窗格的清單。 這包括所有浮動窗格。|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|擷取智慧停駐的管理員的指標。|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|擷取智慧停駐的管理員的指標。|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|智慧停駐參數傳回停駐的管理員。|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|傳回用來顯示智慧停駐標記的佈景主題的靜態方法。|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|隱藏自動隱藏模式中的窗格。|  
|[CDockingManager::InsertDockSite](#insertdocksite)|建立停駐窗格，並將它插入控制列清單。|  
|[CDockingManager::InsertPane](#insertpane)|控制項窗格插入控制列清單。|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|指定是否顯示快顯功能表上的所有窗格的標題。|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|決定所有窗格的配置會進行調整。|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|指定是否停駐的管理員為 OLE 容器模式。|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|判斷指定的點是否停駐位置附近。|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|決定是否預覽列印模式設定。|  
|[CDockingManager::LoadState](#loadstate)|從登錄載入停駐的管理員狀態。|  
|[CDockingManager::LockUpdate](#lockupdate)|鎖定指定的視窗。|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|框架視窗變成使用中或已停用時由架構呼叫。|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|由架構呼叫以移動迷你框架視窗。|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|建置已窗格的清單功能表時由架構呼叫。|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|傳回包含指定的點的窗格。|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|由架構呼叫來選取或清除核取方塊，針對指定的命令，並重新計算顯示窗格的配置。|  
|[CDockingManager::RecalcLayout](#recalclayout)|重新計算存在的控制項清單中的控制項的內部配置。|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|釋出空白窗格容器。|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|移除指定的隱藏窗格列。|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|從迷你框架的清單中移除指定的範圍。|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|取消登錄 窗格，並從停駐的管理員在清單中移除。|  
|[CDockingManager::ReplacePane](#replacepane)|以一個窗格取代另一個。|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|訴諸的迷你框架清單中的框架。|  
|[CDockingManager::SaveState](#savestate)|將停駐的管理員狀態儲存至登錄。|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|將指定的訊息傳送至所有的迷你框架。|  
|[CDockingManager::Serialize](#serialize)|寫入封存停駐的管理員。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|設定大小、 寬度和高度的控制列和指定的窗格。|  
|[CDockingManager::SetDockingMode](#setdockingmode)|設定固定的模式。|  
|[CDockingManager::SetDockState](#setdockstate)|設定停駐控制列、 迷你框架和自動隱藏列的狀態。|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|設定會顯示在預覽列印中的長條的預覽列印模式。|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|設定定義智慧停駐行為的參數。|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|顯示或隱藏的迷你框架視窗。|  
|[CDockingManager::ShowPanes](#showpanes)|顯示或隱藏控制項，並自動隱藏列的窗格。|  
|[CDockingManager::StartSDocking](#startsdocking)|啟動指定的視窗智慧停駐的管理員的對齊方式根據智慧停駐。|  
|[CDockingManager::StopSDocking](#stopsdocking)|停駐點智慧停駐。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|指定是否停駐的管理員隱藏 OLE 容器模式中的窗格。|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|指定全域的停駐模式。|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|指定的停駐的敏感度。|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|指定時間，以毫秒為單位，才能停駐窗格停駐在停駐的即時模式中。|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|指定時間，以毫秒為單位，工具列停駐於主框架視窗之前。|  
  
## <a name="remarks"></a>備註  
 主框架視窗建立，並自動初始化這個類別。  
  
 停駐的管理員物件保留一份所有窗格中的停駐的配置，以及一份所有[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)隸屬於主框架視窗的視窗。  
  
 `CDockingManager`類別會實作某些服務可讓您尋找窗格或`CPaneFrameWnd`視窗。 您通常不這些服務會直接呼叫因為它們會包裝在主框架視窗物件。 如需詳細資訊，請參閱[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)。  
  
## <a name="customization-tips"></a>自訂秘訣  
 下列秘訣適用於`CDockingManager`物件：  
  
- [CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)支援這些停駐模式：  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     這些停駐模式由定義[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)並且由呼叫設定[CDockingManager::SetDockingMode](#setdockingmode)。  
  
-   如果您想要建立非浮動、 非可調整大小的窗格，呼叫[CDockingManager::AddPane](#addpane)方法。 這個方法會使用停駐的管理員會負責窗格配置註冊窗格。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CDockingManager`用來設定類別`CDockingManager`物件。 此範例示範如何顯示額外的按鈕會開啟快顯功能表上的所有停駐窗格的標題，以及如何設定物件的固定模式。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxDockingManager.h  
  
##  <a name="adddocksite"></a>  CDockingManager::AddDockSite  
 建立停駐窗格，並將它加入至控制列清單。  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `info`  
 資訊結構，其中包含的參考將停駐窗格的對齊方式。  
  
 [輸出] `ppDockBar`  
 指向新的停駐窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 建立停駐窗格`FALSE`否則。  
  
##  <a name="addhiddenmditabbedbar"></a>  CDockingManager::AddHiddenMDITabbedBar  
 將控制代碼加入至列窗格，即可隱藏 MDI 索引標籤式窗格列的清單。  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 列的指標窗格  
  
##  <a name="addpane"></a>  CDockingManager::AddPane  
 使用停駐的管理員，註冊一個窗格。  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `pWnd`  
 指定將新增到停駐的管理員 窗格。  
  
 [輸入] `bTail`  
 `TRUE` 若要窗格的清單結尾加入窗格，停駐的管理員。否則， `FALSE`。  
  
 [輸入] `bAutoHide`  
 僅供內部使用。 永遠都會使用預設值`FALSE`。  
  
 [輸入] `bInsertForOuterEdge`  
 僅供內部使用。 永遠都會使用預設值`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果窗格已成功向停駐的管理員。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以非浮動、 非可調整大小的窗格向停駐的管理員。 如果您不要註冊窗格中，將無法正確顯示停駐的管理員已配置版面。  
  
##  <a name="adjustdockinglayout"></a>  CDockingManager::AdjustDockingLayout  
 重新計算，並調整框架視窗中的所有窗格的配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `hdwp`  
 指定延後的視窗位置結構。 如需詳細資訊，請參閱 [Windows 資料類型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addminiframe"></a>  CDockingManager::AddMiniFrame  
 將框架加入迷你框架的清單。  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 框架指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果框架不在迷你框架的清單，且已成功; 新增`FALSE`否則。  
  
##  <a name="adjustpaneframes"></a>  CDockingManager::AdjustPaneFrames  
 會導致`WM_NCCALCSIZE`訊息傳送至所有窗格和`CPaneFrameWnd`windows。  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="adjustrecttoclientarea"></a>  CDockingManager::AdjustRectToClientArea  
 調整矩形的對齊方式。  
  
```  
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rectResult`  
 若要參考`CRect`物件  
  
 [輸入] `dwAlignment`  
 對齊方式`CRect`物件  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果對齊`CRect`物件經過調整。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 `dwAlignment`參數可以有下列值之一：  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="alignautohidepane"></a>  CDockingManager::AlignAutoHidePane  
 調整大小，以自動隱藏模式中的停駐窗格所花費的整個寬度或高度的畫面格的工作區，以停駐的站台。  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDefaultSlider`  
 停駐的滑桿窗格。  
  
 [輸入] `bIsVisible`  
 `TRUE` 如果停駐窗格是可見的。`FALSE`否則。  
  
##  <a name="autohidepane"></a>  CDockingManager::AutoHidePane  
 建立自動隱藏工具列。  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 列的指標窗格。  
  
 [輸入] `pCurrAutoHideToolBar`  
 指標，自動隱藏工具列。  
  
### <a name="return-value"></a>傳回值  
 `NULL` 如果自動隱藏工具列不是。否則為新的工具列的指標。  
  
##  <a name="bringbarstotop"></a>  CDockingManager::BringBarsToTop  
 將有指定的對齊上方停駐的列。  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwAlignment`  
 其他視窗的頂端會前往的停駐列對齊方式。  
  
 [輸入] `bExcludeDockedBars`  
 `TRUE` 若要排除的停駐的長條上方; 在否則`FALSE`。  
  
##  <a name="buildpanesmenu"></a>  CDockingManager::BuildPanesMenu  
 將功能表中的停駐窗格和工具列的名稱。  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `menu`  
 若要新增的停駐窗格和工具列，名稱功能表。  
  
 [輸入] `bToolbarsOnly`  
 `TRUE` 加入功能表; 只有工具列名稱`FALSE`否則。  
  
##  <a name="calcexpecteddockedrect"></a>  CDockingManager::CalcExpectedDockedRect  
 計算預期的固定視窗矩形。  
  
```  
void CalcExpectedDockedRect(
    CWnd* pWnd,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 若要停駐視窗的指標。  
  
 [輸入] `ptMouse`  
 滑鼠位置。  
  
 [輸出] `rectResult`  
 導出的矩形。  
  
 [輸入] `bDrawTab`  
 `TRUE` 若要繪製索引標籤。否則`FALSE`。  
  
 [輸出] `ppTargetBar`  
 指向 [目標] 窗格的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會計算如果使用者拖曳到所指定的點的視窗，視窗會佔據的矩形`ptMouse`和它那里停駐。  
  
##  <a name="create"></a>  CDockingManager::Create  
 建立停駐的管理員。  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pParentWnd`  
 停駐的管理員的父框架指標。 此值不能`NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 一律。  
  
##  <a name="determinepaneandstatus"></a>  CDockingManager::DeterminePaneAndStatus  
 決定包含指定的點和其銜接狀態的窗格。  
  
```  
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,  
    int nSensitivity,  
    DWORD dwEnabledAlignment,  
    CBasePane** ppTargetBar,  
    const CBasePane* pBarToIgnore,  
    const CBasePane* pBarToDock);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pt`  
 若要檢查窗格的位置。  
  
 [輸入] `nSensitivity`  
 值，以延長每個已選取窗格的視窗矩形。 此增加區域中指定的點是否窗格可滿足搜尋條件。  
  
 [輸入] `dwEnabledAlignment`  
 停駐窗格的對齊方式。  
  
 [輸出] `ppTargetBar`  
 指向 [目標] 窗格的指標。  
  
 [輸入] `pBarToIgnore`  
 這個方法會忽略窗格。  
  
 [輸入] `pBarToDock`  
 停駐窗格。  
  
### <a name="return-value"></a>傳回值  
 停駐的狀態。  
  
### <a name="remarks"></a>備註  
 停駐狀態可以是下列值之一：  
  
|AFX_CS_STATUS 值|意義|  
|---------------------------|-------------|  
|CS_NOTHING|指標不是透過停駐位置。 因此，保留窗格浮動。|  
|CS_DOCK_IMMEDIATELY|指標位於即時模式中停駐位置 （DT_IMMEDIATE 樣式已啟用），所以必須立即停駐窗格。|  
|CS_DELAY_DOCK|指標是透過另一個停駐窗格或主框架的邊緣與停駐位置。|  
|CS_DELAY_DOCK_TO_TAB|指標是透過停駐在索引標籤式視窗中，窗格會停駐位置。 會發生這種情況是當滑鼠位於另一個停駐窗格的標題或索引標籤式窗格的索引標籤區域上。|  
  
##  <a name="disablerestoredockstate"></a>  CDockingManager::DisableRestoreDockState  
 啟用或停用停駐配置從登錄載入。  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bDisable`  
 `TRUE` 若要停用載入停駐配置從登錄中。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 載入應用程式的狀態時，您必須保留目前的停駐窗格和工具列版面配置時，請呼叫這個方法。  
  
##  <a name="dockpane"></a>  CDockingManager::DockPane  
 另一個窗格或框架視窗停駐窗格。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 列的指標將停駐窗格。  
  
 [輸入] `nDockBarID`  
 若要停駐列的識別碼。  
  
 [輸入] `lpRect`  
 目的矩形。  
  
##  <a name="dockpaneleftof"></a>  CDockingManager::DockPaneLeftOf  
 將窗格停駐於另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBarToDock`  
 要左邊的停駐窗格的指標`pTargetBar`。  
  
 [輸入] `pTargetBar`  
 [目標] 窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 停駐窗格，否則， `FALSE`。  
  
##  <a name="enableautohidepanes"></a>  CDockingManager::EnableAutoHidePanes  
 可讓主框架窗格的停駐、 建立停駐窗格中，並將它加入至控制列清單。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwStyle`  
 停駐的對齊方式。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 建立停駐窗格`FALSE`否則。  
  
##  <a name="enabledocking"></a>  CDockingManager::EnableDocking  
 建立停駐窗格並啟用停駐窗格的主要畫面格。  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwStyle`  
 停駐的對齊方式。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 建立停駐窗格`FALSE`否則。  
  
##  <a name="enabledocksitemenu"></a>  CDockingManager::EnableDockSiteMenu  
 顯示其他按鈕會開啟快顯功能表上的所有停駐窗格的標題。  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE` 若要啟用停駐的 [網站] 功能表。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 停駐的 [網站] 功能表會顯示下列選項，以變更窗格的停駐狀態：  
  
- `Floating` -讓窗格浮動  
  
- `Docking` -停駐窗格，以在其中窗格上次停駐位置的主要畫面格  
  
- `AutoHide` -窗格切換到自動隱藏模式  
  
- `Hide` -隱藏窗格  
  
 根據預設，不會顯示此功能表。  
  
##  <a name="enablepanecontextmenu"></a>  CDockingManager::EnablePaneContextMenu  
 告知要顯示一個特殊的內容功能表，使用者按一下滑鼠按鈕和程式庫會處理 WM_CONTEXTMENU 訊息時，有一份應用程式工具列和停駐窗格的程式庫。  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 如果`TRUE`，媒體櫃的自動內容功能表中，支援，如果會變成`FALSE`文件庫，則會關閉自動內容功能表的支援。  
  
 [輸入] `uiCustomizeCmd`  
 命令 id**自訂**功能表中的項目。  
  
 [輸入] `strCustomizeText`  
 文字**自訂**項目。  
  
 [輸入] `bToolbarsOnly`  
 如果`TRUE`，功能表就會顯示一份應用程式工具列; 如果`FALSE`，程式庫會將這份清單中的應用程式停駐窗格。  
  
##  <a name="finddocksite"></a>  CDockingManager::FindDockSite  
 擷取列窗格中，位於指定位置，且具有指定的對齊方式。  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwAlignment`  
 列的對齊方式 窗格。  
  
 [輸入] `bOuter`  
 如果`TRUE`，擷取在控制列清單中的標頭位置的列。 否則，擷取在控制列的結尾位置清單中的列。  
  
### <a name="return-value"></a>傳回值  
 具有指定的對齊方式; 停駐窗格`NULL`否則。  
  
##  <a name="findpanebyid"></a>  CDockingManager::FindPaneByID  
 尋找窗格中所指定的控制項 id。  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uBarID`  
 指定要尋找窗格的控制項 ID。  
  
 [輸入] `bSearchMiniFrames`  
 `TRUE` 若要在搜尋中包含所有在浮動窗格。 `FALSE` 若要包括僅停駐的窗格。  
  
### <a name="return-value"></a>傳回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)物件具有指定的控制項識別碼，或`NULL`如果找不到指定的窗格。  
  
### <a name="remarks"></a>備註  
  
##  <a name="finddocksitebypane"></a>  CDockingManager::FindDockSiteByPane  
 傳回列 id 為目標窗格的窗格。  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pTargetBar`  
 目標窗格指標。  
  
### <a name="return-value"></a>傳回值  
 長條圖目標窗格; 識別碼的窗格`NULL`是否有任何例如列窗格。  
  
##  <a name="fixupvirtualrects"></a>  CDockingManager::FixupVirtualRects  
 認可所有目前工具列位置虛擬矩形。  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>備註  
 當使用者開始拖曳工具列時，應用程式會記住其原始位置中的*虛擬矩形*。 當使用者將其停駐站台的工具列時，工具列就可能會變更其他工具列。 其他工具列的原始位置會儲存在對應的虛擬矩形。  
  
##  <a name="framefrompoint"></a>  CDockingManager::FrameFromPoint  
 傳回包含指定的點的框架。  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pt`  
 指定的點，若要檢查的螢幕座標。  
  
 [輸入] `pFrameToExclude`  
 要排除的畫面格指標。  
  
 [輸入] `bFloatMultiOnly`  
 `TRUE` 若要排除的執行個體的畫面格`CMultiPaneFrameWnd`;`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 包含指定的點; 的框架`NULL`否則。  
  
##  <a name="getclientareabounds"></a>  CDockingManager::GetClientAreaBounds  
 取得包含界限的用戶端區域的矩形。  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rcClient`  
 包含用戶端區域的界限的矩形的參考。  
  
### <a name="return-value"></a>傳回值  
 包含用戶端區域的界限的矩形。  
  
##  <a name="getdockingmode"></a>  CDockingManager::GetDockingMode  
 傳回目前的停駐模式。  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>傳回值  
 列舉程式值，代表目前停駐模式。 它可以是下列值之一：  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
### <a name="remarks"></a>備註  
 若要設定停駐的模式，請呼叫[CDockingManager::SetDockingMode](#setdockingmode)。  
  
##  <a name="getdocksiteframewnd"></a>  CDockingManager::GetDockSiteFrameWnd  
 取得父視窗框架指標。  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 父視窗框架指標。  
  
##  <a name="getenabledautohidealignment"></a>  CDockingManager::GetEnabledAutoHideAlignment  
 傳回已啟用的對齊方式的窗格。  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元組合`CBRS_ALIGN_`旗標或 0，如果未啟用自動隱藏窗格。 如需詳細資訊，請參閱[CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)。  
  
### <a name="remarks"></a>備註  
 方法會傳回自動隱藏控制列的已啟用對齊方式。 若要啟用自動隱藏列，請呼叫[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)。  
  
##  <a name="getminiframes"></a>  CDockingManager::GetMiniFrames  
 取得主機的清單。  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含屬於停駐的管理員控制列的主機清單。  
  
##  <a name="getouteredgebounds"></a>  CDockingManager::GetOuterEdgeBounds  
 取得包含外部的框架邊緣的矩形。  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含外部的框架邊緣的矩形。  
  
##  <a name="getpanelist"></a>  CDockingManager::GetPaneList  
 傳回屬於停駐的管理員窗格的清單。 這包括所有浮動窗格。  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `lstBars`  
 包含目前停駐的管理員的所有窗格。  
  
 [輸入] `bIncludeAutohide`  
 `TRUE` 包含自動隱藏模式中的窗格否則， `FALSE`。  
  
 [輸入] `pRTCFilter`  
 如果沒有`NULL`，傳回的清單包含只在指定的執行階段類別的窗格。  
  
 [輸入] `bIncludeTabs`  
 `TRUE` 包含索引標籤。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果停駐的管理員中有任何索引標籤式的窗格，方法會傳回指向[CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)物件，而且您必須 索引標籤列舉明確。  
  
 使用`pRTCFilter`來取得特定類別的窗格。 例如，您可以取得只工具列適當地設定此值。  
  
##  <a name="getsmartdockingmanager"></a>  CDockingManager::GetSmartDockingManager  
 擷取智慧停駐的管理員的指標。  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標[智慧停駐的管理員](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534)。  
  
##  <a name="getsmartdockingmanagerpermanent"></a>  CDockingManager::GetSmartDockingManagerPermanent  
 擷取智慧停駐的管理員的指標。  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 智慧停駐的管理員指標。  
  
##  <a name="getsmartdockingparams"></a>  CDockingManager::GetSmartDockingParams  
 智慧停駐參數傳回停駐的管理員。  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>傳回值  
 包含目前停駐的管理員智慧停駐參數類別。 如需詳細資訊，請參閱[CSmartDockingInfo 類別](../../mfc/reference/csmartdockinginfo-class.md)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hideautohidepanes"></a>  CDockingManager::HideAutoHidePanes  
 隱藏自動隱藏模式中的窗格。  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBarToExclude`  
 要排除隱藏列的指標。  
  
 [輸入] `bImmediately`  
 `TRUE` 若要立即; 隱藏窗格`FALSE`來隱藏自動隱藏效果 窗格。  
  
##  <a name="insertdocksite"></a>  CDockingManager::InsertDockSite  
 建立停駐窗格，並將它插入控制列清單。  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `info`  
 結構，其中包含關於停駐窗格的對齊方式資訊。  
  
 [輸入] `dwAlignToInsertAfter`  
 停駐窗格的對齊方式。  
  
 [輸出] `ppDockBar`  
 指向停駐窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 建立停駐窗格`FALSE`否則。  
  
##  <a name="insertpane"></a>  CDockingManager::InsertPane  
 控制項窗格插入控制列清單。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pControlBar`  
 控制項窗格的指標。  
  
 [輸入] `pTarget`  
 目標窗格的指標。  
  
 [輸入] `bAfter`  
 `TRUE` 插入窗格的 [目標] 窗格中; 位置之後`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果控制項窗格已成功新增到清單的控制列。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 如果 [控制項] 窗格已經存在的控制列清單中，或控制列清單中沒有 [目標] 窗格中，則這個方法會傳回 false。  
  
##  <a name="isdocksitemenu"></a>  CDockingManager::IsDockSiteMenu  
 指定是否顯示快顯功能表上的所有窗格的標題。  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果顯示停駐的網站 功能表上的所有停駐窗格; 標題否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫啟用停駐的 [網站] 功能表[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)。  
  
##  <a name="isinadjustlayout"></a>  CDockingManager::IsInAdjustLayout  
 決定所有窗格的配置會進行調整。  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果所有窗格的配置會進行調整;`FALSE`否則。  
  
##  <a name="isolecontainermode"></a>  CDockingManager::IsOLEContainerMode  
 指定是否停駐的管理員為 OLE 容器模式。  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果停駐的管理員為 OLE 容器模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在 OLE 容器模式中，會隱藏所有停駐窗格和應用程式工具列。 如果您已將窗格也會在此模式中隱藏[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)至`TRUE`。  
  
##  <a name="ispointneardocksite"></a>  CDockingManager::IsPointNearDockSite  
 判斷指定的點是否停駐位置附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `point`  
 指定的點。  
  
 [輸出] `dwBarAlignment`  
 指定的點是附近的邊緣。 可能的值為 `CBRS_ALIGN_LEFT`、`CBRS_ALIGN_RIGHT`、`CBRS_ALIGN_TOP` 和 `CBRS_ALIGN_BOTTOM`。  
  
 [輸出] `bOuterEdge`  
 `TRUE` 如果點附近外框的停駐位置。`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果點附近停駐位置。否則`FALSE`。  
  
##  <a name="isprintpreviewvalid"></a>  CDockingManager::IsPrintPreviewValid  
 決定是否預覽列印模式設定。  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果預覽列印模式就會設定。`FALSE`否則。  
  
##  <a name="loadstate"></a>  CDockingManager::LoadState  
 從登錄載入停駐的管理員狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 設定檔名稱。  
  
 [輸入] `uiID`  
 停駐的管理員識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 載入停駐的管理員狀態否則`FALSE`。  
  
##  <a name="lockupdate"></a>  CDockingManager::LockUpdate  
 鎖定指定的視窗。  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bLock`  
 `TRUE` 如果視窗已鎖定。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 當視窗已鎖定時，無法移動，而且無法重繪。  
  
##  <a name="m_bhidedockingbarsincontainermode"></a>  CDockingManager::m_bHideDockingBarsInContainerMode  
 指定是否停駐的管理員隱藏 OLE 容器模式中的窗格。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>備註  
 將此值設定為`FALSE`如果您想要保留所有窗格停駐於主框架顯示時應用程式是在 OLE 容器模式。 根據預設，這個值是`TRUE`。  
  
##  <a name="m_dockmodeglobal"></a>  CDockingManager::m_dockModeGlobal  
 指定全域的停駐模式。  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>備註  
 根據預設，每個停駐窗格會使用此停駐的模式。 如需可以將此欄位的值的詳細資訊，請參閱[cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。  
  
##  <a name="m_ndocksensitivity"></a>  CDockingManager::m_nDockSensitivity  
 指定的停駐的敏感度。  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>備註  
 停駐敏感度定義如何關閉浮動窗格可以讓停駐窗格、 銜接站台或另一個窗格，framework 就會變更其狀態，以停駐之前。  
  
##  <a name="m_ntimeoutbeforedockingbardock"></a>  CDockingManager::m_nTimeOutBeforeDockingBarDock  
 指定時間，以毫秒為單位，才能停駐窗格停駐在停駐的即時模式中。  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>備註  
 停駐窗格時，架構會等候指定的時間長度。 這樣可避免不小心停駐位置時，使用者仍拖曳窗格。  
  
##  <a name="m_ntimeoutbeforetoolbardock"></a>  CDockingManager::m_nTimeOutBeforeToolBarDock  
 指定時間，以毫秒為單位，工具列停駐於主框架視窗之前。  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>備註  
 工具列停駐之前，架構會等候指定的時間長度。 這樣可避免不小心停駐位置時，使用者仍拖曳工具列。  
  
##  <a name="onactivateframe"></a>  CDockingManager::OnActivateFrame  
 框架視窗變成使用中或已停用時由架構呼叫。  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bActivate`  
 如果`TRUE`，框架視窗變成使用中; 如果`FALSE`，框架視窗已停用。  
  
##  <a name="onclosepopupmenu"></a>  CDockingManager::OnClosePopupMenu  
 架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>備註  
 即將關閉目前的主視窗時，架構會傳送 WM_DESTROY 訊息。 覆寫此方法以處理來自通知`CMFCPopupMenu`屬於框架視窗物件時`CMFCPopupMenu`物件處理程序`WM_DESTROY`訊息。  
  
##  <a name="onmoveminiframe"></a>  CDockingManager::OnMoveMiniFrame  
 由架構呼叫以移動迷你框架視窗。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pFrame`  
 迷你框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法成功。否則`FALSE`。  
  
##  <a name="onpanecontextmenu"></a>  CDockingManager::OnPaneContextMenu  
 建置已窗格的清單功能表時由架構呼叫。  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `point`  
 指定功能表的位置。  
  
##  <a name="panefrompoint"></a>  CDockingManager::PaneFromPoint  
 傳回包含指定的點的窗格。  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL,  
    BOOL bCheckVisibility = FALSE,  
    const CBasePane* pBarToIgnore = NULL) const;  
  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType = NULL,  
    const CBasePane* pBarToIgnore = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `point`  
 指定的點，若要檢查的螢幕座標。  
  
 [輸入] `nSensitivity`  
 如果要增加每個已選取窗格的視窗矩形的值。 如果指定的點是此擴大區域窗格可滿足搜尋準則。  
  
 [輸入] `bExactBar`  
 `TRUE` 表示忽略`nSensitivity`參數，否則`FALSE`。  
  
 [輸入] `pRTCBarType`  
 如果沒有`NULL`，方法會搜尋指定類型的窗格。  
  
 [輸入] `bCheckVisibility`  
 `TRUE` 若要檢查可見窗格;否則， `FALSE`。  
  
 [輸出] `dwAlignment`  
 如果窗格找到指定的點，此參數會包含已最接近指定位置的窗格的側邊。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [輸入] `pBarToIgnore`  
 如果沒有`NULL`，這個方法會忽略此參數所指定的窗格。  
  
### <a name="return-value"></a>傳回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)-衍生物件，其中包含指定的時間點，或`NULL`如果找不到任何窗格。  
  
### <a name="remarks"></a>備註  
 此函數會傳回，而且找不到窗格中，當`dwAlignment`包含指定點的對齊方式。 例如，如果點已頂端的窗格中，最接近`dwAlignment`設`CBRS_ALIGN_TOP`。  
  
##  <a name="processpanecontextmenucommand"></a>  CDockingManager::ProcessPaneContextMenuCommand  
 由架構呼叫來選取或清除核取方塊，針對指定的命令，並重新計算顯示窗格的配置。  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 在功能表中的控制列識別碼。  
  
 [輸入] `nCode`  
 命令通知程式碼。  
  
 [輸入] `pExtra`  
 Void 的指標會轉換成指標`CCmdUI`如果`nCode`是 CN_UPDATE_COMMAND_UI。  
  
 [輸入] `pHandlerInfo`  
 資訊結構的指標。 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果`pEXtra`不是 NULL 和`nCode`等於 CN_UPDATE_COMMAND_UI，或如果沒有使用指定的控制列`nID`。  
  
##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout  
 重新計算存在的控制項清單中的控制項的內部配置。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bNotify`  
 不使用這個參數。  
  
##  <a name="releaseemptypanecontainers"></a>  CDockingManager::ReleaseEmptyPaneContainers  
 釋出空白窗格容器。  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="removehiddenmditabbedbar"></a>  CDockingManager::RemoveHiddenMDITabbedBar  
 移除指定的隱藏窗格列。  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 列的指標窗格，即可移除。  
  
##  <a name="removeminiframe"></a>  CDockingManager::RemoveMiniFrame  
 從迷你框架的清單中移除指定的範圍。  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 要移除的畫面格指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已移除指定的範圍。`FALSE`否則。  
  
##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager  
 取消登錄 窗格，並從停駐的管理員在清單中移除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 要移除窗格的指標。  
  
 [輸入] `bDestroy`  
 如果`TRUE`，[移除] 窗格會終結。  
  
 [輸入] `bAdjustLayout`  
 如果`TRUE`，立即調整停駐的配置。  
  
 [輸入] `bAutoHide`  
 如果`TRUE`，從自動隱藏列清單移除窗格。 如果`FALSE`，窗格會從規則窗格的清單移除。  
  
 [輸入] `pBarReplacement`  
 取代 [移除] 窗格之窗格的指標。  
  
##  <a name="replacepane"></a>  CDockingManager::ReplacePane  
 以一個窗格取代另一個。  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pOriginalBar`  
 [原始] 窗格的指標。  
  
 [輸入] `pNewBar`  
 指標，會取代原始窗格的窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果成功取代窗格;`FALSE`否則。  
  
##  <a name="resortminiframesforzorder"></a>  CDockingManager::ResortMiniFramesForZOrder  
 訴諸的迷你框架清單中的框架。  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="savestate"></a>  CDockingManager::SaveState  
 將停駐的管理員狀態儲存至登錄。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 登錄機碼路徑。  
  
 [輸入] `uiID`  
 停駐的管理員識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 儲存狀態否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 儲存至登錄的停駐的管理員狀態牽涉到儲存狀態的控制列、 自動隱藏列的狀態和迷你框架中停駐的管理員的狀態。  
  
##  <a name="sendmessagetominiframes"></a>  CDockingManager::SendMessageToMiniFrames  
 將指定的訊息傳送至所有的迷你框架。  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uMessage`  
 要傳送的訊息。  
  
 [輸入] `wParam`  
 額外的訊息相關資訊。  
  
 [輸入] `lParam`  
 額外的訊息相關資訊。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 一律。  
  
##  <a name="serialize"></a>  CDockingManager::Serialize  
 寫入封存停駐的管理員。  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `ar`  
 保存物件的參考。  
  
### <a name="remarks"></a>備註  
 停駐的管理員寫入封存涉及判斷停駐控制列和滑桿，並寫入封存中的控制列、 迷你框架、 自動隱藏列和 MDI 索引列的數目。  
  
##  <a name="setautohidezorder"></a>  CDockingManager::SetAutohideZOrder  
 設定大小、 寬度和高度的控制列和指定的窗格。  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pAHDockingBar`  
 可停駐窗格的指標。  
  
##  <a name="setdockingmode"></a>  CDockingManager::SetDockingMode  
 設定固定的模式。  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>參數  
 `dockMode`  
 指定新的停駐模式。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `theme`  
 指定要用於智慧停駐標記的佈景主題。 它可以是下列的列舉值之一： AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>備註  
 呼叫此靜態方法，以設定停駐的模式。  
  
 `dockMode` 可以是下列值之一：  
  
- `DT_STANDARD` 在 Visual Studio.NET 2003年中實作時，停駐模式標準。 拖曳窗格沒有拖曳的內容。  
  
- `DT_IMMEDIATE` -即時停駐的模式，以實作 Microsoft Visio。 拖曳窗格拖曳內容，但沒有標記會顯示。  
  
- `DT_SMART` -在 Visual Studio 2005 中實作時，智慧停駐的模式。 拖曳窗格拖曳內容，而且會顯示智慧標記會顯示可停駐窗格。  
  
##  <a name="setdockstate"></a>  CDockingManager::SetDockState  
 設定停駐控制列、 迷你框架和自動隱藏列的狀態。  
  
```  
virtual void SetDockState();
```  
  
##  <a name="setprintpreviewmode"></a>  CDockingManager::SetPrintPreviewMode  
 設定會顯示在預覽列印中的長條的預覽列印模式。  
  
```  
void SetPrintPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bPreview`  
 `TRUE` 如果預覽列印模式設定;`FALSE`否則。  
  
 [輸入] `pState`  
 預覽狀態指標。 不使用這個參數。  
  
##  <a name="setsmartdockingparams"></a>  CDockingManager::SetSmartDockingParams  
 設定定義智慧停駐行為的參數。  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `params`  
 定義智慧停駐的參數。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂外觀、 色彩或智慧停駐標記的圖形，請呼叫這個方法。  
  
 若要使用智慧停駐標記的預設外觀，將 未初始化的執行個體[CSmartDockingInfo 類別](../../mfc/reference/csmartdockinginfo-class.md)至`params`。  
  
##  <a name="showdelayshowminiframes"></a>  CDockingManager::ShowDelayShowMiniFrames  
 顯示或隱藏的迷你框架視窗。  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bShow`  
 `TRUE` 若要讓顯示框架的視窗作用;`FALSE to`隱藏框架的視窗。  
  
##  <a name="showpanes"></a>  CDockingManager::ShowPanes  
 顯示或隱藏控制項，並自動隱藏列的窗格。  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bShow`  
 `TRUE` 若要顯示的窗格。`FALSE to`隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
##  <a name="startsdocking"></a>  CDockingManager::StartSDocking  
 啟動指定的視窗智慧停駐的管理員的對齊方式根據智慧停駐。  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDockingWnd`  
 若要停駐視窗的指標。  
  
##  <a name="stopsdocking"></a>  CDockingManager::StopSDocking  
 停駐點智慧停駐。  
  
```  
void StopSDocking();
```  
  
##  <a name="getsmartdockingtheme"></a>  CDockingManager::GetSmartDockingTheme  
 傳回用來顯示智慧停駐標記的佈景主題的靜態方法。  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>傳回值  
 下列的列舉值的其中一個： AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)
