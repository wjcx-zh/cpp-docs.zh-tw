---
title: CFrameWndEx 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx::ActiveItemRecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::AddPane
- AFXFRAMEWNDEX/CFrameWndEx::AdjustDockingLayout
- AFXFRAMEWNDEX/CFrameWndEx::DelayUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::DockPane
- AFXFRAMEWNDEX/CFrameWndEx::DockPaneLeftOf
- AFXFRAMEWNDEX/CFrameWndEx::EnableAutoHidePanes
- AFXFRAMEWNDEX/CFrameWndEx::EnableDocking
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMainMenu
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMode
- AFXFRAMEWNDEX/CFrameWndEx::EnableLoadDockState
- AFXFRAMEWNDEX/CFrameWndEx::EnablePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::GetActivePopup
- AFXFRAMEWNDEX/CFrameWndEx::GetDefaultResId
- AFXFRAMEWNDEX/CFrameWndEx::GetDockingManager
- AFXFRAMEWNDEX/CFrameWndEx::GetMenuBar
- AFXFRAMEWNDEX/CFrameWndEx::GetPane
- AFXFRAMEWNDEX/CFrameWndEx::GetRibbonBar
- AFXFRAMEWNDEX/CFrameWndEx::GetTearOffBars
- AFXFRAMEWNDEX/CFrameWndEx::GetToolbarButtonToolTipText
- AFXFRAMEWNDEX/CFrameWndEx::InsertPane
- AFXFRAMEWNDEX/CFrameWndEx::IsFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::IsMenuBarAvailable
- AFXFRAMEWNDEX/CFrameWndEx::IsPointNearDockSite
- AFXFRAMEWNDEX/CFrameWndEx::IsPrintPreview
- AFXFRAMEWNDEX/CFrameWndEx::LoadFrame
- AFXFRAMEWNDEX/CFrameWndEx::NegotiateBorderSpace
- AFXFRAMEWNDEX/CFrameWndEx::OnActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnActivateApp
- AFXFRAMEWNDEX/CFrameWndEx::OnChangeVisualManager
- AFXFRAMEWNDEX/CFrameWndEx::OnClose
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseDockingPane
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnClosePopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnCmdMsg
- AFXFRAMEWNDEX/CFrameWndEx::OnContextHelp
- AFXFRAMEWNDEX/CFrameWndEx::OnCreate
- AFXFRAMEWNDEX/CFrameWndEx::OnDestroy
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuImage
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuLogo
- AFXFRAMEWNDEX/CFrameWndEx::OnDWMCompositionChanged
- AFXFRAMEWNDEX/CFrameWndEx::OnExitSizeMove
- AFXFRAMEWNDEX/CFrameWndEx::OnGetMinMaxInfo
- AFXFRAMEWNDEX/CFrameWndEx::OnIdleUpdateCmdUI
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonDown
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonUp
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuButtonToolHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuChar
- AFXFRAMEWNDEX/CFrameWndEx::OnMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnMoveMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnNcActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnNcCalcSize
- AFXFRAMEWNDEX/CFrameWndEx::OnNcHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnNcMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnNcPaint
- AFXFRAMEWNDEX/CFrameWndEx::OnPaneCheck
- AFXFRAMEWNDEX/CFrameWndEx::OnPostPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnPowerBroadcast
- AFXFRAMEWNDEX/CFrameWndEx::OnSetMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSetPreviewMode
- AFXFRAMEWNDEX/CFrameWndEx::OnSetText
- AFXFRAMEWNDEX/CFrameWndEx::OnShowCustomizePane
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPanes
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSize
- AFXFRAMEWNDEX/CFrameWndEx::OnSizing
- AFXFRAMEWNDEX/CFrameWndEx::OnSysColorChange
- AFXFRAMEWNDEX/CFrameWndEx::OnTearOffMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarContextMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarCreateNew
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarDelete
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameTitle
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdatePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnWindowPosChanged
- AFXFRAMEWNDEX/CFrameWndEx::PaneFromPoint
- AFXFRAMEWNDEX/CFrameWndEx::PreTranslateMessage
- AFXFRAMEWNDEX/CFrameWndEx::RecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::RemovePaneFromDockManager
- AFXFRAMEWNDEX/CFrameWndEx::SetDockState
- AFXFRAMEWNDEX/CFrameWndEx::SetPrintPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::SetupToolbarMenu
- AFXFRAMEWNDEX/CFrameWndEx::ShowFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::ShowPane
- AFXFRAMEWNDEX/CFrameWndEx::UpdateCaption
- AFXFRAMEWNDEX/CFrameWndEx::WinHelp
dev_langs:
- C++
helpviewer_keywords:
- CFrameWndEx [MFC], ActiveItemRecalcLayout
- CFrameWndEx [MFC], AddPane
- CFrameWndEx [MFC], AdjustDockingLayout
- CFrameWndEx [MFC], DelayUpdateFrameMenu
- CFrameWndEx [MFC], DockPane
- CFrameWndEx [MFC], DockPaneLeftOf
- CFrameWndEx [MFC], EnableAutoHidePanes
- CFrameWndEx [MFC], EnableDocking
- CFrameWndEx [MFC], EnableFullScreenMainMenu
- CFrameWndEx [MFC], EnableFullScreenMode
- CFrameWndEx [MFC], EnableLoadDockState
- CFrameWndEx [MFC], EnablePaneMenu
- CFrameWndEx [MFC], GetActivePopup
- CFrameWndEx [MFC], GetDefaultResId
- CFrameWndEx [MFC], GetDockingManager
- CFrameWndEx [MFC], GetMenuBar
- CFrameWndEx [MFC], GetPane
- CFrameWndEx [MFC], GetRibbonBar
- CFrameWndEx [MFC], GetTearOffBars
- CFrameWndEx [MFC], GetToolbarButtonToolTipText
- CFrameWndEx [MFC], InsertPane
- CFrameWndEx [MFC], IsFullScreen
- CFrameWndEx [MFC], IsMenuBarAvailable
- CFrameWndEx [MFC], IsPointNearDockSite
- CFrameWndEx [MFC], IsPrintPreview
- CFrameWndEx [MFC], LoadFrame
- CFrameWndEx [MFC], NegotiateBorderSpace
- CFrameWndEx [MFC], OnActivate
- CFrameWndEx [MFC], OnActivateApp
- CFrameWndEx [MFC], OnChangeVisualManager
- CFrameWndEx [MFC], OnClose
- CFrameWndEx [MFC], OnCloseDockingPane
- CFrameWndEx [MFC], OnCloseMiniFrame
- CFrameWndEx [MFC], OnClosePopupMenu
- CFrameWndEx [MFC], OnCmdMsg
- CFrameWndEx [MFC], OnContextHelp
- CFrameWndEx [MFC], OnCreate
- CFrameWndEx [MFC], OnDestroy
- CFrameWndEx [MFC], OnDrawMenuImage
- CFrameWndEx [MFC], OnDrawMenuLogo
- CFrameWndEx [MFC], OnDWMCompositionChanged
- CFrameWndEx [MFC], OnExitSizeMove
- CFrameWndEx [MFC], OnGetMinMaxInfo
- CFrameWndEx [MFC], OnIdleUpdateCmdUI
- CFrameWndEx [MFC], OnLButtonDown
- CFrameWndEx [MFC], OnLButtonUp
- CFrameWndEx [MFC], OnMenuButtonToolHitTest
- CFrameWndEx [MFC], OnMenuChar
- CFrameWndEx [MFC], OnMouseMove
- CFrameWndEx [MFC], OnMoveMiniFrame
- CFrameWndEx [MFC], OnNcActivate
- CFrameWndEx [MFC], OnNcCalcSize
- CFrameWndEx [MFC], OnNcHitTest
- CFrameWndEx [MFC], OnNcMouseMove
- CFrameWndEx [MFC], OnNcPaint
- CFrameWndEx [MFC], OnPaneCheck
- CFrameWndEx [MFC], OnPostPreviewFrame
- CFrameWndEx [MFC], OnPowerBroadcast
- CFrameWndEx [MFC], OnSetMenu
- CFrameWndEx [MFC], OnSetPreviewMode
- CFrameWndEx [MFC], OnSetText
- CFrameWndEx [MFC], OnShowCustomizePane
- CFrameWndEx [MFC], OnShowPanes
- CFrameWndEx [MFC], OnShowPopupMenu
- CFrameWndEx [MFC], OnSize
- CFrameWndEx [MFC], OnSizing
- CFrameWndEx [MFC], OnSysColorChange
- CFrameWndEx [MFC], OnTearOffMenu
- CFrameWndEx [MFC], OnToolbarContextMenu
- CFrameWndEx [MFC], OnToolbarCreateNew
- CFrameWndEx [MFC], OnToolbarDelete
- CFrameWndEx [MFC], OnUpdateFrameMenu
- CFrameWndEx [MFC], OnUpdateFrameTitle
- CFrameWndEx [MFC], OnUpdatePaneMenu
- CFrameWndEx [MFC], OnWindowPosChanged
- CFrameWndEx [MFC], PaneFromPoint
- CFrameWndEx [MFC], PreTranslateMessage
- CFrameWndEx [MFC], RecalcLayout
- CFrameWndEx [MFC], RemovePaneFromDockManager
- CFrameWndEx [MFC], SetDockState
- CFrameWndEx [MFC], SetPrintPreviewFrame
- CFrameWndEx [MFC], SetupToolbarMenu
- CFrameWndEx [MFC], ShowFullScreen
- CFrameWndEx [MFC], ShowPane
- CFrameWndEx [MFC], UpdateCaption
- CFrameWndEx [MFC], WinHelp
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2854199796f5d75cc4b24016def3c63327a5d511
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692038"
---
# <a name="cframewndex-class"></a>CFrameWndEx 類別
實作 Windows 單一文件介面 (SDI) 重疊或快顯框架視窗的功能，並提供管理視窗的成員。 它會擴充[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|調整 OLE 用戶端項目和框架工作區的配置。|  
|`CFrameWndEx::AddDockSite`|不會使用這個方法。|  
|[CFrameWndEx::AddPane](#addpane)|一種控制列向停駐的管理員。|  
|[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|重新計算停駐在框架視窗的所有窗格的配置。|  
|[CFrameWndEx::DelayUpdateFrameMenu](#delayupdateframemenu)|設定 [框架] 功能表和命令處理閒置時再更新。|  
|[CFrameWndEx::DockPane](#dockpane)|在框架視窗停駐在指定的窗格。|  
|[CFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐在另一個窗格的左邊。|  
|[CFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|當指定的側邊的主框架視窗停駐時，可讓  窗格的 自動隱藏模式。|  
|[Cframewndex:: Enabledocking](#enabledocking)|可讓屬於框架視窗的窗格停駐。|  
|[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|顯示或隱藏主功能表以全螢幕模式。|  
|[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|可讓框架視窗的全螢幕模式。|  
|[CFrameWndEx::EnableLoadDockState](#enableloaddockstate)|啟用或停用的銜接狀態的載入。|  
|[CFrameWndEx::EnablePaneMenu](#enablepanemenu)|啟用或停用窗格功能表的自動處理。|  
|[CFrameWndEx::GetActivePopup](#getactivepopup)|讓指標回到目前顯示的快顯功能表。|  
|[CFrameWndEx::GetDefaultResId](#getdefaultresid)|傳回架構載入框架視窗時所指定的資源識別碼。|  
|[CFrameWndEx::GetDockingManager](#getdockingmanager)|擷取[CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)框架視窗物件。|  
|[CFrameWndEx::GetMenuBar](#getmenubar)|將指標傳回到附加在框架視窗的功能表列物件。|  
|[CFrameWndEx::GetPane](#getpane)|傳回具有指定的識別碼的窗格的指標|  
|[CFrameWndEx::GetRibbonBar](#getribbonbar)|擷取框架的功能區列控制項。|  
|[CFrameWndEx::GetTearOffBars](#gettearoffbars)|傳回分割狀態的窗格物件清單。|  
|[CFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|應用程式顯示的工具列按鈕的工具提示時，由架構呼叫。|  
|[CFrameWndEx::InsertPane](#insertpane)|向停駐的管理員 窗格。|  
|[CFrameWndEx::IsFullScreen](#isfullscreen)|決定框架視窗是否為全螢幕模式。|  
|[CFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|決定功能表列物件的指標是否有效。|  
|[CFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|指出點是否位於未對齊的區域。|  
|[CFrameWndEx::IsPrintPreview](#isprintpreview)|指示框架視窗是否在列印預覽模式。|  
|[CFrameWndEx::LoadFrame](#loadframe)|建立框架視窗並載入其資源的建構完成之後會呼叫此方法。|  
|[CFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|實作 OLE 用戶端框線交涉。|  
|[CFrameWndEx::OnActivate](#onactivate)|當使用者輸入會切換至或離開框架時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnActivateApp](#onactivateapp)|當應用程式選取或取消選取此選項時，由架構呼叫。|  
|[CFrameWndEx::OnChangeVisualManager](#onchangevisualmanager)|在畫面格的變更需要變更的視覺管理員時，由架構呼叫。|  
|[CFrameWndEx::OnClose](#onclose)|架構會呼叫這個方法，以關閉框架。|  
|[CFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|由架構呼叫，當使用者按一下**關閉**停駐窗格上的按鈕。|  
|[CFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|由架構呼叫，當使用者按一下**關閉**浮動迷你框架視窗上的按鈕。|  
|[CFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。|  
|[CFrameWndEx::OnCmdMsg](#oncmdmsg)|分派命令訊息。|  
|[CFrameWndEx::OnContextHelp](#oncontexthelp)|由架構呼叫以顯示內容相關說明。|  
|[CFrameWndEx::OnCreate](#oncreate)|建立框架後，由架構呼叫。|  
|[CFrameWndEx::OnDestroy](#ondestroy)|終結框架時，由架構呼叫。|  
|[CFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|當應用程式繪製功能表項目相關聯的映像時，由架構呼叫。|  
|[CFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|由架構呼叫時`CMFCPopupMenu`物件處理程序[WM_PAINT](/windows/desktop/gdi/wm-paint)訊息。|  
|[CFrameWndEx::OnDWMCompositionChanged](#ondwmcompositionchanged)|桌面視窗管理員 (DWM) 組合已啟用或停用時由架構呼叫。|  
|[CFrameWndEx::OnExitSizeMove](#onexitsizemove)|移動或調整大小，就會停止在畫面格時由架構呼叫。|  
|[CFrameWndEx::OnGetMinMaxInfo](#ongetminmaxinfo)|框架會調整大小以設定視窗維度限制時，由架構呼叫。|  
|[CFrameWndEx::OnIdleUpdateCmdUI](#onidleupdatecmdui)|由架構呼叫以更新框架顯示命令的處理序閒置時。|  
|[CFrameWndEx::OnLButtonDown](#onlbuttondown)|當使用者按下滑鼠左的按鈕時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnLButtonUp](#onlbuttonup)|當使用者放開滑鼠左的按鈕時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|由架構呼叫時`CMFCToolBarButton`物件處理 WM_NCHITTEST 訊息。|  
|[CFrameWndEx::OnMenuChar](#onmenuchar)|會顯示功能表，並在使用者按下按鍵，並未對應到命令時，由架構呼叫。|  
|[CFrameWndEx::OnMouseMove](#onmousemove)|當滑鼠指標移動時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|窗格視窗移動時，由架構呼叫。|  
|[CFrameWndEx::OnNcActivate](#onncactivate)|必須重新繪製畫面格的非工作區，表示處於作用中狀態的變更時由架構呼叫。|  
|[CFrameWndEx::OnNcCalcSize](#onnccalcsize)|必須計算的大小和位置的工作區時，由架構呼叫。|  
|[CFrameWndEx::OnNcHitTest](#onnchittest)|當滑鼠指標移，或按下或放開滑鼠按鈕時由架構呼叫。|  
|[CFrameWndEx::OnNcMouseMove](#onncmousemove)|當滑鼠指標移入非工作區時，由架構呼叫。|  
|[CFrameWndEx::OnNcPaint](#onncpaint)|必須繪製非工作區時，由架構呼叫。|  
|[CFrameWndEx::OnPaneCheck](#onpanecheck)|由架構呼叫以控制的可見性 窗格。|  
|[CFrameWndEx::OnPostPreviewFrame](#onpostpreviewframe)|當使用者變更的預覽列印模式時，由架構呼叫。|  
|[CFrameWndEx::OnPowerBroadcast](#onpowerbroadcast)|電源管理事件發生時，由架構呼叫。|  
|[CFrameWndEx::OnSetMenu](#onsetmenu)|由架構呼叫以取代框架視窗功能表。|  
|[CFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|由架構呼叫以設定框架的預覽列印模式。|  
|[CFrameWndEx::OnSetText](#onsettext)|由架構呼叫以設定視窗的文字。|  
|[CFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|快速自訂時，由架構呼叫窗格已啟用。|  
|[CFrameWndEx::OnShowPanes](#onshowpanes)|由架構呼叫以顯示或隱藏窗格。|  
|[CFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|啟用快顯功能表時，由架構呼叫。|  
|[CFrameWndEx::OnSize](#onsize)|畫面格的大小變更後，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSizing](#onsizing)|當使用者調整框架，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSysColorChange](#onsyscolorchange)|當系統色彩變更時由架構呼叫。|  
|[CFrameWndEx::OnTearOffMenu](#ontearoffmenu)|當有 tear-off 列功能表啟用時，由架構呼叫。|  
|[CFrameWndEx::OnToolbarContextMenu](#ontoolbarcontextmenu)|由架構呼叫以建立工具列的內容功能表。|  
|[CFrameWndEx::OnToolbarCreateNew](#ontoolbarcreatenew)|架構會呼叫這個方法，以建立新的工具列。|  
|[CFrameWndEx::OnToolbarDelete](#ontoolbardelete)|刪除工具列時由架構呼叫。|  
|[CFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|由架構呼叫以設定框架功能表。|  
|[CFrameWndEx::OnUpdateFrameTitle](#onupdateframetitle)|架構會呼叫這個方法，以更新框架視窗的標題列。|  
|[CFrameWndEx::OnUpdatePaneMenu](#onupdatepanemenu)|由架構呼叫以更新 [窗格] 功能表。|  
|[CFrameWndEx::OnWindowPosChanged](#onwindowposchanged)|由於視窗管理方法的呼叫變更畫面格大小、 位置或疊置順序時，由架構呼叫。|  
|[CFrameWndEx::PaneFromPoint](#panefrompoint)|傳回包含指定的點的停駐窗格。|  
|[CFrameWndEx::PreTranslateMessage](#pretranslatemessage)|處理特定的視窗訊息，再將它們分派。|  
|[CFrameWndEx::RecalcLayout](#recalclayout)|調整框架和其子視窗配置。|  
|[CFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|取消註冊 窗格，並從停駐的管理員在內部清單中移除它。|  
|[CFrameWndEx::SetDockState](#setdockstate)|還原儲存在登錄中的停駐狀態的停駐的配置。|  
|[CFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|設定 預覽列印框架視窗。|  
|[CFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|插入使用者定義的命令到工具列功能表。|  
|[CFrameWndEx::ShowFullScreen](#showfullscreen)|切換全螢幕和一般模式之間的主框架。|  
|[CFrameWndEx::ShowPane](#showpane)|顯示或隱藏指定的窗格。|  
|[CFrameWndEx::UpdateCaption](#updatecaption)|由架構呼叫以更新的視窗框架標題。|  
|[CFrameWndEx::WinHelp](#winhelp)|叫用其中一個`WinHelp`應用程式或內容的相關說明。|  
  
## <a name="example"></a>範例  
 下列範例示範如何從類別繼承，`CFrameWndEx`類別。 此範例說明方法簽章中的子類別，以及如何覆寫`OnShowPopupMenu`方法。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/cpp/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/cpp/cframewndex-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxframewndex.h  
  
##  <a name="activeitemrecalclayout"></a>  CFrameWndEx::ActiveItemRecalcLayout  
 調整 OLE 用戶端項目和框架工作區的配置。  
  
```  
void ActiveItemRecalcLayout();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="addpane"></a>  CFrameWndEx::AddPane  
 一種控制列向停駐的管理員。  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*pControlBar*  
 若要註冊控制狀態列窗格。  
  
 [in]*bTail*  
 如果您想要控制狀態列窗格新增至清單結尾，則為 TRUE。FALSE 否則。  
  
### <a name="return-value"></a>傳回值  
 如果已成功註冊控制列，則為 TRUEFALSE 否則。  
  
##  <a name="adjustdockinglayout"></a>  CFrameWndEx::AdjustDockingLayout  
 重新計算停駐在框架視窗的所有窗格的配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>參數  
 *hdwp*  
 結構，其中包含多個視窗的位置控制代碼。 。  
  
### <a name="remarks"></a>備註  
 初始化 hdwp 結構[BeginDeferWindowPos](https://msdn.microsoft.com/library/windows/desktop/ms632672)方法。  
  
##  <a name="delayupdateframemenu"></a>  CFrameWndEx::DelayUpdateFrameMenu  
 設定 [框架] 功能表和命令處理閒置時再更新。  
  
```  
virtual void DelayUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>參數  
 [in]*hMenuAlt*  
 替代的功能表的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="dockpane"></a>  CFrameWndEx::DockPane  
 在框架視窗停駐在指定的窗格。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*pBar*  
 若要停駐控制列指標。  
  
 [in]*nDockBarID*  
 停駐在框架視窗的側邊的識別碼。  
  
 [in]*lpRect*  
 常數的 Rect 結構，指定視窗的螢幕位置和大小的指標。  
  
### <a name="remarks"></a>備註  
 *NDockBarID*參數可以具有下列值之一：  
  
-   AFX_IDW_DOCKBAR_TOP  
  
-   AFX_IDW_DOCKBAR_BOTTOM  
  
-   AFX_IDW_DOCKBAR_LEFT  
  
-   AFX_IDW_DOCKBAR_RIGHT  
  
##  <a name="dockpaneleftof"></a>  CFrameWndEx::DockPaneLeftOf  
 指定的窗格停駐於另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>參數  
 [in]*pBar*  
 若要停駐窗格物件的指標。  
  
 [in]*pLeftOf*  
 要停駐窗格中所指定的左側窗格的指標*pBar*。  
  
### <a name="return-value"></a>傳回值  
 則為 TRUE *pBar*已成功停駐。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 此方法會採用所指定的工具列*pBar*參數，並在左邊工具列所指定的停駐*pLeftOf*參數。  
  
##  <a name="enableautohidepanes"></a>  CFrameWndEx::EnableAutoHidePanes  
 啟用自動隱藏模式窗格停駐到主框架視窗的指定端時。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in]*dwDockStyle*  
 指定要停駐窗格的主框架視窗的側邊。  
  
### <a name="return-value"></a>傳回值  
 如果一個列，則為 TRUE 窗格已成功停駐所指定的框架視窗側邊*dwDockStyle*，否則為 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 *dwDockStyle*可以有下列值之一：  
  
-   CBRS_ALIGN_TOP： 可讓被停駐在框架視窗的工作區頂端控制列。  
  
-   CBRS_ALIGN_BOTTOM： 可讓框架視窗的 [用戶端] 區域底部停駐控制列。  
  
-   CBRS_ALIGN_LEFT： 可讓工作區框架視窗的左側停駐控制列。  
  
-   CBRS_ALIGN_RIGHT： 可讓控制列固定到用戶端區域中，框架視窗的右側。  
  
##  <a name="enabledocking"></a>  Cframewndex:: Enabledocking  
 可讓停駐在框架視窗的窗格。  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in]*dwDockStyle*  
 指定主框架視窗停駐窗格列於其中一端。  
  
### <a name="return-value"></a>傳回值  
 如果一個列，則為 TRUE 窗格可以成功地停駐在指定的側邊。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 *DwDockStyle*參數可以具有下列值之一：  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="enablefullscreenmainmenu"></a>  CFrameWndEx::EnableFullScreenMainMenu  
 顯示或隱藏主功能表以全螢幕模式。  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>參數  
 [in]*bEnableMenu*  
 True 表示要顯示在主功能表中完整畫面模式中，FALSE 否則。  
  
##  <a name="enablefullscreenmode"></a>  CFrameWndEx::EnableFullScreenMode  
 可讓框架視窗的全螢幕模式。  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiFullScreenCmd*  
 啟用和停用的全螢幕模式的命令識別碼。  
  
### <a name="remarks"></a>備註  
 在全螢幕模式中，會隱藏所有停駐控制列、 工具列和功能表，並使用中的檢視會調整大小以佔用全螢幕。  
  
 當您啟用的全螢幕模式時，您必須指定啟用或停用的全螢幕模式的命令識別碼。 您可以呼叫`EnableFullScreenMode`從主要畫面格的`OnCreate`函式。 當框架視窗會切換至全螢幕模式時，此架構會建立浮動的工具列具有一個按鈕具有指定的命令 id。  
  
 如果您想要保留在螢幕上的主功能表中，呼叫[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)。  
  
##  <a name="enableloaddockstate"></a>  CFrameWndEx::EnableLoadDockState  
 啟用或停用的銜接狀態的載入。  
  
```  
void EnableLoadDockState(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bEnable*  
 若要停用的銜接狀態載入，FALSE 啟用的停駐狀態中，載入，則為 TRUE。  
  
##  <a name="enablepanemenu"></a>  CFrameWndEx::EnablePaneMenu  
 啟用或停用窗格功能表的自動處理。  
  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly=FALSE,  
    BOOL bViewMenuShowsToolbarsOnly=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bEnable*  
 若要啟用快顯功能表; 列控制項的自動處理，則為 TRUE若要停用快顯功能表列控制項的自動處理，則為 FALSE。  
  
 [in]*uiCustomizeCmd*  
 命令 ID**自訂**功能表項目。  
  
 [in]*strCustomizeLabel*  
 要顯示的標籤**自訂**功能表項目  
  
 [in]*uiViewToolbarsMenuEntryID*  
 開啟快顯功能表控制項列中的工具列功能表項目識別碼。  
  
 [in]*bContextMenuShowsToolbarsOnly*  
 如果為 TRUE，控制列的內容功能表會顯示只有工具列的清單。 如果為 FALSE，功能表會顯示工具列和停駐列的清單。  
  
 [in]*bViewMenuShowsToolbarsOnly*  
 如果為 TRUE，控制列功能表顯示工具列只有的清單。 如果為 FALSE，功能表會顯示工具列和停駐列的清單。  
  
##  <a name="getactivepopup"></a>  CFrameWndEx::GetActivePopup  
 讓指標回到目前顯示的快顯功能表。  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前顯示的快顯功能表中，指標否則為 NULL。  
  
##  <a name="getdefaultresid"></a>  CFrameWndEx::GetDefaultResId  
 傳回架構載入框架視窗時所指定的資源識別碼。  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用者指定的架構時載入框架視窗資源識別碼的值。 如果框架視窗並沒有功能表列，則為零。  
  
##  <a name="getdockingmanager"></a>  CFrameWndEx::GetDockingManager  
 擷取[CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)框架視窗物件。  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)。  
  
### <a name="remarks"></a>備註  
 框架視窗會建立並使用[CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)管理子視窗停駐的物件。  
  
##  <a name="getmenubar"></a>  CFrameWndEx::GetMenuBar  
 將指標傳回到附加在框架視窗的功能表列物件。  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 附加在框架視窗的功能表列物件指標。  
  
##  <a name="getpane"></a>  CFrameWndEx::GetPane  
 傳回具有指定的識別碼的窗格的指標  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in]*nID*  
 控制項 id。  
  
### <a name="return-value"></a>傳回值  
 [窗格]，擁有指定的識別碼的指標 如果沒有這類窗格存在，則為 NULL。  
  
##  <a name="getribbonbar"></a>  CFrameWndEx::GetRibbonBar  
 擷取框架的功能區列控制項。  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)框架。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettearoffbars"></a>  CFrameWndEx::GetTearOffBars  
 傳回分割狀態的窗格物件清單。  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考`CObList`包含分割狀態窗格物件的指標集合的物件。  
  
##  <a name="gettoolbarbuttontooltiptext"></a>  CFrameWndEx::GetToolbarButtonToolTipText  
 應用程式顯示的工具列按鈕的工具提示時，由架構呼叫。  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>參數  
 [in]*pButton*  
 在工具列按鈕的指標。  
  
 [in]*strTTText*  
 若要為按鈕顯示工具提示文字。  
  
### <a name="return-value"></a>傳回值  
 在顯示工具提示，其值為 TRUE。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法沒有任何作用。 如果您想要顯示的工具列按鈕的工具提示，請覆寫這個方法。  
  
##  <a name="insertpane"></a>  CFrameWndEx::InsertPane  
 將窗格插入控制列清單中，並向停駐的管理員註冊此窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pControlBar*  
 要插入控制列清單，以及向停駐的管理員註冊的控制列指標。  
  
 *pTarget*  
 控制列指標，在其前後插入窗格。  
  
 *bAfter*  
 如果您想要插入則為 TRUE *pControlBar*之後*pTarget*，則為 FALSE，否則為。  
  
### <a name="return-value"></a>傳回值  
 如果成功插入和註冊，FALSE 否則控制列，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 您必須使用註冊每個控制列[CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)參與停駐的配置。  
  
##  <a name="isfullscreen"></a>  CFrameWndEx::IsFullScreen  
 決定框架視窗是否為全螢幕模式。  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果框架視窗為全螢幕模式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫設定的全螢幕模式[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)方法。  
  
##  <a name="ismenubaravailable"></a>  CFrameWndEx::IsMenuBarAvailable  
 決定功能表列物件的指標是否有效。  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果框架視窗的功能表列;，則為 TRUE。否則為 FALSE。  
  
##  <a name="ispointneardocksite"></a>  CFrameWndEx::IsPointNearDockSite  
 判斷點是否位於未對齊的區域。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*點*  
 點的位置。  
  
 [out]*dwBarAlignment*  
 對齊點的位置。 請參閱 < 備註 > 一節的可能值的表格。  
  
 [out]*bOuterEdge*  
 如果該點位於接近框架框線;，則為 TRUE。如果該點位於工作區，則為 FALSE。  
  
### <a name="return-value"></a>傳回值  
 如果點位於對齊區域; 中，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為*dwBarAlignment*參數。  
  
 CBRS_ALIGN_TOP  
 靠上對齊。  
  
 CBRS_ALIGN_RIGHT  
 靠右對齊。  
  
 CBRS_ALIGN_BOTTOM  
 靠下對齊。  
  
 CBRS_ALIGN_LEFT  
 靠左對齊。  
  
##  <a name="isprintpreview"></a>  CFrameWndEx::IsPrintPreview  
 判斷框架視窗是否在列印預覽模式。  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>傳回值  
 如果框架視窗為預覽列印模式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="loadframe"></a>  CFrameWndEx::LoadFrame  
 建立框架視窗並載入其資源的建構完成之後會呼叫此方法。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*nIDResource*  
 用來載入畫面格的所有資源的資源識別碼。  
  
 [in]*dwDefaultStyle*  
 預設的框架視窗樣式。  
  
 [in]*pParentWnd*  
 在畫面格的父視窗的指標。  
  
 [in]*pContext*  
 指標[CCreateContext 結構](../../mfc/reference/ccreatecontext-structure.md)應用程式建立期間由架構的類別。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="negotiateborderspace"></a>  CFrameWndEx::NegotiateBorderSpace  
 實作 OLE 用戶端框線交涉。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>參數  
 [in]*nBorderCmd*  
 框線交涉命令。 請參閱 < 備註 > 一節，如需可能值。  
  
 [in、 out]*lpRectBorder*  
 框線的大小。  
  
### <a name="return-value"></a>傳回值  
 如果配置都必須重新計算;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為*nBorderCmd*參數。  
  
 *borderGet*  
 取得 OLE 用戶端的可用空間。  
  
 *borderRequest*  
 要求 OLE 用戶端空間。  
  
 *borderSet*  
 設定 OLE 用戶端空間。  
  
##  <a name="onactivate"></a>  CFrameWndEx::OnActivate  
 當使用者輸入會切換至或離開框架時，架構會呼叫這個方法。  
  
```  
afx_msg void OnActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>參數  
 [in]*nState*  
 框架是否作用中或非使用中。 請參閱 < 備註 > 一節的可能值的表格。  
  
 [in]*pWndOther*  
 正在切換與目前的使用者輸入的另一個視窗的指標。  
  
 [in]*bMinimized*  
 畫面格的最小化的狀態。 如果框架最小化，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為*nState*參數。  
  
 WA_ACTIVE  
 按下滑鼠以外的方法被選取框架。  
  
 WA_CLICKACTIVE  
 按下滑鼠會選取畫面格。  
  
 WA_INACTIVE  
 未選取的框架。  
  
##  <a name="onactivateapp"></a>  CFrameWndEx::OnActivateApp  
 當應用程式選取或取消選取此選項時，由架構呼叫。  
  
```  
afx_msg void OnActivateApp(
    BOOL bActive,  
    DWORD dwThreadID);
```  
  
### <a name="parameters"></a>參數  
 [in]*bActive*  
 如果已選取 應用程式;，則為 TRUE。如果未選取的應用程式，則為 FALSE。  
  
 [in]*dwThreadID*  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onchangevisualmanager"></a>  CFrameWndEx::OnChangeVisualManager  
 在畫面格的變更需要變更的視覺管理員時，由架構呼叫。  
  
```  
afx_msg LRESULT OnChangeVisualManager(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in]*wParam*  
 不使用這個參數。  
  
 [in]*lParam*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onclose"></a>  CFrameWndEx::OnClose  
 架構會呼叫這個方法，以關閉框架。  
  
```  
afx_msg void OnClose();
```  
  
### <a name="remarks"></a>備註  
 如果框架的預覽列印模式，它會傳送以關閉 預覽列印; Windows 訊息否則，如果框架裝載 OLE 用戶端，就會停用用戶端。  
  
##  <a name="onclosedockingpane"></a>  CFrameWndEx::OnCloseDockingPane  
 由架構呼叫，當使用者按一下**關閉**停駐窗格上的按鈕。  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pPane);
```  
  
### <a name="return-value"></a>傳回值  
 如果可以關閉停駐列，則為 TRUE。 FALSE 否則  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作。 如果您想要處理的停駐列隱藏，請覆寫這個方法。  
  
##  <a name="oncloseminiframe"></a>  CFrameWndEx::OnCloseMiniFrame  
 由架構呼叫，當使用者按一下**關閉**浮動迷你框架視窗上的按鈕。  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="return-value"></a>傳回值  
 如果可以關閉浮動迷你框架視窗，則為 TRUE。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 如果您想要處理的浮動迷你框架視窗隱藏，請覆寫這個方法。  
  
##  <a name="onclosepopupmenu"></a>  CFrameWndEx::OnClosePopupMenu  
 架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>參數  
 *pMenuPopup*  
 快顯功能表指標。  
  
### <a name="remarks"></a>備註  
 要關閉視窗時，架構就會傳送 WM_DESTROY 訊息。 覆寫這個方法，如果您想要處理的通知`CMFCPopupMenu`屬於框架視窗物件時`CMFCPopupMenu`物件正在處理 WM_DESTROY 訊息時關閉視窗，傳送的架構。  
  
##  <a name="oncmdmsg"></a>  CFrameWndEx::OnCmdMsg  
 分派命令訊息。  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>參數  
 [in]*nID*  
 命令 ID。  
  
 [in]*則 nCode*  
 命令訊息分類。  
  
 [in、 out]*pExtra*  
 命令物件的指標。  
  
 [in、 out]*pHandlerInfo*  
 命令處理常式結構指標。  
  
### <a name="return-value"></a>傳回值  
 如果已處理命令訊息，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="oncontexthelp"></a>  CFrameWndEx::OnContextHelp  
 由架構呼叫以顯示內容的相關說明。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="oncreate"></a>  CFrameWndEx::OnCreate  
 建立框架後，由架構呼叫。  
  
```  
afx_msg int OnCreate(LPCREATESTRUCT lpCreateStruct);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpCreateStruct*  
 指標[CREATESTRUCT 結構](../../mfc/reference/createstruct-structure.md)針對新的框架。  
  
### <a name="return-value"></a>傳回值  
 若要繼續畫面格建立; 0終結框架的-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondestroy"></a>  CFrameWndEx::OnDestroy  
 終結框架時，由架構呼叫。  
  
```  
afx_msg void OnDestroy();
```  
  
### <a name="remarks"></a>備註  
 快速鍵對應表和所有的 windows 會遭到銷毀。  
  
##  <a name="ondrawmenuimage"></a>  CFrameWndEx::OnDrawMenuImage  
 當應用程式繪製功能表項目相關聯的映像時，由架構呼叫。  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*pMenuButton*  
 指標，其影像正在呈現的功能表按鈕。  
  
 [in]*rectImage*  
 指標`Rect`結構，指定螢幕位置和大小的影像。  
  
### <a name="return-value"></a>傳回值  
 如果架構已成功轉譯的影像，則為 TRUEFALSE 否則。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，如果您想要自訂功能表項目所擁有的功能表列屬於映像呈現`CFrameWndEx`衍生物件。  
  
##  <a name="ondrawmenulogo"></a>  CFrameWndEx::OnDrawMenuLogo  
 由架構呼叫時`CMFCPopupMenu`物件處理 WM_PAINT 訊息。  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*pMenu*  
 功能表項目的指標。  
  
 [in]*rectLogo*  
 常數的參考`CRect`結構，指定螢幕位置和功能表標誌的大小。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式，如果您想要在快顯功能表屬於所擁有的功能表列上顯示標誌`CFrameWndEx`衍生物件。  
  
##  <a name="ondwmcompositionchanged"></a>  CFrameWndEx::OnDWMCompositionChanged  
 桌面視窗管理員 (DWM) 組合已啟用或停用時由架構呼叫。  
  
```  
afx_msg LRESULT OnDWMCompositionChanged(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 不使用這個參數。  
  
 [in]*lp*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onexitsizemove"></a>  CFrameWndEx::OnExitSizeMove  
 移動或調整大小，就會停止在畫面格時由架構呼叫。  
  
```  
LRESULT OnExitSizeMove(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 不使用這個參數。  
  
 [in]*lp*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ongetminmaxinfo"></a>  CFrameWndEx::OnGetMinMaxInfo  
 框架會調整大小以設定視窗維度限制時，由架構呼叫。  
  
```  
afx_msg void OnGetMinMaxInfo(MINMAXINFO FAR* lpMMI);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpMMI*  
 指標[MINMAXINFO](https://msdn.microsoft.com/library/windows/desktop/ms632605)結構。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onidleupdatecmdui"></a>  CFrameWndEx::OnIdleUpdateCmdUI  
 由架構呼叫以更新框架顯示命令的處理序閒置時。  
  
```  
afx_msg LRESULT OnIdleUpdateCmdUI(
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>參數  
 [in]*wParam*  
 不使用這個參數。  
  
 [in]*lParam*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttondown"></a>  CFrameWndEx::OnLButtonDown  
 當使用者按下滑鼠左的按鈕時，架構會呼叫這個方法。  
  
```  
afx_msg void OnLButtonDown(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in]*nFlags*  
 指出使用者是否按下輔助按鍵。 如需可能的值，請參閱 「 參數*wParam*中[WM_LBUTTONDOWN 通知](/windows/desktop/inputdev/wm-lbuttondown)。  
  
 [in]*點*  
 指定之 x 和指標的 y 座標，相對於視窗左上角。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttonup"></a>  CFrameWndEx::OnLButtonUp  
 當使用者放開滑鼠左的按鈕時，架構會呼叫這個方法。  
  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in]*nFlags*  
 指出使用者是否按下輔助按鍵。 如需可能的值，請參閱 「 參數*wParam*中[WM_LBUTTONUP 通知](/windows/desktop/inputdev/wm-lbuttonup)。  
  
 [in]*點*  
 指定之 x 和指標的 y 座標，相對於視窗左上角。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onmenubuttontoolhittest"></a>  CFrameWndEx::OnMenuButtonToolHitTest  
 由架構呼叫時`CMFCToolBarButton`物件處理 WM_NCHITTEST 訊息。  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>參數  
 [in]*pButton*  
 指向工具列按鈕。  
  
 [out]*pTI*  
 工具的資訊結構的指標。  
  
### <a name="return-value"></a>傳回值  
 如果應用程式會填滿，則為 TRUE *pTI*參數。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 如果您想要提供特定的功能表項目的工具提示資訊，請覆寫這個方法。  
  
##  <a name="onmenuchar"></a>  CFrameWndEx::OnMenuChar  
 會顯示功能表，並在使用者按下按鍵，並未對應到命令時，由架構呼叫。  
  
```  
afx_msg LRESULT OnMenuChar(
    UINT nChar,  
    UINT nFlags,  
    CMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [in]*nChar*  
 按下的按鍵的字元碼。  
  
 [in]*nFlags*  
 如果顯示的功能表為子功能表;，包含 MF_POPUP 旗標如果顯示的功能表控制項功能表，請包含 MF_SYSMENU 旗標。  
  
 [in]*pMenu*  
 功能表的指標。  
  
### <a name="return-value"></a>傳回值  
 高序位文字必須是下列值之一。  
  
 `0`  
 此架構應該忽略按鍵輸入。  
  
 `1`  
 此架構應該關閉功能表。  
  
 `2`  
 此架構應該選取其中一個功能表中顯示的項目。 低序位文字包含用來選取命令的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onmousemove"></a>  CFrameWndEx::OnMouseMove  
 當滑鼠指標移動時，架構會呼叫這個方法。  
  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in]*nFlags*  
 指出使用者是否按下輔助按鍵。 如需可能的值，請參閱 「 參數*wParam*中[WM_MOUSEMOVE 通知](/windows/desktop/inputdev/wm-mousemove)。  
  
 [in]*點*  
 指定的 x 和 y 座標相對於視窗左上角的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onmoveminiframe"></a>  CFrameWndEx::OnMoveMiniFrame  
 窗格視窗移動時，由架構呼叫。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in]*pFrame*  
 指標[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)窗格視窗。  
  
### <a name="return-value"></a>傳回值  
 如果未停駐窗格視窗;，則為 TRUE。如果已停駐窗格視窗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onncactivate"></a>  CFrameWndEx::OnNcActivate  
 必須重新繪製畫面格的非工作區，表示處於作用中狀態的變更時由架構呼叫。  
  
```  
afx_msg BOOL OnNcActivate(BOOL bActive);
```  
  
### <a name="parameters"></a>參數  
 [in]*bActive*  
 若為 true，則繪製作用中; 在畫面格繪製非作用中的框架，則為 FALSE。  
  
### <a name="return-value"></a>傳回值  
 若要繼續使用預設的處理; Nonzero若要防止在已停用非工作區 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onnccalcsize"></a>  CFrameWndEx::OnNcCalcSize  
 必須計算的大小和位置的工作區時，由架構呼叫。  
  
```  
afx_msg void OnNcCalcSize(
    BOOL bCalcValidRects,  
    NCCALCSIZE_PARAMS FAR* lpncsp);
```  
  
### <a name="parameters"></a>參數  
 [in]*bCalcValidRects*  
 當應用程式必須指定有效的用戶端區域; 時，則為 TRUE。否則為 FALSE。  
  
 [in]*lpncsp*  
 指標`NCCALCSIZE_PARAMS`結構，包含框架維度變更。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onnchittest"></a>  CFrameWndEx::OnNcHitTest  
 當滑鼠指標移，或按下或放開滑鼠按鈕時由架構呼叫。  
  
```  
afx_msg LRESULT OnNcHitTest(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in]*點*  
 螢幕座標中指標的位置。  
  
### <a name="return-value"></a>傳回值  
 指標叫用列舉的值。 如需可能值的清單，請參閱[WM_NCHITTEST 通知](/windows/desktop/inputdev/wm-nchittest)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onncmousemove"></a>  CFrameWndEx::OnNcMouseMove  
 當滑鼠指標移入非工作區時，由架構呼叫。  
  
```  
afx_msg void OnNcMouseMove(
    UINT nHitTest,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in]*nHitTest*  
 指標叫用列舉的值。 如需可能值的清單，請參閱[WM_NCHITTEST 通知](/windows/desktop/inputdev/wm-nchittest)。  
  
 [in]*點*  
 螢幕座標中指標的位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onncpaint"></a>  CFrameWndEx::OnNcPaint  
 必須繪製非工作區時，由架構呼叫。  
  
```  
afx_msg void OnNcPaint();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onpanecheck"></a>  CFrameWndEx::OnPaneCheck  
 由架構呼叫以控制的可見性 窗格。  
  
```  
afx_msg BOOL OnPaneCheck(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in]*nID*  
 窗格的控制項識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果已處理命令，則為 TRUE如果為 false，則繼續處理命令。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onpostpreviewframe"></a>  CFrameWndEx::OnPostPreviewFrame  
 當使用者變更的預覽列印模式時，由架構呼叫。  
  
```  
afx_msg LRESULT OnPostPreviewFrame(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in]*wParam*  
 不使用這個參數。  
  
 [in]*lParam*  
 預覽列印模式; 在畫面格時，則為 TRUE。關閉預覽列印模式時，則為 FALSE。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onpowerbroadcast"></a>  CFrameWndEx::OnPowerBroadcast  
 電源管理事件發生時，由架構呼叫。  
  
```  
afx_msg LRESULT OnPowerBroadcast(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 電源管理事件。 如需可能值的清單，請參閱[WM_POWERBROADCAST 訊息](/windows/desktop/Power/wm-powerbroadcast)。  
  
 [in]*lp*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 因為呼叫預設視窗程序。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsetmenu"></a>  CFrameWndEx::OnSetMenu  
 由架構呼叫以取代框架視窗功能表。  
  
```  
afx_msg LRESULT OnSetMenu(
    WPARAM wp,  
    LPARAM lp);  
  
BOOL OnSetMenu(HMENU hmenu);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 新的框架視窗功能表的控制代碼。  
  
 [in]*lp*  
 新的 [視窗] 功能表的控制代碼。  
  
 [in]*hmenu*  
 新的框架視窗功能表的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 LRESULT 會呼叫預設視窗程序的結果。  
  
 BOOL，已處理事件; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsetpreviewmode"></a>  CFrameWndEx::OnSetPreviewMode  
 由架構呼叫以設定框架的預覽列印模式。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [in]*bPreview*  
 若要啟用列印預覽;，則為 TRUE若要停用預覽列印，則為 FALSE。  
  
 [in]*pState*  
 指標`CPrintPreviewState`框架狀態結構。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsettext"></a>  CFrameWndEx::OnSetText  
 由架構呼叫以設定視窗的文字。  
  
```  
afx_msg LRESULT OnSetText(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in]*wParam*  
 不使用這個參數。  
  
 [in]*lParam*  
 視窗文字指標。  
  
### <a name="return-value"></a>傳回值  
 從呼叫傳回值[DefWindowProc](/windows/desktop/api/winuser/nf-winuser-defwindowproca)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onshowcustomizepane"></a>  CFrameWndEx::OnShowCustomizePane  
 顯示時由架構呼叫`QuickCustomizePane`。  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMenuPane*  
 快速的指標自訂窗格。  
  
 [in]*uiToolbarID*  
 若要自訂工具列控制項識別碼。  
  
### <a name="return-value"></a>傳回值  
 這個方法一定會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 快速自訂功能表會顯示當您按一下工具列的自訂按鈕的快顯功能表  
  
##  <a name="onshowpanes"></a>  CFrameWndEx::OnShowPanes  
 由架構呼叫以顯示或隱藏窗格。  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in]*bShow*  
 如果應用程式會顯示窗格中，則為 TRUEFALSE 否則。  
  
### <a name="return-value"></a>傳回值  
 這個方法一定會傳回 FALSE。  
  
### <a name="remarks"></a>備註  
 預設實作會顯示窗格如果*bShow*為 TRUE，而且會隱藏窗格或當*bShow*是 FALSE 且窗格會顯示。  
  
 如果預設實作會隱藏窗格*bShow*為 TRUE，而且窗格是可見或當*bShow*是 FALSE，且會隱藏窗格。  
  
 覆寫此方法在衍生類別時，架構會顯示或隱藏窗格執行自訂程式碼中。  
  
##  <a name="onshowpopupmenu"></a>  CFrameWndEx::OnShowPopupMenu  
 顯示快顯功能表時，由架構呼叫。  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMenu*  
 快顯功能表指標。  
  
### <a name="return-value"></a>傳回值  
 如果快顯功能表會顯示;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 覆寫此方法在衍生類別時，架構會顯示快顯功能表執行自訂程式碼中。 例如，您可以覆寫這個方法，以變更背景色彩的快顯功能表中的命令。  
  
##  <a name="onsize"></a>  CFrameWndEx::OnSize  
 畫面格的大小變更後，由架構呼叫。  
  
```  
afx_msg void OnSize(
    UINT nType,  
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>參數  
 [in]*n*  
 調整大小的類型。 如需可能的值，請參閱 「 參數*wParam*中[WM_SIZE 通知](/windows/desktop/winmsg/wm-size)。  
  
 [in]*cx*  
 新框架寬度的像素為單位。  
  
 [in]*cy*  
 新的高度，單位為像素框架。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsizing"></a>  CFrameWndEx::OnSizing  
 當使用者調整框架，由架構呼叫。  
  
```  
afx_msg void OnSizing(
    UINT fwSide,  
    LPRECT pRect);
```  
  
### <a name="parameters"></a>參數  
 [in]*fwSide*  
 移動的框架邊緣。 請參閱參數*wParam*中[WM_SIZING 通知](/windows/desktop/winmsg/wm-sizing)。  
  
 [in、 out]*pRect*  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)或是[RECT](../../mfc/reference/rect-structure1.md)結構，其中包含 畫面格的座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsyscolorchange"></a>  CFrameWndEx::OnSysColorChange  
 當系統色彩變更時由架構呼叫。  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="ontearoffmenu"></a>  CFrameWndEx::OnTearOffMenu  
 當應用程式就會顯示有 tear-off 列的功能表時，由架構呼叫。  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMenuPopup*  
 快顯功能表指標。  
  
 [in]*pBar*  
 Tear-off 列指標。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用快顯功能表與 tear-off 列，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 覆寫此方法在衍生類別時，架構會顯示一種控制列，執行自訂程式碼中。  
  
 預設實作不做任何動作，並傳回 TRUE。  
  
##  <a name="ontoolbarcontextmenu"></a>  CFrameWndEx::OnToolbarContextMenu  
 由架構呼叫以建立工具列的快顯功能表。  
  
```  
afx_msg LRESULT OnToolbarContextMenu(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 不使用這個參數。  
  
 [in]*lp*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律會傳回 1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ontoolbarcreatenew"></a>  CFrameWndEx::OnToolbarCreateNew  
 架構會呼叫這個方法，以建立新的工具列。  
  
```  
afx_msg LRESULT OnToolbarCreateNew(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]*wp*  
 不使用這個參數。  
  
 [in]*lp*  
 在工具列的標題列文字指標。  
  
### <a name="return-value"></a>傳回值  
 新的工具列中，指標如果未建立工具列，為 NULL。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ontoolbardelete"></a>  CFrameWndEx::OnToolbarDelete  
 刪除工具列時由架構呼叫。  
  
```  
afx_msg LRESULT OnToolbarDelete(
    WPARAM, 
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]  
 不使用這個參數。  
  
 [in]*lp*  
 工具列的指標。  
  
### <a name="return-value"></a>傳回值  
 如果工具列已刪除，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdateframemenu"></a>  CFrameWndEx::OnUpdateFrameMenu  
 由架構呼叫以設定框架功能表。  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>參數  
 [in]*hMenuAlt*  
 替代的功能表的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdateframetitle"></a>  CFrameWndEx::OnUpdateFrameTitle  
 架構會呼叫這個方法，以更新框架視窗的標題列。  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>參數  
 [in]*bAddToTitle*  
 若要加入至框架視窗標題列; 主動式文件標題，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatepanemenu"></a>  CFrameWndEx::OnUpdatePaneMenu  
 由架構呼叫以更新 [窗格] 功能表。  
  
```  
afx_msg void OnUpdatePaneMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 [in]*pCmdUI*  
 窗格使用者介面物件的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onwindowposchanged"></a>  CFrameWndEx::OnWindowPosChanged  
 由於視窗管理方法的呼叫變更畫面格大小、 位置或疊置順序時，由架構呼叫。  
  
```  
afx_msg void OnWindowPosChanged(WINDOWPOS FAR* lpwndpos);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpwndpos*  
 指標[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)結構，其中包含新的大小和位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="panefrompoint"></a>  CFrameWndEx::PaneFromPoint  
 搜尋每個窗格，針對給定的點。  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*點*  
 若要檢查點的螢幕座標。  
  
 [in]*nSensitivity*  
 搜尋點時，請展開此數量的每個控制列的週框矩形。  
  
 [in]*bExactBar*  
 TRUE 表示忽略*nSensitivity*參數; 否則為 FALSE。  
  
 [in]*pRTCBarType*  
 如果不是 NULL，則該方法會搜尋只指定型別的控制列。  
  
 [out]*dwAlignment*  
 如果成功，則此參數會包含最接近指定點的控制列的側邊。 否則，此參數未初始化。  
  
### <a name="return-value"></a>傳回值  
 包含的控制列指標*點*;如果找不到任何控制項，則為 NULL。  
  
### <a name="remarks"></a>備註  
 這個方法會搜尋您的應用程式中的所有控制列*點*。  
  
 使用*nSensitivity*來增加搜尋區域大小。 使用*pRTCBarType*來限制該方法會搜尋的控制列的類型。  
  
##  <a name="pretranslatemessage"></a>  CFrameWndEx::PreTranslateMessage  
 處理特定的視窗訊息，再將它們分派。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMsg*  
 指標[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 非為零，如果訊息已處理，因此不應該分派;0，表示未處理訊息，並且應該分派。  
  
### <a name="remarks"></a>備註  
  
##  <a name="recalclayout"></a>  CFrameWndEx::RecalcLayout  
 調整框架和其子視窗配置。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bNotify*  
 指定是否要通知 OLE 用戶端項目與變更相關的版面配置。  
  
### <a name="remarks"></a>備註  
 框架視窗的大小已變更時，或控制列的顯示或隱藏時，會呼叫這個方法。  
  
##  <a name="removepanefromdockmanager"></a>  CFrameWndEx::RemovePaneFromDockManager  
 取消註冊 窗格，並移除停駐的管理員。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>參數  
 [in]*pControlBar*  
 若要移除控制狀態列窗格指標。  
  
 [in]*bDestroy*  
 要移除之後, 終結控制列，則為 TRUEFALSE 否則。  
  
 [in]*bAdjustLayout*  
 若要調整停駐的配置;，則為 TRUEFALSE 否則。  
  
 [in]*bAutoHide*  
 如果控制列為自動隱藏模式，則為 TRUEFALSE 否則。  
  
 [in]*pBarReplacement*  
 指標，會取代 [移除] 窗格的窗格。  
  
### <a name="remarks"></a>備註  
 若要移除的框架視窗停駐的配置中的一種控制列中使用這個方法。  
  
 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)處理的控制列配置。 您必須向停駐的管理員註冊每個控制列，使用[CFrameWndEx::AddPane](#addpane)方法或[CFrameWndEx::InsertPane](#insertpane)方法。  
  
##  <a name="setdockstate"></a>  CFrameWndEx::SetDockState  
 還原儲存在登錄中的停駐狀態的停駐的配置。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>參數  
 *state*  
 停駐的狀態。 這個參數已忽略。  
  
##  <a name="setprintpreviewframe"></a>  CFrameWndEx::SetPrintPreviewFrame  
 設定 預覽列印框架視窗。  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in]*pWnd*  
 預覽列印框架視窗的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setuptoolbarmenu"></a>  CFrameWndEx::SetupToolbarMenu  
 插入使用者定義的命令到工具列功能表。  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>參數  
 [in]*功能表*  
 A`CMenu`要修改的物件。  
  
 [in]*uiViewUserToolbarCmdFirst*  
 第一個使用者定義的命令。  
  
 [in]*uiViewUserToolbarCmdLast*  
 最後一個使用者定義的命令。  
  
### <a name="remarks"></a>備註  
 架構會儲存在清單中的使用者定義的命令。 使用*uiViewUserToolbarCmdFirst*並*uiViewUserToolbarCmdList*來指定要插入的命令的索引。  
  
##  <a name="showfullscreen"></a>  CFrameWndEx::ShowFullScreen  
 切換全螢幕模式與一般模式之間的主框架。  
  
```  
void ShowFullScreen();
```  
  
##  <a name="showpane"></a>  CFrameWndEx::ShowPane  
 顯示或隱藏指定的窗格。  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in]*pBar*  
 若要顯示或隱藏的控制列指標。  
  
 [in]*bShow*  
 如果為 TRUE，則應用程式會顯示控制列。 否則，應用程式會隱藏控制列。  
  
 [in]*bDelay*  
 如果為 TRUE，會延遲的停駐配置的調整之前，架構會呼叫[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)。 否則，立即重新計算停駐的配置。  
  
 [in]*bActivate*  
 如果為 TRUE，讓控制列作用中。 否則，顯示控制列中非作用中狀態。  
  
##  <a name="updatecaption"></a>  CFrameWndEx::UpdateCaption  
 由架構呼叫以更新的視窗框架標題。  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="winhelp"></a>  CFrameWndEx::WinHelp  
 叫用 WinHelp 應用程式或內容相關說明。  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>參數  
 *dwData*  
 資料相依於*nCmd*參數。 如需可能值的清單，請參閱[WinHelp](/windows/desktop/api/winuser/nf-winuser-winhelpa)。  
  
 *nCmd*  
 [說明] 命令。 如需可能值的清單，請參閱[WinHelp](/windows/desktop/api/winuser/nf-winuser-winhelpa)。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)
