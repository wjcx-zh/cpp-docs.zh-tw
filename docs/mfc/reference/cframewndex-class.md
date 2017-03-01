---
title: "Cframewndex 則是類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFrameWndEx
dev_langs:
- C++
helpviewer_keywords:
- CFrameWndEx class
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
caps.latest.revision: 39
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b2106c3067a0164395eddab0e8b156728697d5bb
ms.lasthandoff: 02/24/2017

---
# <a name="cframewndex-class"></a>Cframewndex 則是類別
實作 Windows 單一文件介面 (SDI) 重疊或快顯框架視窗的功能，並提供管理視窗的成員。 它會擴充[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|調整 OLE 用戶端項目和框架的用戶端區域的配置。|  
|`CFrameWndEx::AddDockSite`|不使用這個方法。|  
|[CFrameWndEx::AddPane](#addpane)|控制列向停駐的管理員。|  
|[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|重新計算所有窗格的停駐在框架視窗的配置。|  
|[CFrameWndEx::DelayUpdateFrameMenu](#delayupdateframemenu)|設定 [框架] 功能表，然後更新命令處理閒置時。|  
|[CFrameWndEx::DockPane](#dockpane)|框架視窗停駐於指定的窗格。|  
|[CFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐在另一個窗格的左邊。|  
|[CFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|啟動指定的側邊的主框架視窗停駐窗格的 自動隱藏模式。|  
|[CFrameWndEx::EnableDocking](#enabledocking)|可讓屬於框架視窗窗格的停駐。|  
|[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|顯示或隱藏主功能表以全螢幕模式。|  
|[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|可讓框架視窗的全螢幕模式。|  
|[CFrameWndEx::EnableLoadDockState](#enableloaddockstate)|啟用或停用的銜接狀態的載入。|  
|[CFrameWndEx::EnablePaneMenu](#enablepanemenu)|啟用或停用 [窗格] 功能表的自動處理。|  
|[CFrameWndEx::GetActivePopup](#getactivepopup)|傳回目前所顯示的快顯功能表上的指標。|  
|[CFrameWndEx::GetDefaultResId](#getdefaultresid)|傳回架構載入框架視窗時所指定的資源識別碼。|  
|[CFrameWndEx::GetDockingManager](#getdockingmanager)|擷取[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)框架視窗物件。|  
|[CFrameWndEx::GetMenuBar](#getmenubar)|將指標傳回到附加在框架視窗的功能表列物件。|  
|[CFrameWndEx::GetPane](#getpane)|將指標傳回至窗格中具有指定的識別碼。|  
|[CFrameWndEx::GetRibbonBar](#getribbonbar)|擷取框架的功能區列控制項。|  
|[CFrameWndEx::GetTearOffBars](#gettearoffbars)|傳回分割狀態的窗格物件清單。|  
|[CFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|當應用程式顯示的工具列按鈕的工具提示時，由架構呼叫。|  
|[CFrameWndEx::InsertPane](#insertpane)|向停駐的管理員 窗格。|  
|[CFrameWndEx::IsFullScreen](#isfullscreen)|判斷是否在全螢幕模式中的框架視窗。|  
|[CFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|判斷是否為有效的功能表列物件的指標。|  
|[CFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|指出是否對齊區域位於點。|  
|[CFrameWndEx::IsPrintPreview](#isprintpreview)|指出是否在預覽列印模式中的框架視窗。|  
|[CFrameWndEx::LoadFrame](#loadframe)|建立框架視窗並載入其資源的建構完成之後會呼叫這個方法。|  
|[CFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|實作 OLE 用戶端框線交涉。|  
|[CFrameWndEx::OnActivate](#onactivate)|當使用者輸入切換至或離開框架，架構會呼叫這個方法。|  
|[CFrameWndEx::OnActivateApp](#onactivateapp)|當應用程式選取或取消選取此選項時，由架構呼叫。|  
|[CFrameWndEx::OnChangeVisualManager](#onchangevisualmanager)|畫面格的變更需要變更視覺管理員時，由架構呼叫。|  
|[CFrameWndEx::OnClose](#onclose)|架構會呼叫這個方法，以關閉框架。|  
|[CFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|當使用者按一下時，由框架呼叫**關閉**停駐窗格上的按鈕。|  
|[CFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|當使用者按一下時，由框架呼叫**關閉**浮動的迷你框架視窗上的按鈕。|  
|[CFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。|  
|[CFrameWndEx::OnCmdMsg](#oncmdmsg)|分派命令訊息。|  
|[CFrameWndEx::OnContextHelp](#oncontexthelp)|由架構呼叫，以顯示內容相關說明。|  
|[CFrameWndEx::OnCreate](#oncreate)|架構建立框架之後呼叫。|  
|[CFrameWndEx::OnDestroy](#ondestroy)|終結框架時，由架構呼叫。|  
|[CFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|當應用程式繪製功能表項目相關聯的映像時，由架構呼叫。|  
|[CFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|由架構呼叫時`CMFCPopupMenu`物件處理程序[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)訊息。|  
|[CFrameWndEx::OnDWMCompositionChanged](#ondwmcompositionchanged)|已啟用或停用桌面視窗管理員 (DWM) 組合，由架構呼叫。|  
|[CFrameWndEx::OnExitSizeMove](#onexitsizemove)|當框架停止移動或調整大小，由架構呼叫。|  
|[CFrameWndEx::OnGetMinMaxInfo](#ongetminmaxinfo)|框架的設定視窗維度限制大小時，由架構呼叫。|  
|[CFrameWndEx::OnIdleUpdateCmdUI](#onidleupdatecmdui)|更新框架顯示命令的處理序閒置時架構呼叫。|  
|[CFrameWndEx::OnLButtonDown](#onlbuttondown)|當使用者按下滑鼠左鍵時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnLButtonUp](#onlbuttonup)|當使用者放開滑鼠左鍵時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|由架構呼叫時`CMFCToolBarButton`物件處理程序`WM_NCHITTEST`訊息。|  
|[CFrameWndEx::OnMenuChar](#onmenuchar)|架構會顯示功能表與使用者按下命令未對應的索引鍵時呼叫。|  
|[CFrameWndEx::OnMouseMove](#onmousemove)|移動指標時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|窗格視窗移動時，由架構呼叫。|  
|[CFrameWndEx::OnNcActivate](#onncactivate)|必須重繪框架的非工作區，以表示作用中狀態變更時，由架構呼叫。|  
|[CFrameWndEx::OnNcCalcSize](#onnccalcsize)|必須計算的大小和位置的工作區時，由架構呼叫。|  
|[CFrameWndEx::OnNcHitTest](#onnchittest)|移動指標時，或按下或放開滑鼠按鈕時，由架構呼叫。|  
|[CFrameWndEx::OnNcMouseMove](#onncmousemove)|在非工作區中移動指標時，由架構呼叫。|  
|[CFrameWndEx::OnNcPaint](#onncpaint)|架構必須繪製非工作區時呼叫。|  
|[CFrameWndEx::OnPaneCheck](#onpanecheck)|若要控制可見性 窗格的架構呼叫。|  
|[CFrameWndEx::OnPostPreviewFrame](#onpostpreviewframe)|當使用者變更預覽列印模式時，由架構呼叫。|  
|[CFrameWndEx::OnPowerBroadcast](#onpowerbroadcast)|電源管理事件發生時，由架構呼叫。|  
|[CFrameWndEx::OnSetMenu](#onsetmenu)|若要取代的框架視窗功能表架構呼叫。|  
|[CFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|若要設定框架預覽列印模式架構呼叫。|  
|[CFrameWndEx::OnSetText](#onsettext)|若要設定視窗的文字架構呼叫。|  
|[CFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|您可以快速自訂時，由框架呼叫窗格已啟用。|  
|[CFrameWndEx::OnShowPanes](#onshowpanes)|若要顯示或隱藏窗格架構呼叫。|  
|[CFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|啟用快顯功能表時，由架構呼叫。|  
|[CFrameWndEx::OnSize](#onsize)|框架的大小變更之後，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSizing](#onsizing)|當使用者調整框架，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSysColorChange](#onsyscolorchange)|當系統色彩變更時，由架構呼叫。|  
|[CFrameWndEx::OnTearOffMenu](#ontearoffmenu)|啟用具有撕列功能表時，由架構呼叫。|  
|[CFrameWndEx::OnToolbarContextMenu](#ontoolbarcontextmenu)|建立工具列的內容功能表架構呼叫。|  
|[CFrameWndEx::OnToolbarCreateNew](#ontoolbarcreatenew)|架構會呼叫這個方法，以建立新的工具列。|  
|[CFrameWndEx::OnToolbarDelete](#ontoolbardelete)|刪除工具列時，由架構呼叫。|  
|[CFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|若要設定框架功能表架構呼叫。|  
|[CFrameWndEx::OnUpdateFrameTitle](#onupdateframetitle)|架構會呼叫這個方法，以更新框架視窗的標題列。|  
|[CFrameWndEx::OnUpdatePaneMenu](#onupdatepanemenu)|若要更新窗格功能表架構呼叫。|  
|[CFrameWndEx::OnWindowPosChanged](#onwindowposchanged)|因為視窗管理方法呼叫而變更的框架大小、 位置或圖層順序時，由架構呼叫。|  
|[CFrameWndEx::PaneFromPoint](#panefrompoint)|傳回包含指定的點的停駐窗格。|  
|[CFrameWndEx::PreTranslateMessage](#pretranslatemessage)|再分派這些處理特定視窗訊息。|  
|[CFrameWndEx::RecalcLayout](#recalclayout)|調整框架和其子視窗的配置。|  
|[CFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|取消註冊 窗格，並將它從 內部 清單中停駐管理員移除。|  
|[CFrameWndEx::SetDockState](#setdockstate)|還原停駐配置到停駐狀態儲存在登錄中。|  
|[CFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|設定預覽列印框架視窗。|  
|[CFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|插入使用者定義的命令於工具列功能表。|  
|[CFrameWndEx::ShowFullScreen](#showfullscreen)|切換全螢幕與標準模式之間的主框架。|  
|[CFrameWndEx::ShowPane](#showpane)|顯示或隱藏指定的窗格。|  
|[CFrameWndEx::UpdateCaption](#updatecaption)|若要更新的視窗框架標題架構呼叫。|  
|[CFrameWndEx::WinHelp](#winhelp)|叫用 `WinHelp`應用程式或內容的相關說明。|  
  
## <a name="example"></a>範例  
 下列範例示範如何從類別繼承，`CFrameWndEx`類別。 此範例說明子類別，而方法簽章如何覆寫`OnShowPopupMenu`方法。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&3;](../../mfc/reference/codesnippet/cpp/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad #&4;](../../mfc/reference/codesnippet/cpp/cframewndex-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [Cframewndex 則是](../../mfc/reference/cframewndex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxframewndex.h  
  
##  <a name="a-nameactiveitemrecalclayouta--cframewndexactiveitemrecalclayout"></a><a name="activeitemrecalclayout"></a>CFrameWndEx::ActiveItemRecalcLayout  
 調整 OLE 用戶端項目和框架的用戶端區域的配置。  
  
```  
void ActiveItemRecalcLayout();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddpanea--cframewndexaddpane"></a><a name="addpane"></a>CFrameWndEx::AddPane  
 控制列向停駐的管理員。  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 若要註冊控制項窗格。  
  
 [in] `bTail`  
 `TRUE`如果您想要新增至清單結尾的控制列窗格`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功註冊控制列。，`FALSE`否則。  
  
##  <a name="a-nameadjustdockinglayouta--cframewndexadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CFrameWndEx::AdjustDockingLayout  
 重新計算所有窗格的停駐在框架視窗的配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>參數  
 `hdwp`  
 結構，包含位置的多個視窗控制代碼。 。  
  
### <a name="remarks"></a>備註  
 初始化 hdwp 結構[BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672)方法。  
  
##  <a name="a-namedelayupdateframemenua--cframewndexdelayupdateframemenu"></a><a name="delayupdateframemenu"></a>CFrameWndEx::DelayUpdateFrameMenu  
 設定 [框架] 功能表，然後更新命令處理閒置時。  
  
```  
virtual void DelayUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenuAlt`  
 替代的功能表上的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedockpanea--cframewndexdockpane"></a><a name="dockpane"></a>CFrameWndEx::DockPane  
 框架視窗停駐於指定的窗格。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要停駐控制列指標。  
  
 [in] `nDockBarID`  
 框架視窗停駐邊的識別碼。  
  
 [in] `lpRect`  
 常數的 Rect 結構，指定視窗的螢幕位置和大小的指標。  
  
### <a name="remarks"></a>備註  
 `nDockBarID`參數可能會有下列值之一︰  
  
-   AFX_IDW_DOCKBAR_TOP  
  
-   AFX_IDW_DOCKBAR_BOTTOM  
  
-   AFX_IDW_DOCKBAR_LEFT  
  
-   AFX_IDW_DOCKBAR_RIGHT  
  
##  <a name="a-namedockpaneleftofa--cframewndexdockpaneleftof"></a><a name="dockpaneleftof"></a>CFrameWndEx::DockPaneLeftOf  
 指定的窗格停駐於另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要停駐窗格物件的指標。  
  
 [in] `pLeftOf`  
 要停駐窗格中所指定的左窗格的指標`pBar`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`pBar`停駐成功。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 此方法會接受所指定的工具列`pBar`參數，並在工具列的左邊所指定的停駐`pLeftOf`參數。  
  
##  <a name="a-nameenableautohidepanesa--cframewndexenableautohidepanes"></a><a name="enableautohidepanes"></a>CFrameWndEx::EnableAutoHidePanes  
 啟用自動隱藏模式窗格時它停駐於主框架視窗的指定端。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定要停駐窗格的主框架視窗的側邊。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果列所指定的框架視窗端成功停駐窗格`dwDockStyle`，`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 `dwDockStyle`可以有下列值之一︰  
  
-   CBRS_ALIGN_TOP︰ 可讓框架視窗的工作區頂端停駐控制列。  
  
-   CBRS_ALIGN_BOTTOM︰ 可讓工作區框架視窗的底部停駐控制列。  
  
-   CBRS_ALIGN_LEFT︰ 可讓框架視窗的工作區左邊算起停駐控制列。  
  
-   CBRS_ALIGN_RIGHT︰ 可讓框架視窗的工作區右側停駐控制列。  
  
##  <a name="a-nameenabledockinga--cframewndexenabledocking"></a><a name="enabledocking"></a>CFrameWndEx::EnableDocking  
 可讓框架視窗窗格的停駐。  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定主框架視窗停駐窗格列於其中一端。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果列窗格可以順利停駐在指定的側邊。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 `dwDockStyle`參數可能會有下列值之一︰  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="a-nameenablefullscreenmainmenua--cframewndexenablefullscreenmainmenu"></a><a name="enablefullscreenmainmenu"></a>CFrameWndEx::EnableFullScreenMainMenu  
 顯示或隱藏主功能表以全螢幕模式。  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnableMenu`  
 `TRUE`若要在全螢幕模式中，顯示在主功能表`FALSE`否則。  
  
##  <a name="a-nameenablefullscreenmodea--cframewndexenablefullscreenmode"></a><a name="enablefullscreenmode"></a>CFrameWndEx::EnableFullScreenMode  
 可讓框架視窗的全螢幕模式。  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiFullScreenCmd`  
 啟用和停用全螢幕模式的命令識別碼。  
  
### <a name="remarks"></a>備註  
 在全螢幕模式中，會隱藏所有停駐控制列、 工具列和功能表，並使用中的檢視會調整大小以佔用全螢幕。  
  
 當您啟用全螢幕模式時，您必須指定啟用或停用全螢幕模式的命令識別碼。 您可以呼叫`EnableFullScreenMode`從主框架的`OnCreate`函式。 當框架視窗會切換至全螢幕模式時，此架構會建立浮動的工具列具有一個按鈕具有指定的命令識別碼。  
  
 如果您想要保留在螢幕上的主功能表上，呼叫[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)。  
  
##  <a name="a-nameenableloaddockstatea--cframewndexenableloaddockstate"></a><a name="enableloaddockstate"></a>CFrameWndEx::EnableLoadDockState  
 啟用或停用的銜接狀態的載入。  
  
```  
void EnableLoadDockState(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用的銜接狀態中，載入`FALSE`停用的銜接狀態的載入。  
  
##  <a name="a-nameenablepanemenua--cframewndexenablepanemenu"></a><a name="enablepanemenu"></a>CFrameWndEx::EnablePaneMenu  
 啟用或停用 [窗格] 功能表的自動處理。  
  
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
 [in] `bEnable`  
 `TRUE`若要啟用快顯功能表; 列控制項的自動處理`FALSE`停用快顯功能表列控制項的自動處理。  
  
 [in] `uiCustomizeCmd`  
 命令 ID 的**自訂**功能表項目。  
  
 [in] `strCustomizeLabel`  
 要顯示的標籤**自訂**功能表項目  
  
 [in] `uiViewToolbarsMenuEntryID`  
 在控制列中開啟快顯功能表的工具列功能表項目識別碼。  
  
 [in] `bContextMenuShowsToolbarsOnly`  
 如果`TRUE`，內容功能表列控制項顯示的工具列只有清單。 如果`FALSE`，功能表就會顯示的工具列和停駐列清單。  
  
 [in] `bViewMenuShowsToolbarsOnly`  
 如果`TRUE`，控制列功能表顯示的工具列只有清單。 如果`FALSE`，功能表就會顯示的工具列和停駐列清單。  
  
##  <a name="a-namegetactivepopupa--cframewndexgetactivepopup"></a><a name="getactivepopup"></a>CFrameWndEx::GetActivePopup  
 傳回目前所顯示的快顯功能表上的指標。  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 到目前顯示的快顯功能表中，指標否則`NULL`。  
  
##  <a name="a-namegetdefaultresida--cframewndexgetdefaultresid"></a><a name="getdefaultresid"></a>CFrameWndEx::GetDefaultResId  
 傳回架構載入框架視窗時所指定的資源識別碼。  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 架構框架視窗中載入時指定的使用者資源識別碼值。 如果框架視窗並沒有功能表列，則為零。  
  
##  <a name="a-namegetdockingmanagera--cframewndexgetdockingmanager"></a><a name="getdockingmanager"></a>CFrameWndEx::GetDockingManager  
 擷取[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)框架視窗物件。  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)。  
  
### <a name="remarks"></a>備註  
 建立框架視窗，並使用[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)物件來管理子視窗停駐。  
  
##  <a name="a-namegetmenubara--cframewndexgetmenubar"></a><a name="getmenubar"></a>CFrameWndEx::GetMenuBar  
 將指標傳回到附加在框架視窗的功能表列物件。  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 附加至框架視窗的功能表列物件指標。  
  
##  <a name="a-namegetpanea--cframewndexgetpane"></a><a name="getpane"></a>CFrameWndEx::GetPane  
 將指標傳回至窗格中具有指定的識別碼。  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 控制項 id。  
  
### <a name="return-value"></a>傳回值  
 [窗格]，擁有指定的識別碼的指標 `NULL`如果存在這類 窗格。  
  
##  <a name="a-namegetribbonbara--cframewndexgetribbonbar"></a><a name="getribbonbar"></a>CFrameWndEx::GetRibbonBar  
 擷取框架的功能區列控制項。  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)框架。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettearoffbarsa--cframewndexgettearoffbars"></a><a name="gettearoffbars"></a>CFrameWndEx::GetTearOffBars  
 傳回分割狀態的窗格物件清單。  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考`CObList`包含撕狀態窗格物件的指標集合的物件。  
  
##  <a name="a-namegettoolbarbuttontooltiptexta--cframewndexgettoolbarbuttontooltiptext"></a><a name="gettoolbarbuttontooltiptext"></a>CFrameWndEx::GetToolbarButtonToolTipText  
 當應用程式顯示的工具列按鈕的工具提示時，由架構呼叫。  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指標，工具列按鈕。  
  
 [in] `strTTText`  
 若要為按鈕顯示工具提示文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已顯示工具提示。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法沒有作用。 如果您想要顯示工具列按鈕的工具提示，請覆寫這個方法。  
  
##  <a name="a-nameinsertpanea--cframewndexinsertpane"></a><a name="insertpane"></a>CFrameWndEx::InsertPane  
 將窗格插入控制列清單中，並向停駐的管理員註冊此窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pControlBar`  
 要插入控制列清單，以及向停駐的管理員註冊的控制列指標。  
  
 `pTarget`  
 控制列指標，在其前後插入窗格。  
  
 `bAfter`  
 `TRUE`如果您想要插入`pControlBar`之後`pTarget`，`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果控制列成功插入和註冊，`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 您必須使用註冊每一種控制列[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)參與的停駐配置。  
  
##  <a name="a-nameisfullscreena--cframewndexisfullscreen"></a><a name="isfullscreen"></a>CFrameWndEx::IsFullScreen  
 判斷是否在全螢幕模式中的框架視窗。  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架視窗會以全螢幕模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫設定全螢幕模式[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)方法。  
  
##  <a name="a-nameismenubaravailablea--cframewndexismenubaravailable"></a><a name="ismenubaravailable"></a>CFrameWndEx::IsMenuBarAvailable  
 判斷是否為有效的功能表列物件的指標。  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架視窗的功能表列。否則`FALSE`。  
  
##  <a name="a-nameispointneardocksitea--cframewndexispointneardocksite"></a><a name="ispointneardocksite"></a>CFrameWndEx::IsPointNearDockSite  
 判斷點位於未對齊的區域。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 點的位置。  
  
 [輸出] `dwBarAlignment`  
 對齊點的位置。 請參閱 < 備註 > 一節，取得可能的值。  
  
 [輸出] `bOuterEdge`  
 `TRUE`如果該點位於接近框架框線。`FALSE`如果點位於工作區中。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果點位於對齊區域中。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為`dwBarAlignment`參數。  
  
 `CBRS_ALIGN_TOP`  
 靠上對齊。  
  
 `CBRS_ALIGN_RIGHT`  
 靠右對齊。  
  
 `CBRS_ALIGN_BOTTOM`  
 靠下對齊。  
  
 `CBRS_ALIGN_LEFT`  
 靠左對齊。  
  
##  <a name="a-nameisprintpreviewa--cframewndexisprintpreview"></a><a name="isprintpreview"></a>CFrameWndEx::IsPrintPreview  
 決定框架視窗是否處於預覽列印模式。  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架視窗處於預覽列印模式。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadframea--cframewndexloadframe"></a><a name="loadframe"></a>CFrameWndEx::LoadFrame  
 建立框架視窗並載入其資源的建構完成之後會呼叫這個方法。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIDResource`  
 用來載入所有框架資源的資源識別碼。  
  
 [in] `dwDefaultStyle`  
 預設的框架視窗樣式。  
  
 [in] `pParentWnd`  
 父視窗框架的指標。  
  
 [in] `pContext`  
 指標[CCreateContext 結構](../../mfc/reference/ccreatecontext-structure.md)應用程式建立期間由架構的類別。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功則為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namenegotiateborderspacea--cframewndexnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWndEx::NegotiateBorderSpace  
 實作 OLE 用戶端框線交涉。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>參數  
 [in] `nBorderCmd`  
 框線交涉命令。 請參閱 < 備註 > 一節，取得可能的值。  
  
 [in、out] `lpRectBorder`  
 框線的維度。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果必須重新計算配置。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為`nBorderCmd`參數。  
  
 `borderGet`  
 取得 OLE 用戶端的可用空間。  
  
 `borderRequest`  
 要求 OLE 用戶端空間。  
  
 `borderSet`  
 設定 OLE 用戶端空間。  
  
##  <a name="a-nameonactivatea--cframewndexonactivate"></a><a name="onactivate"></a>CFrameWndEx::OnActivate  
 當使用者輸入切換至或離開框架，架構會呼叫這個方法。  
  
```  
afx_msg void OnActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>參數  
 [in] `nState`  
 框架是否作用中或非作用中。 請參閱 < 備註 > 一節，取得可能的值。  
  
 [in] `pWndOther`  
 正在切換與目前的使用者輸入的另一個視窗的指標。  
  
 [in] `bMinimized`  
 框架的最小化的狀態。 `TRUE`如果框架最小化。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為`nState`參數。  
  
 `WA_ACTIVE`  
 滑鼠點按以外的方法被選取框架。  
  
 `WA_CLICKACTIVE`  
 按一下滑鼠選取框架。  
  
 `WA_INACTIVE`  
 未選取的框架。  
  
##  <a name="a-nameonactivateappa--cframewndexonactivateapp"></a><a name="onactivateapp"></a>CFrameWndEx::OnActivateApp  
 當應用程式選取或取消選取此選項時，由架構呼叫。  
  
```  
afx_msg void OnActivateApp(
    BOOL bActive,  
    DWORD dwThreadID);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActive`  
 `TRUE`如果已選取 應用程式。，`FALSE`如果未選取應用程式。  
  
 [in] `dwThreadID`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonchangevisualmanagera--cframewndexonchangevisualmanager"></a><a name="onchangevisualmanager"></a>CFrameWndEx::OnChangeVisualManager  
 畫面格的變更需要變更視覺管理員時，由架構呼叫。  
  
```  
afx_msg LRESULT OnChangeVisualManager(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 不使用這個參數。  
  
 [in] `lParam`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonclosea--cframewndexonclose"></a><a name="onclose"></a>CFrameWndEx::OnClose  
 架構會呼叫這個方法，以關閉框架。  
  
```  
afx_msg void OnClose();
```  
  
### <a name="remarks"></a>備註  
 如果框架的預覽列印模式時，會傳送 Windows 訊息來關閉預覽列印。否則，如果框架裝載 OLE 用戶端，就會停用用戶端。  
  
##  <a name="a-nameonclosedockingpanea--cframewndexonclosedockingpane"></a><a name="onclosedockingpane"></a>CFrameWndEx::OnCloseDockingPane  
 當使用者按一下時，由框架呼叫**關閉**停駐窗格上的按鈕。  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pPane);
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以關閉停駐列。 `FALSE`否則  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作。 如果您想要處理的停駐列隱藏，請覆寫這個方法。  
  
##  <a name="a-nameoncloseminiframea--cframewndexoncloseminiframe"></a><a name="oncloseminiframe"></a>CFrameWndEx::OnCloseMiniFrame  
 當使用者按一下時，由框架呼叫**關閉**浮動的迷你框架視窗上的按鈕。  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以關閉浮動的迷你框架視窗。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 如果您想要處理的浮動的迷你框架視窗隱藏，請覆寫這個方法。  
  
##  <a name="a-nameonclosepopupmenua--cframewndexonclosepopupmenu"></a><a name="onclosepopupmenu"></a>CFrameWndEx::OnClosePopupMenu  
 架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>參數  
 `pMenuPopup`  
 快顯功能表上的指標。  
  
### <a name="remarks"></a>備註  
 即將關閉視窗時，架構會傳送 WM_DESTROY 訊息。 覆寫這個方法，如果您想要處理來自通知`CMFCPopupMenu`物件所屬的框架視窗時`CMFCPopupMenu`物件正在處理`WM_DESTROY`於視窗關閉時，由架構傳送的訊息。  
  
##  <a name="a-nameoncmdmsga--cframewndexoncmdmsg"></a><a name="oncmdmsg"></a>CFrameWndEx::OnCmdMsg  
 分派命令訊息。  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 命令 ID。  
  
 [in] `nCode`  
 命令訊息類別。  
  
 [in、out] `pExtra`  
 命令物件的指標。  
  
 [in、out] `pHandlerInfo`  
 若要命令處理常式結構的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已處理的命令訊息。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncontexthelpa--cframewndexoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWndEx::OnContextHelp  
 若要顯示內容的相關說明架構呼叫。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncreatea--cframewndexoncreate"></a><a name="oncreate"></a>CFrameWndEx::OnCreate  
 架構建立框架之後呼叫。  
  
```  
afx_msg int OnCreate(LPCREATESTRUCT lpCreateStruct);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpCreateStruct`  
 指標[CREATESTRUCT 結構](../../mfc/reference/createstruct-structure.md)針對新的框架。  
  
### <a name="return-value"></a>傳回值  
 若要繼續畫面格建立;&0;終結框架的-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondestroya--cframewndexondestroy"></a><a name="ondestroy"></a>CFrameWndEx::OnDestroy  
 終結框架時，由架構呼叫。  
  
```  
afx_msg void OnDestroy();
```  
  
### <a name="remarks"></a>備註  
 快速鍵對應表和所有視窗會終結。  
  
##  <a name="a-nameondrawmenuimagea--cframewndexondrawmenuimage"></a><a name="ondrawmenuimage"></a>CFrameWndEx::OnDrawMenuImage  
 當應用程式繪製功能表項目相關聯的映像時，由架構呼叫。  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pMenuButton`  
 功能表按鈕呈現其影像指標。  
  
 [in] `rectImage`  
 指標`Rect`結構，指定螢幕位置和大小的影像。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功架構呈現的影像。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，如果您想要自訂的功能表項目所擁有的功能表列屬於映像轉譯`CFrameWndEx`衍生物件。  
  
##  <a name="a-nameondrawmenulogoa--cframewndexondrawmenulogo"></a><a name="ondrawmenulogo"></a>CFrameWndEx::OnDrawMenuLogo  
 由架構呼叫時`CMFCPopupMenu`物件處理 WM_PAINT 訊息。  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pMenu`  
 功能表項目的指標。  
  
 [in] `rectLogo`  
 常數的參考`CRect`結構，指定螢幕位置和功能表標誌的大小。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式，如果您想要顯示屬於所擁有的功能表列的快顯功能表上的標誌`CFrameWndEx`衍生物件。  
  
##  <a name="a-nameondwmcompositionchangeda--cframewndexondwmcompositionchanged"></a><a name="ondwmcompositionchanged"></a>CFrameWndEx::OnDWMCompositionChanged  
 已啟用或停用桌面視窗管理員 (DWM) 組合，由架構呼叫。  
  
```  
afx_msg LRESULT OnDWMCompositionChanged(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 不使用這個參數。  
  
 [in] `lp`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonexitsizemovea--cframewndexonexitsizemove"></a><a name="onexitsizemove"></a>CFrameWndEx::OnExitSizeMove  
 當框架停止移動或調整大小，由架構呼叫。  
  
```  
LRESULT OnExitSizeMove(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 不使用這個參數。  
  
 [in] `lp`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameongetminmaxinfoa--cframewndexongetminmaxinfo"></a><a name="ongetminmaxinfo"></a>CFrameWndEx::OnGetMinMaxInfo  
 框架的設定視窗維度限制大小時，由架構呼叫。  
  
```  
afx_msg void OnGetMinMaxInfo(MINMAXINFO FAR* lpMMI);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpMMI`  
 指標[MINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632605)結構。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonidleupdatecmduia--cframewndexonidleupdatecmdui"></a><a name="onidleupdatecmdui"></a>CFrameWndEx::OnIdleUpdateCmdUI  
 更新框架顯示命令的處理序閒置時架構呼叫。  
  
```  
afx_msg LRESULT OnIdleUpdateCmdUI(
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 不使用這個參數。  
  
 [in] `lParam`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonlbuttondowna--cframewndexonlbuttondown"></a><a name="onlbuttondown"></a>CFrameWndEx::OnLButtonDown  
 當使用者按下滑鼠左鍵時，架構會呼叫這個方法。  
  
```  
afx_msg void OnLButtonDown(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFlags`  
 指出使用者是否按輔助按鍵。 如需可能的值，請參閱參數`wParam`中[WM_LBUTTONDOWN 通知](http://msdn.microsoft.com/library/windows/desktop/ms645607)。  
  
 [in] `point`  
 指定之 x 和指標的 y 座標，相對於視窗左上角。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonlbuttonupa--cframewndexonlbuttonup"></a><a name="onlbuttonup"></a>CFrameWndEx::OnLButtonUp  
 當使用者放開滑鼠左鍵時，架構會呼叫這個方法。  
  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFlags`  
 指出使用者是否按輔助按鍵。 如需可能的值，請參閱參數`wParam`中[WM_LBUTTONUP 通知](http://msdn.microsoft.com/library/windows/desktop/ms645608)。  
  
 [in] `point`  
 指定之 x 和指標的 y 座標，相對於視窗左上角。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonmenubuttontoolhittesta--cframewndexonmenubuttontoolhittest"></a><a name="onmenubuttontoolhittest"></a>CFrameWndEx::OnMenuButtonToolHitTest  
 由架構呼叫時`CMFCToolBarButton`物件處理程序`WM_NCHITTEST`訊息。  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指標，工具列按鈕。  
  
 [輸出] `pTI`  
 工具的資訊結構的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應用程式會填入`pTI`參數。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果您想要提供特定的功能表項目相關的工具提示資訊，請覆寫這個方法。  
  
##  <a name="a-nameonmenuchara--cframewndexonmenuchar"></a><a name="onmenuchar"></a>CFrameWndEx::OnMenuChar  
 架構會顯示功能表與使用者按下命令未對應的索引鍵時呼叫。  
  
```  
afx_msg LRESULT OnMenuChar(
    UINT nChar,  
    UINT nFlags,  
    CMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `nChar`  
 按下的按鍵的字元碼。  
  
 [in] `nFlags`  
 包含`MF_POPUP`旗標 子功能表中，顯示的功能表是否包含`MF_SYSMENU`如果顯示的功能表控制項 功能表的旗標。  
  
 [in] `pMenu`  
 功能表的指標。  
  
### <a name="return-value"></a>傳回值  
 高序位文字必須是下列值之一。  
  
 `0`  
 架構應忽略按鍵。  
  
 `1`  
 此架構應該關閉功能表。  
  
 `2`  
 架構應該選取其中一個顯示在功能表中的項目。 低序位字組包含要選取命令的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonmousemovea--cframewndexonmousemove"></a><a name="onmousemove"></a>CFrameWndEx::OnMouseMove  
 移動指標時，架構會呼叫這個方法。  
  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFlags`  
 指出使用者是否按輔助按鍵。 如需可能的值，請參閱參數`wParam`中[WM_MOUSEMOVE 通知](http://msdn.microsoft.com/library/windows/desktop/ms645616)。  
  
 [in] `point`  
 指定的 x 和 y 座標相對於視窗左上角的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonmoveminiframea--cframewndexonmoveminiframe"></a><a name="onmoveminiframe"></a>CFrameWndEx::OnMoveMiniFrame  
 窗格視窗移動時，由架構呼叫。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 指標[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)窗格視窗。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果未停駐窗格視窗。，`FALSE`如果已停駐窗格視窗。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonncactivatea--cframewndexonncactivate"></a><a name="onncactivate"></a>CFrameWndEx::OnNcActivate  
 必須重繪框架的非工作區，以表示作用中狀態變更時，由架構呼叫。  
  
```  
afx_msg BOOL OnNcActivate(BOOL bActive);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActive`  
 `TRUE`若要繪製框架使用中。`FALSE`要繪製非作用中的框架。  
  
### <a name="return-value"></a>傳回值  
 若要繼續使用預設處理; Nonzero若要防止非工作區正在停用 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonnccalcsizea--cframewndexonnccalcsize"></a><a name="onnccalcsize"></a>CFrameWndEx::OnNcCalcSize  
 必須計算的大小和位置的工作區時，由架構呼叫。  
  
```  
afx_msg void OnNcCalcSize(
    BOOL bCalcValidRects,  
    NCCALCSIZE_PARAMS FAR* lpncsp);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCalcValidRects`  
 `TRUE`當應用程式必須指定有效的用戶端的區域。否則， `FALSE`。  
  
 [in] `lpncsp`  
 指標`NCCALCSIZE_PARAMS`結構，包含框架維度變更。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonnchittesta--cframewndexonnchittest"></a><a name="onnchittest"></a>CFrameWndEx::OnNcHitTest  
 移動指標時，或按下或放開滑鼠按鈕時，由架構呼叫。  
  
```  
afx_msg LRESULT OnNcHitTest(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 螢幕座標中指標的位置。  
  
### <a name="return-value"></a>傳回值  
 指標叫用列舉的值。 如需可能值的清單，請參閱[WM_NCHITTEST 通知](http://msdn.microsoft.com/library/windows/desktop/ms645618)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonncmousemovea--cframewndexonncmousemove"></a><a name="onncmousemove"></a>CFrameWndEx::OnNcMouseMove  
 在非工作區中移動指標時，由架構呼叫。  
  
```  
afx_msg void OnNcMouseMove(
    UINT nHitTest,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHitTest`  
 指標叫用列舉的值。 如需可能值的清單，請參閱[WM_NCHITTEST 通知](http://msdn.microsoft.com/library/windows/desktop/ms645618)。  
  
 [in] `point`  
 螢幕座標中指標的位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonncpainta--cframewndexonncpaint"></a><a name="onncpaint"></a>CFrameWndEx::OnNcPaint  
 架構必須繪製非工作區時呼叫。  
  
```  
afx_msg void OnNcPaint();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonpanechecka--cframewndexonpanecheck"></a><a name="onpanecheck"></a>CFrameWndEx::OnPaneCheck  
 若要控制可見性 窗格的架構呼叫。  
  
```  
afx_msg BOOL OnPaneCheck(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 窗格的控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已處理命令。`FALSE`繼續命令處理。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonpostpreviewframea--cframewndexonpostpreviewframe"></a><a name="onpostpreviewframe"></a>CFrameWndEx::OnPostPreviewFrame  
 在使用者變更預覽列印模式時，由架構呼叫。  
  
```  
afx_msg LRESULT OnPostPreviewFrame(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 不使用這個參數。  
  
 [in] `lParam`  
 `TRUE`當框架是在預覽列印模式。`FALSE`預覽列印模式為關閉。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonpowerbroadcasta--cframewndexonpowerbroadcast"></a><a name="onpowerbroadcast"></a>CFrameWndEx::OnPowerBroadcast  
 電源管理事件發生時，由架構呼叫。  
  
```  
afx_msg LRESULT OnPowerBroadcast(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 電源管理事件。 如需可能值的清單，請參閱[WM_POWERBROADCAST 訊息](http://msdn.microsoft.com/library/windows/desktop/aa373247)。  
  
 [in] `lp`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 來自呼叫預設視窗程序。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsetmenua--cframewndexonsetmenu"></a><a name="onsetmenu"></a>CFrameWndEx::OnSetMenu  
 若要取代的框架視窗功能表架構呼叫。  
  
```  
afx_msg LRESULT OnSetMenu(
    WPARAM wp,  
    LPARAM lp);  
  
BOOL OnSetMenu(HMENU hmenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 新的框架視窗功能表的控制代碼。  
  
 [in] `lp`  
 新的視窗功能表的控制代碼。  
  
 [in] `hmenu`  
 新的框架視窗功能表的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `LRESULT`是呼叫預設視窗程序的結果。  
  
 `BOOL`是`TRUE`如果事件已處理，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsetpreviewmodea--cframewndexonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWndEx::OnSetPreviewMode  
 若要設定框架預覽列印模式架構呼叫。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPreview`  
 `TRUE`若要啟用預覽列印。`FALSE`停用預覽列印。  
  
 [in] `pState`  
 指標`CPrintPreviewState`框架狀態結構。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsettexta--cframewndexonsettext"></a><a name="onsettext"></a>CFrameWndEx::OnSetText  
 若要設定視窗的文字架構呼叫。  
  
```  
afx_msg LRESULT OnSetText(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 不使用這個參數。  
  
 [in] `lParam`  
 視窗的文字指標。  
  
### <a name="return-value"></a>傳回值  
 傳回值呼叫[DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonshowcustomizepanea--cframewndexonshowcustomizepane"></a><a name="onshowcustomizepane"></a>CFrameWndEx::OnShowCustomizePane  
 顯示時，由框架呼叫`QuickCustomizePane`。  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPane`  
 指向快速自訂窗格。  
  
 [in] `uiToolbarID`  
 若要自訂工具列控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 這個方法永遠會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 快速自訂功能表是快顯功能表，顯示當您按一下工具列的自訂按鈕  
  
##  <a name="a-nameonshowpanesa--cframewndexonshowpanes"></a><a name="onshowpanes"></a>CFrameWndEx::OnShowPanes  
 若要顯示或隱藏窗格架構呼叫。  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 `TRUE`如果應用程式顯示的窗格。`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 這個方法永遠會傳回`FALSE`。  
  
### <a name="remarks"></a>備註  
 預設實作會顯示窗格如果`bShow`是`TRUE`和要隱藏窗格或`bShow`是`FALSE`而且窗格會顯示出來。  
  
 如果預設實作會隱藏窗格`bShow`是`TRUE`和窗格是可見或`bShow`是`FALSE`和要隱藏窗格。  
  
 在衍生類別時所要執行自訂程式碼架構顯示或隱藏窗格中的，這個方法會覆寫。  
  
##  <a name="a-nameonshowpopupmenua--cframewndexonshowpopupmenu"></a><a name="onshowpopupmenu"></a>CFrameWndEx::OnShowPopupMenu  
 顯示快顯功能表時，由架構呼叫。  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenu`  
 快顯功能表上的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果快顯功能表是可見的。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 在衍生類別時，架構會顯示快顯功能表上，執行自訂程式碼中的，這個方法會覆寫。 例如，您可以覆寫這個方法，以變更背景色彩的快顯功能表中的命令。  
  
##  <a name="a-nameonsizea--cframewndexonsize"></a><a name="onsize"></a>CFrameWndEx::OnSize  
 框架的大小變更後，由框架呼叫。  
  
```  
afx_msg void OnSize(
    UINT nType,  
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>參數  
 [in] `nType`  
 調整大小的型別。 如需可能的值，請參閱參數`wParam`中[WM_SIZE 通知](http://msdn.microsoft.com/library/windows/desktop/ms632646)。  
  
 [in] `cx`  
 新框架寬度的像素為單位。  
  
 [in] `cy`  
 單位為像素框架的新高度。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsizinga--cframewndexonsizing"></a><a name="onsizing"></a>CFrameWndEx::OnSizing  
 當使用者調整框架，由架構呼叫。  
  
```  
afx_msg void OnSizing(
    UINT fwSide,  
    LPRECT pRect);
```  
  
### <a name="parameters"></a>參數  
 [in] `fwSide`  
 移動的資料框架的邊緣。 請參閱參數`wParam`中[WM_SIZING 通知](http://msdn.microsoft.com/library/windows/desktop/ms632647)。  
  
 [in、out] `pRect`  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](../../mfc/reference/rect-structure1.md)結構，包含框架的座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsyscolorchangea--cframewndexonsyscolorchange"></a><a name="onsyscolorchange"></a>CFrameWndEx::OnSysColorChange  
 當系統色彩變更時，由架構呼叫。  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameontearoffmenua--cframewndexontearoffmenu"></a><a name="ontearoffmenu"></a>CFrameWndEx::OnTearOffMenu  
 當應用程式會顯示具有撕列功能表時，由架構呼叫。  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPopup`  
 快顯功能表上的指標。  
  
 [in] `pBar`  
 撕下橫條指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用快顯功能表上，使用撕列。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法來執行自訂程式碼時，架構會顯示一種控制列在衍生類別中。  
  
 預設實作不做任何動作，並傳回`TRUE`。  
  
##  <a name="a-nameontoolbarcontextmenua--cframewndexontoolbarcontextmenu"></a><a name="ontoolbarcontextmenu"></a>CFrameWndEx::OnToolbarContextMenu  
 建立工具列的快顯功能表上的架構所呼叫。  
  
```  
afx_msg LRESULT OnToolbarContextMenu(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 不使用這個參數。  
  
 [in] `lp`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameontoolbarcreatenewa--cframewndexontoolbarcreatenew"></a><a name="ontoolbarcreatenew"></a>CFrameWndEx::OnToolbarCreateNew  
 架構會呼叫這個方法，以建立新的工具列。  
  
```  
afx_msg LRESULT OnToolbarCreateNew(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in] `wp`  
 不使用這個參數。  
  
 [in] `lp`  
 在工具列的標題列文字指標。  
  
### <a name="return-value"></a>傳回值  
 指向新的工具列。或`NULL`若未建立工具列。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameontoolbardeletea--cframewndexontoolbardelete"></a><a name="ontoolbardelete"></a>CFrameWndEx::OnToolbarDelete  
 刪除工具列時，由架構呼叫。  
  
```  
afx_msg LRESULT OnToolbarDelete(
    WPARAM, 
    LPARAM lp);
```  
  
### <a name="parameters"></a>參數  
 [in]  
 不使用這個參數。  
  
 [in] `lp`  
 工具列的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列已刪除。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonupdateframemenua--cframewndexonupdateframemenu"></a><a name="onupdateframemenu"></a>CFrameWndEx::OnUpdateFrameMenu  
 若要設定框架功能表架構呼叫。  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenuAlt`  
 替代功能表的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonupdateframetitlea--cframewndexonupdateframetitle"></a><a name="onupdateframetitle"></a>CFrameWndEx::OnUpdateFrameTitle  
 架構會呼叫這個方法，以更新框架視窗的標題列。  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAddToTitle`  
 `TRUE`若要加入至框架視窗標題列中，主動式文件標題否則`FALSE.`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonupdatepanemenua--cframewndexonupdatepanemenu"></a><a name="onupdatepanemenu"></a>CFrameWndEx::OnUpdatePaneMenu  
 若要更新窗格功能表架構呼叫。  
  
```  
afx_msg void OnUpdatePaneMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCmdUI`  
 窗格使用者介面物件的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonwindowposchangeda--cframewndexonwindowposchanged"></a><a name="onwindowposchanged"></a>CFrameWndEx::OnWindowPosChanged  
 因為視窗管理方法呼叫而變更的框架大小、 位置或圖層順序時，由架構呼叫。  
  
```  
afx_msg void OnWindowPosChanged(WINDOWPOS FAR* lpwndpos);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpwndpos`  
 指標[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)結構，其中包含新的大小和位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namepanefrompointa--cframewndexpanefrompoint"></a><a name="panefrompoint"></a>CFrameWndEx::PaneFromPoint  
 搜尋指定的點的每個窗格。  
  
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
 [in] `point`  
 若要檢查點的螢幕座標。  
  
 [in] `nSensitivity`  
 展開這個數量的每個控制列，這個周框搜尋點時。  
  
 [in] `bExactBar`  
 `TRUE`若要忽略`nSensitivity`參數，否則`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，該方法會搜尋只指定類型的控制列。  
  
 [輸出] `dwAlignment`  
 如果成功，此參數會包含控制列最接近指定點開始。 否則，這個參數未初始化。  
  
### <a name="return-value"></a>傳回值  
 控制列，其中包含一個指向`point`;`NULL`如果找不到任何控制項。  
  
### <a name="remarks"></a>備註  
 這個方法會搜尋針對應用程式中的所有控制列`point`。  
  
 使用`nSensitivity`來增加搜尋區域的大小。 使用`pRTCBarType`以限制該方法會搜尋的控制列類型。  
  
##  <a name="a-namepretranslatemessagea--cframewndexpretranslatemessage"></a><a name="pretranslatemessage"></a>CFrameWndEx::PreTranslateMessage  
 再分派這些處理特定視窗訊息。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMsg`  
 指標[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 非零，如果訊息已處理並不會分派;如果未處理的訊息，並且應該分派到，0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerecalclayouta--cframewndexrecalclayout"></a><a name="recalclayout"></a>CFrameWndEx::RecalcLayout  
 調整框架和其子視窗的配置。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNotify`  
 指定是否要通知 OLE 用戶端項目與變更相關的配置。  
  
### <a name="remarks"></a>備註  
 框架視窗的大小已變更或控制列的顯示或隱藏時，會呼叫此方法。  
  
##  <a name="a-nameremovepanefromdockmanagera--cframewndexremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CFrameWndEx::RemovePaneFromDockManager  
 取消註冊 窗格，並將它從停駐管理員移除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 控制列窗格中，若要移除的指標。  
  
 [in] `bDestroy`  
 `TRUE`控制列終結之前移除。`FALSE`否則。  
  
 [in] `bAdjustLayout`  
 `TRUE`若要調整停駐的版面配置。`FALSE`否則。  
  
 [in] `bAutoHide`  
 `TRUE`如果控制列處於自動隱藏模式;`FALSE`否則。  
  
 [in] `pBarReplacement`  
 指標，會取代 [移除] 窗格的窗格。  
  
### <a name="remarks"></a>備註  
 若要移除的框架視窗停駐配置的控制列中使用這個方法。  
  
 [CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)處理的控制列配置。 您必須向每個控制列的停駐的管理員使用[CFrameWndEx::AddPane](#addpane)方法或[CFrameWndEx::InsertPane](#insertpane)方法。  
  
##  <a name="a-namesetdockstatea--cframewndexsetdockstate"></a><a name="setdockstate"></a>CFrameWndEx::SetDockState  
 還原停駐配置到停駐狀態儲存在登錄中。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>參數  
 `state`  
 停駐的狀態。 這個參數已忽略。  
  
##  <a name="a-namesetprintpreviewframea--cframewndexsetprintpreviewframe"></a><a name="setprintpreviewframe"></a>CFrameWndEx::SetPrintPreviewFrame  
 設定預覽列印框架視窗。  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 預覽列印框架視窗的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetuptoolbarmenua--cframewndexsetuptoolbarmenu"></a><a name="setuptoolbarmenu"></a>CFrameWndEx::SetupToolbarMenu  
 插入使用者定義的命令於工具列功能表。  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>參數  
 [in] `menu`  
 A`CMenu`要修改的物件。  
  
 [in] `uiViewUserToolbarCmdFirst`  
 第一個使用者定義的命令。  
  
 [in] `uiViewUserToolbarCmdLast`  
 最後一個使用者定義的命令。  
  
### <a name="remarks"></a>備註  
 架構會儲存在清單中的使用者定義的命令。 使用`uiViewUserToolbarCmdFirst`和`uiViewUserToolbarCmdList`來指定要插入的命令索引。  
  
##  <a name="a-nameshowfullscreena--cframewndexshowfullscreen"></a><a name="showfullscreen"></a>CFrameWndEx::ShowFullScreen  
 切換全螢幕模式和標準模式之間的主框架。  
  
```  
void ShowFullScreen();
```  
  
##  <a name="a-nameshowpanea--cframewndexshowpane"></a><a name="showpane"></a>CFrameWndEx::ShowPane  
 顯示或隱藏指定的窗格。  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 控制列，以顯示或隱藏指標。  
  
 [in] `bShow`  
 如果`TRUE`，應用程式會顯示控制列。 否則，應用程式會隱藏控制列。  
  
 [in] `bDelay`  
 如果`TRUE`，直到這個架構會呼叫延遲停駐配置調整[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)。 否則，請立即重新計算停駐配置。  
  
 [in] `bActivate`  
 如果`TRUE`，啟動控制列。 否則，顯示控制項列處於非作用中狀態。  
  
##  <a name="a-nameupdatecaptiona--cframewndexupdatecaption"></a><a name="updatecaption"></a>CFrameWndEx::UpdateCaption  
 若要更新的視窗框架標題架構呼叫。  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namewinhelpa--cframewndexwinhelp"></a><a name="winhelp"></a>CFrameWndEx::WinHelp  
 叫用 WinHelp 的應用程式或內容的相關說明。  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>參數  
 `dwData`  
 資料相依於`nCmd`參數。 如需可能值的清單，請參閱[WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267)。  
  
 `nCmd`  
 [說明] 命令。 如需可能值的清單，請參閱[WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267)。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)

