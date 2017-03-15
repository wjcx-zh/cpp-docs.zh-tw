---
title: "Cmdiframewndex 是類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIFrameWndEx.AddDockSite
- CMDIFrameWndEx
- CMDIFrameWndEx::AddDockSite
dev_langs:
- C++
helpviewer_keywords:
- CMDIFrameWndEx class
ms.assetid: dbcafcb3-9a7a-4f11-9dfe-ba57565c81d0
caps.latest.revision: 42
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b9946f59b9ed789604ac6a02d2148188831bae56
ms.lasthandoff: 02/24/2017

---
# <a name="cmdiframewndex-class"></a>CMDIFrameWndEx 類別
擴充功能的[CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)，Windows 多重文件介面 (MDI) 框架視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CMDIFrameWndEx : public CMDIFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMDIFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|重新計算使用中的項目的配置。|  
|`CMDIFrameWndEx::AddDockSite`|不使用這個方法。|  
|[CMDIFrameWndEx::AddPane](#addpane)|向停駐的管理員 窗格。|  
|[CMDIFrameWndEx::AdjustClientArea](#adjustclientarea)|減少工作區，以允許框線。|  
|[CMDIFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|重新計算所有停駐窗格的配置。|  
|[CMDIFrameWndEx::AreMDITabs](#aremditabs)|判斷是否已啟用 MDI 索引標籤功能或 MDI 索引標籤式群組功能。|  
|[CMDIFrameWndEx::CanCovertControlBarToMDIChild](#cancovertcontrolbartomdichild)|若要判斷框架視窗是否可以轉換成索引標籤式文件的停駐窗格架構呼叫。|  
|[CMDIFrameWndEx::ControlBarToTabbedDocument](#controlbartotabbeddocument)|索引標籤式文件會將指定的停駐窗格。|  
|[CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow)|建立子文件視窗。|  
|[CMDIFrameWndEx::CreateNewWindow](#createnewwindow)|若要建立新的視窗，架構呼叫。|  
|`CMDIFrameWndEx::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMDIFrameWndEx::DockPane](#dockpane)|框架視窗停駐於指定的窗格。|  
|[CMDIFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐在另一個窗格的左邊。|  
|[CMDIFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|啟用自動隱藏窗格模式在指定的側邊的主框架視窗停駐時。|  
|[CMDIFrameWndEx::EnableDocking](#enabledocking)|啟用的停駐屬於 MDI 框架視窗的窗格。|  
|[CMDIFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|顯示或隱藏全螢幕模式中的主功能表。|  
|[CMDIFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|啟用全螢幕模式，框架視窗。|  
|[CMDIFrameWndEx::EnableLoadDockState](#enableloaddockstate)|啟用或停用的銜接狀態的載入。|  
|[CMDIFrameWndEx::EnableMDITabbedGroups](#enablemditabbedgroups)|啟用或停用的 MDI 索引標籤式群組功能。|  
|[CMDIFrameWndEx::EnableMDITabs](#enablemditabs)|啟用或停用 MDI 索引標籤功能。 啟用時，框架視窗會顯示每個 MDI 子視窗的索引標籤。|  
|[CMDIFrameWndEx::EnableMDITabsLastActiveActivation](#enablemditabslastactiveactivation)|指定當使用者關閉目前的索引標籤是否應啟用 [最後一個使用中] 索引標籤。|  
|[CMDIFrameWndEx::EnablePaneMenu](#enablepanemenu)|啟用或停用自動建立及管理的快顯窗格功能表會顯示應用程式窗格的清單。  。|  
|[CMDIFrameWndEx::EnableWindowsDialog](#enablewindowsdialog)|插入功能表項目的命令 ID 會呼叫[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)對話方塊。|  
|[CMDIFrameWndEx::GetActivePopup](#getactivepopup)|將指標傳回到目前顯示的快顯功能表。|  
|[CMDIFrameWndEx::GetPane](#getpane)|將指標傳回至窗格中具有指定之的控制項 id。|  
|[CMDIFrameWndEx::GetDefaultResId](#getdefaultresid)|傳回的 MDI 框架視窗的共用資源的識別碼。|  
|[CMDIFrameWndEx::GetMDITabGroups](#getmditabgroups)|傳回一份 MDI 索引視窗。|  
|[CMDIFrameWndEx::GetMDITabs](#getmditabs)|傳回加上底線的索引標籤式視窗的參考。|  
|[CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems](#getmditabscontextmenualloweditems)|傳回旗標的組合，用來判定哪些內容功能表項目有效啟用 MDI 索引標籤式群組功能。|  
|[CMDIFrameWndEx::GetMenuBar](#getmenubar)|傳回附加到的框架視窗的功能表列物件的指標。|  
|[CMDIFrameWndEx::GetRibbonBar](#getribbonbar)|擷取框架的功能區列控制項。|  
|[CMDIFrameWndEx::GetTearOffBars](#gettearoffbars)|會傳回一份[CPane](../../mfc/reference/cpane-class.md)-衍生撕狀態的物件。|  
|`CMDIFrameWndEx::GetThisClass`|若要取得的指標，架構呼叫[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMDIFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|當應用程式顯示的工具列按鈕的工具提示時，由架構呼叫。|  
|[CMDIFrameWndEx::InsertPane](#insertpane)|連接管理員會向指定的窗格。|  
|[CMDIFrameWndEx::IsFullScreen](#isfullscreen)|判斷是否在全螢幕模式中的框架視窗。|  
|[CMDIFrameWndEx::IsMDITabbedGroup](#ismditabbedgroup)|判斷是否已啟用 MDI 索引標籤式群組功能。|  
|[CMDIFrameWndEx::IsMemberOfMDITabGroup](#ismemberofmditabgroup)|判斷指定的索引標籤式的視窗是否為 MDI 索引標籤式群組中的視窗的清單中。|  
|[CMDIFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|決定框架視窗是否有功能表列。|  
|[CMDIFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|判斷指定的點是否停駐位置附近。|  
|[CMDIFrameWndEx::IsPrintPreview](#isprintpreview)|決定框架視窗是否處於預覽列印模式。|  
|[CMDIFrameWndEx::LoadFrame](#loadframe)|建立框架視窗從資源資訊。 (覆寫 `CMDIFrameWnd::LoadFrame`。)|  
|[Cmdiframewndex:: Loadmdistate](#loadmdistate)|載入指定的 MDI 索引標籤式群組的配置和先前開啟的文件的清單。|  
|[CMDIFrameWndEx::MDITabMoveToNextGroup](#mditabmovetonextgroup)|將作用中的索引標籤從目前使用中的索引標籤式視窗移至下一個或前一個索引群組。|  
|[CMDIFrameWndEx::MDITabNewGroup](#mditabnewgroup)|建立新的索引標籤式的群組具有單一視窗。|  
|[CMDIFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|會在框架視窗的框線空間交涉 OLE 就地啟用期間。|  
|[CMDIFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|當使用者按一下時，由框架呼叫**關閉**可停駐窗格上的按鈕。|  
|[CMDIFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|當使用者按一下時，由框架呼叫**關閉**浮動的迷你框架視窗上的按鈕。|  
|[CMDIFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|使用中的快顯功能表上處理時，由框架呼叫`WM_DESTROY`訊息。|  
|[CMDIFrameWndEx::OnCmdMsg](#oncmdmsg)|傳送和分派命令訊息，並以更新命令使用者介面物件的架構所呼叫。|  
|[CMDIFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|架構在繪製與功能表項目相關聯的映像時所呼叫。|  
|[CMDIFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|由架構呼叫時[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)處理程序`WM_PAINT`訊息。|  
|[CMDIFrameWndEx::OnEraseMDIClientBackground](#onerasemdiclientbackground)|MDI 框架視窗程序時，由框架呼叫`WM_ERASEBKGND`訊息。|  
|[CMDIFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|由架構呼叫時[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件處理程序`WM_NCHITTEST`訊息。|  
|[CMDIFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|若要移動的迷你框架視窗，架構呼叫。|  
|[CMDIFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|設定應用程式的主框架視窗預覽列印模式。 (覆寫[CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode)。)|  
|[CMDIFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|啟動快速自訂窗格時，由架構呼叫。|  
|[CMDIFrameWndEx::OnShowMDITabContextMenu](#onshowmditabcontextmenu)|由架構呼叫時應該顯示內容功能表，在其中一個索引標籤。 （有效的 MDI 索引標籤式群組只。）|  
|[CMDIFrameWndEx::OnShowPanes](#onshowpanes)|若要顯示或隱藏窗格架構呼叫。|  
|[CMDIFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|架構在啟動快顯功能表時所呼叫。|  
|[CMDIFrameWndEx::OnSizeMDIClient](#onsizemdiclient)|架構的用戶端 MDI 視窗大小變更時呼叫。|  
|[CMDIFrameWndEx::OnTearOffMenu](#ontearoffmenu)|架構在啟動有分割列的功能表時所呼叫。|  
|[CMDIFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|若要更新 [框架] 功能表架構呼叫。 (覆寫 `CMDIFrameWnd::OnUpdateFrameMenu`。)|  
|[CMDIFrameWndEx::PaneFromPoint](#panefrompoint)|傳回包含指定的點的停駐窗格。|  
|`CMDIFrameWndEx::PreTranslateMessage`|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。  (覆寫 `CMDIFrameWnd::PreTranslateMessage`。)|  
|[CMDIFrameWndEx::RecalcLayout](#recalclayout)|若要重新計算框架視窗的版面配置架構呼叫。 (覆寫[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。)|  
|[CMDIFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|取消註冊 窗格，並將它從停駐管理員移除。|  
|[CMDIFrameWndEx::SaveMDIState](#savemdistate)|儲存目前的 MDI 索引標籤式群組的配置和先前所開啟的文件的清單。|  
|[CMDIFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|設定預覽列印框架視窗。|  
|[CMDIFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|藉由搜尋虛設項目並替換成指定的使用者定義項目，修改工具列物件。|  
|[CMDIFrameWndEx::ShowFullScreen](#showfullscreen)|切換至全螢幕模式一般模式從主框架。|  
|[CMDIFrameWndEx::ShowPane](#showpane)|顯示或隱藏指定的窗格。|  
|[CMDIFrameWndEx::ShowWindowsDialog](#showwindowsdialog)|建立[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)方塊，並將它開啟。|  
|[CMDIFrameWndEx::TabbedDocumentToControlBar](#tabbeddocumenttocontrolbar)|將指定的索引標籤式文件轉換為停駐窗格。|  
|[CMDIFrameWndEx::UpdateCaption](#updatecaption)|若要更新的視窗框架標題架構呼叫。|  
|[CMDIFrameWndEx::UpdateMDITabbedBarsIcons](#updatemditabbedbarsicons)|設定每個 MDI 索引標籤式窗格的圖示。|  
|[CMDIFrameWndEx::WinHelp](#winhelp)|架構所呼叫以起始 WinHelp 應用程式或內容說明。 (覆寫[CWnd::WinHelp](../../mfc/reference/cwnd-class.md#winhelp)。)|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild](#m_bcancovertcontrolbartomdichild)|判斷是否停駐窗格可以轉換成 MDI 子視窗。|  
|[CMDIFrameWndEx::m_bDisableSetRedraw](#m_bdisablesetredraw)|啟用或停用的 MDI 子視窗的重繪最佳化。|  
  
## <a name="remarks"></a>備註  
 若要在 MDI 應用程式中利用自訂擴充的功能，可以衍生 MDI 框架視窗類別，從應用程式的`CMDIFrameWndEx`而不是`CMDIFrameWnd`。  
  
## <a name="example"></a>範例  
 下列範例是衍生自`CMDIFrameWndEx`。 此程式碼片段來自[DrawClient 範例︰ MFC Ribbon-Based OLE 物件的繪圖應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&1;](../../mfc/reference/codesnippet/cpp/cmdiframewndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)  
  
 [Cmdiframewndex 是](../../mfc/reference/cmdiframewndex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxMDIFrameWndEx.h  
  
##  <a name="a-nameactiveitemrecalclayouta--cmdiframewndexactiveitemrecalclayout"></a><a name="activeitemrecalclayout"></a>CMDIFrameWndEx::ActiveItemRecalcLayout  
 重新計算使用中的項目的配置。  
  
```  
void ActiveItemRecalcLayout();
```  
  
##  <a name="a-nameaddpanea--cmdiframewndexaddpane"></a><a name="addpane"></a>CMDIFrameWndEx::AddPane  
 向停駐的管理員 窗格。  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 [註冊] 窗格的指標。  
  
 [in] `bTail`  
 指定是否要將這個窗格加入至清單的結尾。  
  
### <a name="return-value"></a>傳回值  
 如果已成功註冊窗格會傳回非零值。 如果窗格已向停駐 manager，傳回 0。  
  
### <a name="remarks"></a>備註  
 每個窗格必須向[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)它可以參加的停駐配置之前。 使用此方法以通知停駐的經理想要停駐特定的窗格。 一旦註冊此窗格，會停駐管理員對齊根據其對齊設定和位置清單中的停駐的管理員所維護的窗格。  
  
##  <a name="a-nameadjustclientareaa--cmdiframewndexadjustclientarea"></a><a name="adjustclientarea"></a>CMDIFrameWndEx::AdjustClientArea  
 減少工作區，以允許框線。  
  
```  
virtual void AdjustClientArea();
```  
  
##  <a name="a-nameadjustdockinglayouta--cmdiframewndexadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CMDIFrameWndEx::AdjustDockingLayout  
 重新計算所有停駐窗格的配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `hdwp`  
 識別多個視窗位置結構。 您可以取得此值，藉由呼叫`BeginDeferWindowPos`。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，重新計算所有窗格停駐在框架視窗的配置。  
  
##  <a name="a-namearemditabsa--cmdiframewndexaremditabs"></a><a name="aremditabs"></a>CMDIFrameWndEx::AreMDITabs  
 決定是否啟用 MDI 索引標籤功能或 MDI 索引標籤式的群組功能。  
  
```  
BOOL AreMDITabs(int* pnMDITabsType=NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pnMDITabsType`  
 表示要啟用哪些功能的整數變數的指標︰  
  
-   0︰ 停用所有功能。  
  
-   1︰ 啟用 MDI 索引標籤。  
  
-   2︰ 啟用 MDI 索引群組。  
  
### <a name="return-value"></a>傳回值  
 `Returns TRUE`如果 MDI 索引標籤或 MDI 索引標籤式群組已啟用。  
  
 `Returns FALSE`如果沒有上述功能啟用。  
  
### <a name="remarks"></a>備註  
 使用此函式可判斷 MDI 索引標籤或 MDI 索引群組會啟用框架視窗。 使用[CMDIFrameWndEx::EnableMDITabs](#enablemditabs)啟用或停用 MDI 索引標籤功能。  
  
 使用[CMDIFrameWndEx::EnableMDITabbedGroups](#enablemditabbedgroups)啟用或停用 MDI 索引標籤式的群組功能。  
  
##  <a name="a-namecancovertcontrolbartomdichilda--cmdiframewndexcancovertcontrolbartomdichild"></a><a name="cancovertcontrolbartomdichild"></a>CMDIFrameWndEx::CanCovertControlBarToMDIChild  
 若要判斷框架視窗是否可以轉換成索引標籤式文件的停駐窗格架構呼叫  
  
```  
virtual BOOL CanCovertControlBarToMDIChild();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果框架視窗可以將停駐窗格轉換為索引標籤式文件; 否則會傳回`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，並傳回`TRUE`可停駐窗格索引標籤式文件轉換。 或者，您可以設定[CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild](#m_bcancovertcontrolbartomdichild)到`TRUE`。  
  
##  <a name="a-namecontrolbartotabbeddocumenta--cmdiframewndexcontrolbartotabbeddocument"></a><a name="controlbartotabbeddocument"></a>CMDIFrameWndEx::ControlBarToTabbedDocument  
 索引標籤式文件會將指定的停駐窗格。  
  
```  
virtual CMDIChildWndEx* ControlBarToTabbedDocument(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>參數  
 `pBar`  
 要轉換的停駐窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回新的 MDI 子視窗，其中包含停駐窗格的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會將索引標籤式文件中的停駐窗格。 當您呼叫這個方法時，此架構會建立[CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)物件，移除停駐窗格從停駐的管理員，並加入新的 MDI 子視窗停駐窗格。 MDI 子視窗調整大小，以涵蓋整個工作區的停駐窗格  
  
##  <a name="a-namecreatedocumentwindowa--cmdiframewndexcreatedocumentwindow"></a><a name="createdocumentwindow"></a>CMDIFrameWndEx::CreateDocumentWindow  
 建立子文件視窗。  
  
```  
virtual CMDIChildWndEx* CreateDocumentWindow(
    LPCTSTR lpcszDocName,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpcszDocName`  
 文字字串，其中包含文件識別碼。 一般而言，它是文件檔案的完整路徑。  
  
 [in] `pObj`  
 使用者定義的物件指標。 例如，開發人員可以建立應用程式特定的資料結構描述文件，並告訴您如何在文件應該在啟動時初始化。  
  
### <a name="return-value"></a>傳回值  
 指標`CMDIChildWndEx`。  
  
### <a name="remarks"></a>備註  
 載入先前儲存在登錄中的文件的清單時，架構會呼叫這個方法。  
  
 若要建立文件，從登錄載入時，覆寫這個方法。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`CreateDocumentWindow`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 在此範例中，`g_strStartViewName`可能是 「 虛擬文件 」 （例如，「 啟動頁面 」），實際上不是從磁碟檔案載入的名稱。 因此我們需要特殊處理，以處理這種情況。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&13;](../../mfc/codesnippet/cpp/cmdiframewndex-class_2.cpp)]  
  
##  <a name="a-namecreatenewwindowa--cmdiframewndexcreatenewwindow"></a><a name="createnewwindow"></a>CMDIFrameWndEx::CreateNewWindow  
 若要建立新的視窗，架構呼叫。  
  
```  
virtual CMDIChildWndEx* CreateNewWindow(
    LPCTSTR lpcszDocName,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpcszDocName`  
 文件名稱。  
  
 [in] `pObj`  
 保留供未來使用。  
  
### <a name="return-value"></a>傳回值  
 新視窗的指標。  
  
##  <a name="a-namedockpanea--cmdiframewndexdockpane"></a><a name="dockpane"></a>CMDIFrameWndEx::DockPane  
 框架視窗停駐於指定的窗格。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要停駐窗格的指標。  
  
 [in] `nDockBarID`  
 指定框架視窗停駐的側的邊。  
  
 [in] `lpRect`  
 未使用。  
  
### <a name="remarks"></a>備註  
 這個方法停駐在指定的其中一個已在框架視窗的側邊窗格時指定[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)和[CMDIFrameWndEx::EnableDocking](#enabledocking)所呼叫。  
  
### <a name="example"></a>範例  
 下列範例示範 `DockPane` 方法的用法。 此程式碼片段來自[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&4;](../../mfc/codesnippet/cpp/cmdiframewndex-class_3.cpp)]  
  
##  <a name="a-namedockpaneleftofa--cmdiframewndexdockpaneleftof"></a><a name="dockpaneleftof"></a>CMDIFrameWndEx::DockPaneLeftOf  
 將窗格停駐在另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 指標停駐窗格。  
  
 [in] `pLeftOf`  
 此窗格，可做為停駐位置指標。 。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`作業是否成功。 否則傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以停駐在預先定義的順序中的數個窗格物件。 這個方法所指定的窗格停駐於`pBar`左邊窗格中所指定的`pLeftOf`。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`DockPaneLeftOf`方法使用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&5;](../../mfc/codesnippet/cpp/cmdiframewndex-class_4.cpp)]  
  
##  <a name="a-nameenableautohidepanesa--cmdiframewndexenableautohidepanes"></a><a name="enableautohidepanes"></a>CMDIFrameWndEx::EnableAutoHidePanes  
 啟用自動隱藏窗格模式時指定的側邊的主框架視窗停駐。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定要啟用的主框架視窗的側邊。 使用一或多個下列旗標。  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>傳回值  
 呼叫此函式可啟用窗格的 自動隱藏模式時指定的側邊的主框架視窗停駐。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnableAutoHidePanes`方法使用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&6;](../../mfc/codesnippet/cpp/cmdiframewndex-class_5.cpp)]  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenabledockinga--cmdiframewndexenabledocking"></a><a name="enabledocking"></a>CMDIFrameWndEx::EnableDocking  
 啟用的停駐屬於 MDI 框架視窗的窗格。  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定您想要套用的停駐樣式。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 呼叫此函式可讓屬於窗格的停駐`CMDIFrameWndEx`物件。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnableDocking`方法使用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&7;](../../mfc/codesnippet/cpp/cmdiframewndex-class_6.cpp)]  
  
##  <a name="a-nameenablefullscreenmainmenua--cmdiframewndexenablefullscreenmainmenu"></a><a name="enablefullscreenmainmenu"></a>CMDIFrameWndEx::EnableFullScreenMainMenu  
 顯示或隱藏全螢幕模式中的主功能表。  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnableMenu`  
 `TRUE`若要在全螢幕模式中，顯示在主功能表或`FALSE`隱藏起來。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenablefullscreenmodea--cmdiframewndexenablefullscreenmode"></a><a name="enablefullscreenmode"></a>CMDIFrameWndEx::EnableFullScreenMode  
 啟用全螢幕模式，框架視窗。  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiFullScreenCmd`  
 啟用或停用全螢幕模式的命令識別碼。  
  
### <a name="remarks"></a>備註  
 在全螢幕模式中，會隱藏所有停駐控制列、 工具列和功能表，並使用中的檢視會調整大小以佔用全螢幕。當您啟用全螢幕模式時，您必須指定啟用或停用該命令的識別碼。 您可以呼叫`EnableFullScreenMode`從主框架的`OnCreate`函式。 當框架視窗會切換至全螢幕模式時，此架構會建立浮動的工具列具有一個按鈕具有指定的命令識別碼。如果您想要保留在螢幕上的主功能表上，呼叫[CMDIFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)。  
  
##  <a name="a-nameenableloaddockstatea--cmdiframewndexenableloaddockstate"></a><a name="enableloaddockstate"></a>CMDIFrameWndEx::EnableLoadDockState  
 啟用或停用的銜接狀態的載入。  
  
```  
void EnableLoadDockState(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用的銜接狀態中，載入`FALSE`停用的銜接狀態的載入。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenablemditabbedgroupsa--cmdiframewndexenablemditabbedgroups"></a><a name="enablemditabbedgroups"></a>CMDIFrameWndEx::EnableMDITabbedGroups  
 啟用或停用框架視窗的 MDI 索引標籤式的群組功能。  
  
```  
void EnableMDITabbedGroups(
    BOOL bEnable,  
    const CMDITabInfo& params);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 如果`TRUE`，啟用 MDI 索引標籤式的群組功能; 如果`FALSE`，MDI 索引標籤式的群組功能已停用。  
  
 [in] `params`  
 指定架構適用於在 MDI 工作區中建立子視窗的參數。  
  
### <a name="remarks"></a>備註  
 使用這個方法來啟用或停用 MDI 索引標籤式的群組功能。 這項功能可讓您以垂直對齊的索引標籤式視窗或 MDI 工作區中水平顯示子視窗的 MDI 應用程式。 索引視窗會以分隔器分隔。 使用者可以使用分隔器調整索引標籤式的群組的大小。  
  
-   使用者可以︰  
  
-   在群組間拖曳個別索引標籤。  
  
-   若要建立新的群組視窗的邊緣拖曳個別索引標籤。  
  
-   移動索引標籤，或使用捷徑功能表建立新的群組。  
  
-   索引標籤式視窗的目前配置和目前開啟的文件的清單，可以儲存您的應用程式。  
  
 如果您呼叫這個方法與`bEnable`設`FALSE`，`params`會被忽略。  
  
 即使已啟用 MDI 索引群組，您可以呼叫這個方法一次修改子視窗的設定。 使用呼叫方法`bEnable`設`TRUE`和修改的成員`CMDITabInfo`物件所指定的`params`參數。  
  
 如需有關如何使用 MDI 索引標籤式群組，請參閱[MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnableMDITabbedGroups`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&8;](../../mfc/codesnippet/cpp/cmdiframewndex-class_7.cpp)]  
  
##  <a name="a-nameenablemditabsa--cmdiframewndexenablemditabs"></a><a name="enablemditabs"></a>CMDIFrameWndEx::EnableMDITabs  
 啟用或停用 MDI 框架視窗的 MDI 索引標籤功能。 啟用時，框架視窗會顯示每個 MDI 子視窗的索引標籤。  
  
```  
void EnableMDITabs(
    BOOL bEnable=TRUE,  
    BOOL bIcons=TRUE,  
    CMFCTabCtrl::Location tabLocation=CMFCTabCtrl::LOCATION_BOTTOM,  
    BOOL bTabCloseButton=FALSE,  
    CMFCTabCtrl::Style style=CMFCTabCtrl::STYLE_3D_SCROLLED,  
    BOOL bTabCustomTooltips=FALSE,  
    BOOL bActiveTabCloseButton=FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 指定是否啟用索引標籤。  
  
 `bIcons`  
 指定的索引標籤上，是否會顯示圖示。  
  
 `tabLocation`  
 指定的索引標籤的位置。  
  
 `bTabCloseButton`  
 指定是否要顯示索引標籤 [關閉] 按鈕。  
  
 `style`  
 指定的索引標籤的樣式。 使用`STYLE_3D_SCROLLED`一般索引標籤或`STYLE_3D_ONENOTE`Microsoft OneNote 索引標籤。  
  
 `bTabCustomTooltips`  
 指定是否啟用自訂的工具提示。  
  
 `bActiveTabCloseButton`  
 如果`TRUE`、**關閉**按鈕將顯示使用中 索引標籤上而不是最右邊的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟用或停用 MDI 框架視窗的 MDI 索引標籤功能。 啟用時，所有的子視窗會顯示為索引標籤。  
  
 索引標籤可位於頂端或底部的框架中，根據參數設定`tabLocation`。 您可以指定`CMFCTabCtrl::LOCATION_BOTTOM`（預設值） 或`CMFCTabCtrl::LOCATION_TOP`。  
  
 如果`bTabCustomTooltips`是`TRUE`、`AFX_WM_ON_GET_TAB_TOOLTIP`訊息會傳送到主框架視窗。 您的程式碼可以處理這個訊息，並提供自訂的工具提示與 MDI 索引標籤的架構。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnableMDITabs`用於[MDITabsDemo 範例︰ MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo #&3;](../../mfc/reference/codesnippet/cpp/cmdiframewndex-class_8.cpp)]  
  
##  <a name="a-nameenablemditabslastactiveactivationa--cmdiframewndexenablemditabslastactiveactivation"></a><a name="enablemditabslastactiveactivation"></a>CMDIFrameWndEx::EnableMDITabsLastActiveActivation  
 指定當使用者關閉目前的索引標籤是否要開啟 [最後一個使用中] 索引標籤。  
  
```  
void EnableMDITabsLastActiveActivation(BOOL bLastActiveTab=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bLastActiveTab`  
 如果`TRUE`，啟用 「 啟用 」 的最後一個使用中的索引標籤。 如果`FALSE`，停用啟動過程的最後一個使用中的索引標籤。  
  
### <a name="remarks"></a>備註  
 有兩種方式可以關閉使用中的索引標籤時，請開啟索引標籤︰  
  
-   啟用 [下一步] 索引標籤。  
  
-   啟動前一個作用中的索引標籤。  
  
 預設實作會使用第一種方式。  
  
 使用`EnableMDITabsLastActiveActivation`若要啟用索引標籤上啟用的第二個方法。 它會模擬開啟視窗的 MDI 子視窗的方式。  
  
##  <a name="a-nameenablepanemenua--cmdiframewndexenablepanemenu"></a><a name="enablepanemenu"></a>CMDIFrameWndEx::EnablePaneMenu  
 啟用或停用自動建立及管理的快顯窗格功能表會顯示應用程式窗格的清單。  
  
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
 如果`TRUE`，啟用自動處理窗格功能表; 如果`FALSE`，停用自動處理。  
  
 [in] `uiCustomizeCmd`  
 命令 ID 的**自訂**功能表項目。 這個功能表項目通常被加到窗格的清單結尾。  
  
 [in] `strCustomizeLabel`  
 要顯示的文字**自訂**（適用於當地語系化） 的功能表項目。  
  
 [in] `uiViewToolbarsMenuEntryID`  
 指定開啟 [窗格] 功能表的工具列功能表項目識別碼。 這通常是**工具列**子功能表中的**檢視**功能表。  
  
 [in] `bContextMenuShowsToolbarsOnly`  
 如果`TRUE`，窗格功能表會顯示工具列的清單。 如果`FALSE`，功能表就會顯示的工具列和停駐列清單。  
  
 [in] `bViewMenuShowsToolbarsOnly`  
 如果`TRUE`，窗格功能表會顯示工具列的清單。 如果`FALSE`，功能表就會顯示的工具列和停駐列清單。  
  
### <a name="remarks"></a>備註  
 窗格的快顯功能表會顯示應用程式的窗格的清單，並讓使用者顯示或隱藏個別的窗格。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnablePaneMenu`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&9;](../../mfc/codesnippet/cpp/cmdiframewndex-class_9.cpp)]  
  
##  <a name="a-nameenablewindowsdialoga--cmdiframewndexenablewindowsdialog"></a><a name="enablewindowsdialog"></a>CMDIFrameWndEx::EnableWindowsDialog  
 插入功能表項目的命令 ID 會呼叫[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)對話方塊。  
  
```  
void EnableWindowsDialog(
    UINT uiMenuId,  
    LPCTSTR lpszMenuText,  
    BOOL bShowAllways=FALSE,  
    BOOL bShowHelpButton=FALSE);

 
void EnableWindowsDialog(
    UINT uiMenuId,  
    UINT uiMenuTextResId,  
    BOOL bShowAllways=FALSE,  
    BOOL bShowHelpButton=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiMenuId`  
 指定功能表上的資源識別碼。  
  
 [in] `lpszMenuText`  
 指定項目的文字。  
  
 [in] `bShowHelpButton`  
 指定是否要顯示**協助**windows 的 [管理] 對話方塊上的按鈕。  
  
 [in] `uiMenuTextResId`  
 包含項目的文字字串的字串資源識別碼。  
  
### <a name="remarks"></a>備註  
 使用此方法來插入其命令呼叫 MDI 子視窗管理對話方塊中的功能表項目 ( [CMFCWindowsManagerDialog 類別](../../mfc/reference/cmfcwindowsmanagerdialog-class.md))。 新的項目插入所指定的功能表`uiMenuId`。 呼叫`EnableWindowsDialog`當處理`WM_CREATE`訊息。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`EnableWindowsDialog`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&10;](../../mfc/codesnippet/cpp/cmdiframewndex-class_10.cpp)]  
  
##  <a name="a-namegetactivepopupa--cmdiframewndexgetactivepopup"></a><a name="getactivepopup"></a>CMDIFrameWndEx::GetActivePopup  
 將指標傳回到目前顯示的快顯功能表。  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用中的快顯功能表中，指標`NULL`如果快顯功能表沒有作用。  
  
### <a name="remarks"></a>備註  
 使用此函式取得的指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)目前顯示的物件。  
  
##  <a name="a-namegetdefaultresida--cmdiframewndexgetdefaultresid"></a><a name="getdefaultresid"></a>CMDIFrameWndEx::GetDefaultResId  
 傳回的 MDI 框架視窗的共用資源的識別碼。  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資源識別碼值。 0，如果框架視窗有沒有功能表列。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回載入 MDI 框架視窗時所指定的資源識別碼[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)。  
  
##  <a name="a-namegetmditabgroupsa--cmdiframewndexgetmditabgroups"></a><a name="getmditabgroups"></a>CMDIFrameWndEx::GetMDITabGroups  
 傳回一份 MDI 索引視窗。  
  
```  
const CObList& GetMDITabGroups() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含一份索引標籤式視窗。 不要儲存或修改清單。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法來存取索引標籤式視窗的清單。 如果您想要變更或查詢的個別索引標籤式視窗的一些參數，它可以是很有幫助。  
  
##  <a name="a-namegetmditabsa--cmdiframewndexgetmditabs"></a><a name="getmditabs"></a>CMDIFrameWndEx::GetMDITabs  
 傳回加上底線的索引標籤式視窗的參考。  
  
```  
CMFCTabCtrl& GetMDITabs();
```  
  
### <a name="return-value"></a>傳回值  
 加上底線的索引標籤式視窗的參考。  
  
##  <a name="a-namegetmditabscontextmenualloweditemsa--cmdiframewndexgetmditabscontextmenualloweditems"></a><a name="getmditabscontextmenualloweditems"></a>CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems  
 傳回旗標的組合，用來判定哪些作業有效啟用 MDI 索引標籤式群組功能。  
  
```  
DWORD GetMDITabsContextMenuAllowedItems();
```  
  
### <a name="return-value"></a>傳回值  
 下列旗標的位元 OR 組合︰  
  
- `BCGP_MDI_CREATE_VERT_GROUP`-可以建立垂直索引標籤群組。  
  
- `BCGP_MDI_CREATE_HORZ_GROUP`-可以建立水平索引標籤群組。  
  
- `BCGP_MDI_CAN_MOVE_PREV`-可以將索引標籤移至前一個索引標籤群組。  
  
- `BCGP_MDI_CAN_MOVE_NEXT`-可以移至下一步 索引標籤群組中 索引標籤。  
  
### <a name="remarks"></a>備註  
 啟用 MDI 索引標籤式群組功能時，您必須知道特定視窗的索引標籤上允許哪些作業。 這個方法會分析目前的索引標籤式視窗配置，並傳回旗標的組合，可以用來建置，比方說，快顯功能表。  
  
 當所有的索引標籤式的視窗會垂直對齊，或只有一個索引標籤式的視窗時，您可以建立新的垂直索引標籤群組。  
  
 水平對齊所有索引標籤式的視窗時，或只有一個索引標籤式的視窗時，您可以建立新的水平索引標籤群組。  
  
 只有當索引標籤式視窗中有多個索引標籤，您可以移至上一個群組索引標籤。  
  
 只有當索引標籤式視窗中有多個索引標籤，您可以將索引標籤移到下一個群組中。  
  
##  <a name="a-namegetmenubara--cmdiframewndexgetmenubar"></a><a name="getmenubar"></a>CMDIFrameWndEx::GetMenuBar  
 傳回附加到的框架視窗的功能表列物件的指標。  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能表列物件的指標。  
  
##  <a name="a-namegetpanea--cmdiframewndexgetpane"></a><a name="getpane"></a>CMDIFrameWndEx::GetPane  
 將指標傳回至窗格中具有指定之的控制項 id。  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果存在具有指定之的控制項 ID，窗格指標。 否則為 `NULL`。  
  
##  <a name="a-namegetribbonbara--cmdiframewndexgetribbonbar"></a><a name="getribbonbar"></a>CMDIFrameWndEx::GetRibbonBar  
 擷取框架的功能區列控制項。  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)框架。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettearoffbarsa--cmdiframewndexgettearoffbars"></a><a name="gettearoffbars"></a>CMDIFrameWndEx::GetTearOffBars  
 傳回一份 tear-off 功能表。  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含的指標集合`CPane`-衍生撕狀態的物件。  
  
### <a name="remarks"></a>備註  
 `CMDIFrameWndEx`會維護一堆 tear-off 功能表。 使用這個方法來擷取這份清單的參考。  
  
##  <a name="a-namegettoolbarbuttontooltiptexta--cmdiframewndexgettoolbarbuttontooltiptext"></a><a name="gettoolbarbuttontooltiptext"></a>CMDIFrameWndEx::GetToolbarButtonToolTipText  
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
  
##  <a name="a-nameinsertpanea--cmdiframewndexinsertpane"></a><a name="insertpane"></a>CMDIFrameWndEx::InsertPane  
 連接管理員會向指定的窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 要插入窗格指標。  
  
 [in] `pTarget`  
 指標之前或之後要插入窗格的窗格。  
  
 [in] `bAfter`  
 如果`TRUE`，`pControlBar`後面插入`pTarget`。 如果`FALSE`，`pControlBar`之前，插入`pTarget`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功註冊的工作窗格中，`FALSE`如果窗格已註冊到停駐的管理員。  
  
### <a name="remarks"></a>備註  
 使用這個方法來通知窗格中所指定的停駐管理員`pControlBar`。 停駐管理員將對齊此窗格根據窗格的對齊和停駐管理員的內部清單中的位置。  
  
##  <a name="a-nameisfullscreena--cmdiframewndexisfullscreen"></a><a name="isfullscreen"></a>CMDIFrameWndEx::IsFullScreen  
 判斷是否在全螢幕模式中的框架視窗。  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架視窗會以全螢幕模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫設定全螢幕模式[CMDIFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)方法。  
  
##  <a name="a-nameismditabbedgroupa--cmdiframewndexismditabbedgroup"></a><a name="ismditabbedgroup"></a>CMDIFrameWndEx::IsMDITabbedGroup  
 指定是否啟用 MDI 索引標籤式群組功能。  
  
```  
BOOL IsMDITabbedGroup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用 MDI 索引標籤式群組功能。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 若要判斷是否啟用一般 MDI 索引標籤或 MDI 索引標籤式群組功能，請使用[CMDIFrameWndEx::AreMDITabs](#aremditabs)。  
  
##  <a name="a-nameismemberofmditabgroupa--cmdiframewndexismemberofmditabgroup"></a><a name="ismemberofmditabgroup"></a>CMDIFrameWndEx::IsMemberOfMDITabGroup  
 判斷指定的索引標籤式的視窗是否為 MDI 索引標籤式群組中的視窗的清單中。  
  
```  
BOOL IsMemberOfMDITabGroup(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 索引標籤式視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的索引標籤式的視窗是構成 MDI 索引標籤式群組的索引標籤式視窗的清單。 否則`FALSE`。  
  
##  <a name="a-nameismenubaravailablea--cmdiframewndexismenubaravailable"></a><a name="ismenubaravailable"></a>CMDIFrameWndEx::IsMenuBarAvailable  
 決定框架視窗是否有功能表列。  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能表列物件的指標不`NULL`，否則為`FALSE`。  
  
##  <a name="a-nameispointneardocksitea--cmdiframewndexispointneardocksite"></a><a name="ispointneardocksite"></a>CMDIFrameWndEx::IsPointNearDockSite  
 判斷指定的點是否停駐位置附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 螢幕座標中指定的點。  
  
 [in] `dwBarAlignment`  
 指定的點是附近的邊緣。 可能的值為`CBRS_ALIGN_LEFT`， `CBRS_ALIGN_RIGHT`， `CBRS_ALIGN_TOP`，並`CBRS_ALIGN_BOTTOM`  
  
 [in] `bOuterEdge`  
 `TRUE`如果點很近外框的停駐位置。`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果點附近的停駐位置。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 重點是停駐位置附近時中設定連接管理員中的敏感度。 預設區分大小寫為 15 像素。  
  
##  <a name="a-nameisprintpreviewa--cmdiframewndexisprintpreview"></a><a name="isprintpreview"></a>CMDIFrameWndEx::IsPrintPreview  
 決定框架視窗是否處於預覽列印模式。  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架視窗處於預覽列印模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadframea--cmdiframewndexloadframe"></a><a name="loadframe"></a>CMDIFrameWndEx::LoadFrame  
 建立框架視窗從資源資訊。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIDResource`  
 框架視窗相關聯的共用資源的識別碼。  
  
 [in] `dwDefaultStyle`  
 框架視窗樣式。  
  
 [in] `pParentWnd`  
 父框架的指標。  
  
 [in] `pContext`  
 指標[CCreateContext 結構](../../mfc/reference/ccreatecontext-structure.md)。 這個參數可以是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功，否則`FALSE`。  
  
##  <a name="a-nameloadmdistatea--cmdiframewndexloadmdistate"></a><a name="loadmdistate"></a>Cmdiframewndex:: Loadmdistate  
 載入指定的 MDI 索引標籤式群組的配置和先前開啟的文件的清單。  
  
```  
virtual BOOL LoadMDIState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定設定檔名稱。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果載入成功。`FALSE`如果載入失敗，或沒有載入的資料。  
  
### <a name="remarks"></a>備註  
 若要載入或儲存 MDI 索引標籤和群組的狀態和開啟文件的清單，執行下列作業︰  
  
-   呼叫[CMDIFrameWndEx::SaveMDIState](#savemdistate)關閉主框架時  
  
-   呼叫[cmdiframewndex:: Loadmdistate](#loadmdistate)建立主要畫面格時。 建議您將這個呼叫是主要畫面格第一次顯示之前。 新增`CWinAppEx::EnableLoadWindowPlacement``(FALSE);`之前`pMainFrame->LoadFrame (IDR_MAINFRAME);.`新增`CBCGPWorkspace::ReloadWindowPlacement``(pMainFrame);`呼叫之後`LoadMDIState`主框架顯示儲存在登錄中的位置。  
  
-   覆寫`GetDocumentName`中`CMDIChildWndEx`-衍生類別，如果您的應用程式會顯示不會儲存為檔案的文件。 傳回的字串會儲存在登錄中，做為文件識別碼。 基底實作[CMDIChildWndEx::GetDocumentName](../../mfc/reference/cmdichildwndex-class.md#getdocumentname)傳回值，這個值取自[CDocument::GetPathName](../../mfc/reference/cdocument-class.md#getpathname)。  
  
-   覆寫[CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow)時從登錄載入正確建立文件。 第一個參數是字串，`GetDocumentName`傳回。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`LoadMDIState`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&11;](../../mfc/codesnippet/cpp/cmdiframewndex-class_11.cpp)]  
  
##  <a name="a-namemditabmovetonextgroupa--cmdiframewndexmditabmovetonextgroup"></a><a name="mditabmovetonextgroup"></a>CMDIFrameWndEx::MDITabMoveToNextGroup  
 將作用中的索引標籤從目前使用中的索引標籤式視窗移至下一個或前一個索引群組。  
  
```  
void MDITabMoveToNextGroup(BOOL bNext=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNext`  
 如果`TRUE`，移至下一個索引標籤式群組的索引標籤。 如果`FALSE`，將它移至前一個索引標籤式群組。  
  
##  <a name="a-namemditabnewgroupa--cmdiframewndexmditabnewgroup"></a><a name="mditabnewgroup"></a>CMDIFrameWndEx::MDITabNewGroup  
 建立新的索引標籤式的群組具有單一視窗。  
  
```  
void MDITabNewGroup(BOOL bVert=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bVert`  
 指定新群組對齊方式。 如果`TRUE`，新的群組會垂直對齊。 如果`FALSE`，新的群組水平對齊。  
  
### <a name="remarks"></a>備註  
 使用此函式來建立新的索引標籤式視窗 （新的索引標籤式群組），然後為其新增第一個索引標籤。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`MDITabNewGroup`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&12;](../../mfc/codesnippet/cpp/cmdiframewndex-class_12.cpp)]  
  
##  <a name="a-namembcancovertcontrolbartomdichilda--cmdiframewndexmbcancovertcontrolbartomdichild"></a><a name="m_bcancovertcontrolbartomdichild"></a>CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild  
 指定是否停駐窗格可以轉換成 MDI 子視窗。  
  
```  
BOOL m_bCanCovertControlBarToMDIChild;  
```  
  
### <a name="remarks"></a>備註  
 表示停駐控制列是否可轉換為 MDI 子視窗。 如果這個旗標`TRUE`，架構會處理轉換的自動當使用者選取**索引標籤式文件**命令。 旗標受到保護，且您必須明確啟用此選項設定的`m_bCanCovertControlBarToMDIChild`建構函式中`CMDIFrameWndEx`-衍生的類別，或藉由覆寫`CanConvertControlBarToMDIChild`。  
  
 預設值是 `FALSE`。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`m_bCanCovertControlBarToMDIChild`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&13;](../../mfc/codesnippet/cpp/cmdiframewndex-class_2.cpp)]  
  
##  <a name="a-namembdisablesetredrawa--cmdiframewndexmbdisablesetredraw"></a><a name="m_bdisablesetredraw"></a>CMDIFrameWndEx::m_bDisableSetRedraw  
 啟用或停用的 MDI 子視窗的重繪最佳化。  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableSetRedraw;  
```  
  
### <a name="remarks"></a>備註  
 預設值是 `TRUE`。  
  
 若要設定此旗標`FALSE`如果您想要最佳化的 MDI 子視窗重繪作業。 在此情況下，架構會呼叫`SetRedraw (FALSE)`主要畫面格應用程式會變更使用中的索引標籤。  
  
 這個旗標可能會導致不必要的影響 （例如背景應用程式，就會顯示）。 因此我們建議您變更預設值，只有在遇到明顯閃爍在啟動過程中 MDI 索引標籤。  
  
##  <a name="a-namenegotiateborderspacea--cmdiframewndexnegotiateborderspace"></a><a name="negotiateborderspace"></a>CMDIFrameWndEx::NegotiateBorderSpace  
 會在框架視窗的框線空間交涉 OLE 就地啟用期間。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>參數  
 [in] `nBorderCmd`  
 列舉中的以下值的其中一個`CFrameWnd::BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 [in、out] `lpRectBorder`  
 指標[RECT 結構](../../mfc/reference/rect-structure1.md)或[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)物件，指定框線的座標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法是實作的 OLE 框線空間交涉。  
  
##  <a name="a-nameonclosedockingpanea--cmdiframewndexonclosedockingpane"></a><a name="onclosedockingpane"></a>CMDIFrameWndEx::OnCloseDockingPane  
 當使用者按一下時，由框架呼叫**關閉**可停駐窗格上的按鈕。  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 [關閉] 窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以關閉停駐窗格。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫此方法以處理隱藏停駐窗格。 傳回`FALSE`如果您想要防止在隱藏停駐窗格。  
  
 預設實作不做任何動作，並傳回`TRUE`。  
  
##  <a name="a-nameoncloseminiframea--cmdiframewndexoncloseminiframe"></a><a name="oncloseminiframe"></a>CMDIFrameWndEx::OnCloseMiniFrame  
 當使用者按一下時，由框架呼叫**關閉**浮動的迷你框架視窗上的按鈕。  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd*);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 正在關閉迷你框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以關閉浮動的迷你框架視窗。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫此方法以處理隱藏浮動迷你框架視窗。 傳回`FALSE`如果您想要防止在隱藏浮動的迷你框架視窗。  
  
 預設實作不做任何動作，並傳回`TRUE`。  
  
##  <a name="a-nameonclosepopupmenua--cmdiframewndexonclosepopupmenu"></a><a name="onclosepopupmenu"></a>CMDIFrameWndEx::OnClosePopupMenu  
 使用中的快顯功能表上處理時，由框架呼叫`WM_DESTROY`訊息。  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPopup`  
 快顯功能表上的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，如果您想要處理的通知[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)時處理這些物件屬於 MDI 框架視窗物件`WM_DESTROY`訊息。  
  
##  <a name="a-nameoncmdmsga--cmdiframewndexoncmdmsg"></a><a name="oncmdmsg"></a>CMDIFrameWndEx::OnCmdMsg  
 傳送和分派命令訊息，並以更新命令使用者介面物件的架構所呼叫。  
  
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
 識別命令通知程式碼。 請參閱[CCmdTarget::OnCmdMsg](../../mfc/reference/ccmdtarget-class.md#oncmdmsg)如需有關值`nCode`。  
  
 [in] `pExtra`  
 依據的值來使用`nCode`。 請參閱[CCmdTarget::OnCmdMsg](../../mfc/reference/ccmdtarget-class.md#oncmdmsg)如需詳細資訊`pExtra`。  
  
 [in、out] `pHandlerInfo`  
 通常，這個參數應該是`NULL`。如果不是`NULL`，`OnCmdMsg`填入`pTarget`和`pmf`成員`pHandlerInfo`結構，而不是分派命令。  
  
### <a name="return-value"></a>傳回值  
 處理訊息的; 如果為非零否則為 0。  
  
##  <a name="a-nameondrawmenuimagea--cmdiframewndexondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMDIFrameWndEx::OnDrawMenuImage  
 架構在繪製與功能表項目相關聯的映像時所呼叫。  
  
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
 指標 [功能表] 按鈕。  
  
 [in] `rectImage`  
 週框的影像。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法會繪製影像。 預設實作會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，如果您想要自訂的功能表項目所擁有的功能表列屬於影像轉譯`CMDIFrameWndEx`-衍生物件。 預設實作不做任何動作。  
  
##  <a name="a-nameondrawmenulogoa--cmdiframewndexondrawmenulogo"></a><a name="ondrawmenulogo"></a>CMDIFrameWndEx::OnDrawMenuLogo  
 由架構呼叫時[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)處理程序`WM_PAINT`訊息。  
  
```  
virtual void OnDrawMenuLogo(
    CDC*, 
    CMFCPopupMenu*, 
    const CRect&);
```  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來顯示屬於所擁有的功能表列的快顯功能表上的標誌`CMDIFrameWndEx`-衍生物件。 預設實作不做任何動作。  
  
##  <a name="a-nameonerasemdiclientbackgrounda--cmdiframewndexonerasemdiclientbackground"></a><a name="onerasemdiclientbackground"></a>CMDIFrameWndEx::OnEraseMDIClientBackground  
 MDI 框架視窗程序時，由框架呼叫`WM_ERASEBKGND`訊息。  
  
```  
virtual BOOL OnEraseMDIClientBackground(CDC*);
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應用程式處理訊息，並清除背景。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，如果您想要處理`WM_ERASEBKGND`中訊息`CMDIFrameWndEx`-衍生的類別。  
  
##  <a name="a-nameonmenubuttontoolhittesta--cmdiframewndexonmenubuttontoolhittest"></a><a name="onmenubuttontoolhittest"></a>CMDIFrameWndEx::OnMenuButtonToolHitTest  
 由架構呼叫時[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件處理程序`WM_NCHITTEST`訊息。  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 工具列按鈕。  
  
 [輸出] `pTI`  
 指標[TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256)結構。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應用程式會填入`pTI`參數。 預設實作會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果您想要提供特定的功能表項目，為工具提示的相關資訊，請覆寫這個方法。 預設實作不做任何動作。  
  
##  <a name="a-nameonmoveminiframea--cmdiframewndexonmoveminiframe"></a><a name="onmoveminiframe"></a>CMDIFrameWndEx::OnMoveMiniFrame  
 若要移動的迷你框架視窗，架構呼叫。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 迷你框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功，否則`FALSE`。  
  
##  <a name="a-nameonsetpreviewmodea--cmdiframewndexonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CMDIFrameWndEx::OnSetPreviewMode  
 設定應用程式的主框架視窗預覽列印模式。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPreview`  
 如果`TRUE`，設定預覽列印模式。 如果`FALSE`，取消預覽模式。  
  
 [in] `pState`  
 指標`CPrintPreviewState`結構。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫[CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode)。  
  
##  <a name="a-nameonshowcustomizepanea--cmdiframewndexonshowcustomizepane"></a><a name="onshowcustomizepane"></a>CMDIFrameWndEx::OnShowCustomizePane  
 啟動快速自訂窗格時，由架構呼叫。  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPane`  
 快速自訂的窗格指標。  
  
 [in] `uiToolbarID`  
 控制項 ID 的工具列來自訂。  
  
### <a name="return-value"></a>傳回值  
 這個方法一律會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 快速自訂的窗格是當使用者按一下 [開啟] 功能表**自訂**工具列上。  
  
 在快速自訂的窗格中進行變更的衍生類別中，這個方法會覆寫。  
  
##  <a name="a-nameonshowmditabcontextmenua--cmdiframewndexonshowmditabcontextmenu"></a><a name="onshowmditabcontextmenu"></a>CMDIFrameWndEx::OnShowMDITabContextMenu  
 由架構呼叫其中一個索引標籤上顯示快顯功能表之前。 針對 MDI 索引標籤式群組才有效。  
  
```  
virtual BOOL OnShowMDITabContextMenu(
    CPoint point,  
    DWORD dwAllowedItems,  
    BOOL bTabDrop);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 螢幕座標中的功能表中的位置。  
  
 [in] `dwAllowedItems`  
 位元 OR 組合的旗標，指出目前的索引標籤允許的動作︰  
  
- `BCGP_MDI_CREATE_VERT_GROUP`-可以建立垂直索引標籤群組。  
  
- `BCGP_MDI_CREATE_HORZ_GROUP`-可以建立水平索引標籤群組。  
  
- `BCGP_MDI_CAN_MOVE_PREV`-可以將索引標籤移至前一個索引標籤群組。  
  
- `BCGP_MDI_CAN_MOVE_NEXT`-可以移至下一步 索引標籤群組中 索引標籤。  
  
- `BCGP_MDI_CAN_BE_DOCKED`-索引標籤式文件切換停駐狀態 （如索引標籤式文件相關）。  
  
 [in] `bTabDrop`  
 `TRUE`若要顯示的結果 索引標籤拖曳到另一個索引標籤式群組功能表。 `FALSE`若要顯示為目前使用中 索引標籤上的快顯功能表的功能表。  
  
### <a name="return-value"></a>傳回值  
 覆寫這個方法在[CBCGPMDIFrameWnd](../../mfc/reference/cmdiframewndex-class.md)-衍生的類別。  
  
### <a name="remarks"></a>備註  
 如果您不會處理`OnShowMDITabContextMenu`，將不會顯示快顯功能表。 此函式由產生**MFC 應用程式精靈**當您啟用 MDI 索引標籤式群組功能。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`OnShowMDITabContextMenu`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&14;](../../mfc/codesnippet/cpp/cmdiframewndex-class_13.cpp)]  
  
##  <a name="a-nameonshowpanesa--cmdiframewndexonshowpanes"></a><a name="onshowpanes"></a>CMDIFrameWndEx::OnShowPanes  
 若要顯示或隱藏窗格架構呼叫。  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 `TRUE`若要顯示的窗格，`FALSE`隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果因而呼叫這個方法，變更窗格的狀態`FALSE`窗格會在中所指定的狀態已經是`bShow`。 例如，如果隱藏的窗格和`bShow`是`FALSE`，則傳回值是`FALSE`。  
  
### <a name="remarks"></a>備註  
 預設實作會移除最上層框架視窗的工具列。  
  
 如果[CDockingManager::m_bHideDockingBarsInContainerMode](../../mfc/reference/cdockingmanager-class.md#m_bhidedockingbarsincontainermode)是`TRUE`（預設值），將隱藏所有停駐窗格。  
  
##  <a name="a-nameonshowpopupmenua--cmdiframewndexonshowpopupmenu"></a><a name="onshowpopupmenu"></a>CMDIFrameWndEx::OnShowPopupMenu  
 開啟快顯功能表時，由架構呼叫。  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu*);
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果要顯示為快顯功能表。 否則為 `FALSE`。 預設實作會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果您想要實作在快顯功能表啟動時的特殊處理，覆寫這個方法。 例如，如果您想要將規則功能表項目變更為色彩功能表按鈕，設定撕列等等。  
  
 預設實作不做任何動作。  
  
##  <a name="a-nameonsizemdiclienta--cmdiframewndexonsizemdiclient"></a><a name="onsizemdiclient"></a>CMDIFrameWndEx::OnSizeMDIClient  
 架構的用戶端 MDI 視窗大小變更時呼叫。  
  
```  
virtual void OnSizeMDIClient(
    const CRect& rectOld,  
    const CRect& rectNew);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectOld`  
 目前的 MDI 用戶端視窗大小。  
  
 [in] `rectNew`  
 新的 MDI 用戶端視窗大小。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameontearoffmenua--cmdiframewndexontearoffmenu"></a><a name="ontearoffmenu"></a>CMDIFrameWndEx::OnTearOffMenu  
 架構在啟動有分割列的功能表時所呼叫。  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPopup`  
 快顯功能表上的指標。  
  
 [in] `pBar`  
 撕下列指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`若要允許快顯功能表與撕下列進行啟動。否則`FALSE`。 預設為 `TRUE`。  
  
### <a name="remarks"></a>備註  
 當您想要實作撕列特殊的設定會覆寫這個函式。 預設實作不做任何動作。  
  
##  <a name="a-nameonupdateframemenua--cmdiframewndexonupdateframemenu"></a><a name="onupdateframemenu"></a>CMDIFrameWndEx::OnUpdateFrameMenu  
 若要更新 [框架] 功能表架構呼叫。  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenuAlt`  
 功能表的控點。  
  
##  <a name="a-namepanefrompointa--cmdiframewndexpanefrompoint"></a><a name="panefrompoint"></a>CMDIFrameWndEx::PaneFromPoint  
 傳回包含指定的點的停駐窗格。  
  
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
 （在螢幕座標表示） 的點。  
  
 [in] `nSensitivity`  
 已檢查的每個窗格的視窗矩形會在所有方向中放大，此值。  
  
 [in] `bExactBar`  
 如果`TRUE`、`nSensitivity`參數會被忽略。  
  
 [in] `pRTCBarType`  
 如果非`NULL`，此方法會逐一查看指定之型別的窗格。  
  
 [輸出] `dwAlignment`  
 如果找到一個窗格，則這個參數會指定哪一側窗格的最接近指定位置。  
  
### <a name="return-value"></a>傳回值  
 停駐窗格的指標或`NULL`如果控制項包含所指定的點`point`。  
  
### <a name="remarks"></a>備註  
 呼叫重新導向至[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)。 請參閱[CDockingManager::ControlBarFromPoint](../../mfc/reference/cdockingmanager-class.md#panefrompoint)如需詳細資訊。  
  
##  <a name="a-namerecalclayouta--cmdiframewndexrecalclayout"></a><a name="recalclayout"></a>CMDIFrameWndEx::RecalcLayout  
 若要重新計算框架視窗的版面配置架構呼叫。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNotify`  
 決定框架視窗的使用中就地項目是否要接收的配置變更通知。 如果`TRUE`，項目就會通知否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。  
  
##  <a name="a-nameremovepanefromdockmanagera--cmdiframewndexremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CMDIFrameWndEx::RemovePaneFromDockManager  
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
 要移除的窗格指標。  
  
 [in] `bDestroy`  
 `TRUE`要終結 [移除] 窗格。 `FALSE`若要摧毀它。  
  
 [in] `bAdjustLayout`  
 `TRUE`若要立即調整停駐配置。 如果`FALSE`，調整 就會發生只重繪事件發生時因為其他原因 （使用者調整視窗大小時，拖曳主要畫面格等等）。  
  
 [in] `bAutoHide`  
 `TRUE`若要移除自動隱藏窗格的清單 窗格。 `FALSE`若要移除規則 窗格的清單 窗格。  
  
 [in] `pBarReplacement`  
 指標，會取代 [移除] 窗格的窗格。  
  
### <a name="remarks"></a>備註  
 您必須向要參加的停駐配置的停駐管理員的每個窗格。 使用[CMDIFrameWndEx::AddPane](#addpane)或[CMDIFrameWndEx::InsertPane](#insertpane)註冊窗格。  
  
 當窗格不再是框架視窗停駐配置的一部分，請使用此方法。  
  
##  <a name="a-namesavemdistatea--cmdiframewndexsavemdistate"></a><a name="savemdistate"></a>CMDIFrameWndEx::SaveMDIState  
 儲存目前的 MDI 索引標籤式群組的配置和先前所開啟的文件的清單。  
  
```  
virtual BOOL SaveMDIState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定設定檔名稱。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果儲存成功。`FALSE`如果，儲存作業失敗。  
  
### <a name="remarks"></a>備註  
 若要載入或儲存 MDI 索引標籤和群組的狀態和開啟文件的清單，執行下列作業︰  
  
-   呼叫`SaveMDIState`關閉主框架時  
  
-   呼叫[cmdiframewndex:: Loadmdistate](#loadmdistate)建立主要畫面格時。 此呼叫的建議的位置是主要畫面格第一次顯示之前。  
  
-   呼叫`CWinAppEx::EnableLoadWindowPlacement(FALSE);`之前`pMainFrame->LoadFrame (IDR_MAINFRAME);`  
  
-   呼叫`CWinAppEx::ReloadWindowPlacement``(pMainFrame)`之後`LoadMDIState`主框架顯示儲存在登錄中的位置。  
  
-   覆寫`GetDocumentName`中`CMDIChildWndEx`-衍生類別，如果您的應用程式會顯示不會儲存為檔案的文件。 傳回的字串會儲存在登錄中，做為文件識別項。 如需詳細資訊，請參閱[CMDIChildWndEx::GetDocumentName](../../mfc/reference/cmdichildwndex-class.md#getdocumentname)。  
  
-   覆寫[CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow)正確建立文件，它們會從登錄載入時。 參數可`CreateDocumentWindow`是字串，`GetDocumentName`稍早傳回。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`SaveMDIState`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&15;](../../mfc/codesnippet/cpp/cmdiframewndex-class_14.cpp)]  
  
##  <a name="a-namesetprintpreviewframea--cmdiframewndexsetprintpreviewframe"></a><a name="setprintpreviewframe"></a>CMDIFrameWndEx::SetPrintPreviewFrame  
 設定預覽列印框架視窗。  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 預覽列印框架視窗的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetuptoolbarmenua--cmdiframewndexsetuptoolbarmenu"></a><a name="setuptoolbarmenu"></a>CMDIFrameWndEx::SetupToolbarMenu  
 使用者定義的項目取代成空的項目修改工具列物件。  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>參數  
 [in] `menu`  
 參考[CMenu 類別](../../mfc/reference/cmenu-class.md)要修改的物件。  
  
 [in] `uiViewUserToolbarCmdFirst`  
 指定的使用者定義的第一個命令。  
  
 [in] `uiViewUserToolbarCmdLast`  
 指定的使用者定義的最後一個命令。  
  
##  <a name="a-nameshowfullscreena--cmdiframewndexshowfullscreen"></a><a name="showfullscreen"></a>CMDIFrameWndEx::ShowFullScreen  
 切換至全螢幕模式一般模式從主框架。  
  
```  
void ShowFullScreen();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameshowpanea--cmdiframewndexshowpane"></a><a name="showpane"></a>CMDIFrameWndEx::ShowPane  
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
 顯示或隱藏窗格的指標。  
  
 [in] `bShow`  
 `TRUE`若要顯示的窗格。 `FALSE`若要隱藏窗格。  
  
 [in] `bDelay`  
 `TRUE`若要延遲的停駐配置的重新計算。 `FALSE`若要立即重新計算停駐配置。  
  
 [in] `bActivate`  
 `TRUE`若要顯示的窗格應該為使用中。 `FALSE`若要顯示為非作用中 窗格。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以顯示或隱藏窗格。 請勿使用`ShowWindow`停駐窗格。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`ShowPane`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&16;](../../mfc/codesnippet/cpp/cmdiframewndex-class_15.cpp)]  
  
##  <a name="a-nameshowwindowsdialoga--cmdiframewndexshowwindowsdialog"></a><a name="showwindowsdialog"></a>CMDIFrameWndEx::ShowWindowsDialog  
 建立[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)方塊，並將它開啟。  
  
```  
void ShowWindowsDialog();
```  
  
### <a name="example"></a>範例  
 下列範例將示範如何`ShowWindowsDialog`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&18;](../../mfc/codesnippet/cpp/cmdiframewndex-class_16.cpp)]  
  
##  <a name="a-nametabbeddocumenttocontrolbara--cmdiframewndextabbeddocumenttocontrolbar"></a><a name="tabbeddocumenttocontrolbar"></a>CMDIFrameWndEx::TabbedDocumentToControlBar  
 將指定的索引標籤式文件轉換為停駐窗格。  
  
```  
virtual BOOL TabbedDocumentToControlBar(CMDIChildWndEx* pMDIChildWnd);
```  
  
### <a name="parameters"></a>參數  
 `pMDIChildWnd`  
 包含的停駐窗格的 MDI 子視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`方法成功，則`FALSE`失敗。  
  
### <a name="remarks"></a>備註  
 若要將轉換的停駐窗格的索引標籤式文件中使用這個方法。 索引標籤式文件必須已建立使用[CMDIFrameWndEx::ControlBarToTabbedDocument](#controlbartotabbeddocument)。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`TabbedDocumentToControlBar`用於[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&19;](../../mfc/codesnippet/cpp/cmdiframewndex-class_17.cpp)]  
  
##  <a name="a-nameupdatecaptiona--cmdiframewndexupdatecaption"></a><a name="updatecaption"></a>CMDIFrameWndEx::UpdateCaption  
 若要更新的視窗框架標題架構呼叫。  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameupdatemditabbedbarsiconsa--cmdiframewndexupdatemditabbedbarsicons"></a><a name="updatemditabbedbarsicons"></a>CMDIFrameWndEx::UpdateMDITabbedBarsIcons  
 設定每個 MDI 索引標籤式窗格的圖示。  
  
```  
void UpdateMDITabbedBarsIcons();
```  
  
##  <a name="a-namewinhelpa--cmdiframewndexwinhelp"></a><a name="winhelp"></a>CMDIFrameWndEx::WinHelp  
 架構所呼叫以起始 WinHelp 應用程式或內容說明。  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwData`  
 指定資料為 `nCmd`所指定之說明類型的必要項目。  
  
 [in] `nCmd`  
 指定要求的說明類型。 如需可能的值清單以及它們如何影響 `dwData` 參數的相關資訊，請參閱 Windows SDK 中的 [WinHelp 函式](http://msdn.microsoft.com/library/windows/desktop/bb762267) 。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫[CWnd::WinHelp](../../mfc/reference/cwnd-class.md#winhelp)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)

