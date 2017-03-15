---
title: "COleIPFrameWndEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWndEx
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWndEx class
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
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
ms.openlocfilehash: 5eec8e3a9cc4ad71a1ee3de9f6d5f25cffef1242
ms.lasthandoff: 02/24/2017

---
# <a name="coleipframewndex-class"></a>COleIPFrameWndEx 類別
`COleIPFrameWndEx` 類別會實作支援 MFC 的 OLE 容器。 您必須為您的應用程式衍生就地框架視窗類別`COleIPFrameWndEx`類別，而不是從[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleIPFrameWndEx::AddDockSite](#adddocksite)||  
|[COleIPFrameWndEx::AddPane](#addpane)||  
|[COleIPFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)||  
|[COleIPFrameWndEx::DockPane](#dockpane)||  
|[COleIPFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐在另一個窗格的左邊。|  
|[COleIPFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)||  
|[COleIPFrameWndEx::EnableDocking](#enabledocking)||  
|[COleIPFrameWndEx::EnablePaneMenu](#enablepanemenu)||  
|[COleIPFrameWndEx::GetActivePopup](#getactivepopup)|將指標傳回到目前顯示的快顯功能表。|  
|[COleIPFrameWndEx::GetContainerFrameWindow](#getcontainerframewindow)||  
|[COleIPFrameWndEx::GetDefaultResId](#getdefaultresid)|在載入視窗時傳回您指定的框架視窗資源識別碼。|  
|[COleIPFrameWndEx::GetDockFrame](#getdockframe)||  
|[COleIPFrameWndEx::GetDockingManager](#getdockingmanager)||  
|[COleIPFrameWndEx::GetMainFrame](#getmainframe)||  
|[COleIPFrameWndEx::GetMenuBar](#getmenubar)|將指標傳回到附加在框架視窗的功能表列物件。|  
|[COleIPFrameWndEx::GetPane](#getpane)||  
|[COleIPFrameWndEx::GetTearOffBars](#gettearoffbars)|傳回分割狀態的窗格物件清單。|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|架構先呼叫，再顯示工具提示按鈕。|  
|[COleIPFrameWndEx::InsertPane](#insertpane)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|決定功能表列物件的指標是否不是 `NULL`。|  
|[COleIPFrameWndEx::IsPointNearDockSite](#ispointneardocksite)||  
|[COleIPFrameWndEx::LoadFrame](#loadframe)|(覆寫 `COleIPFrameWnd::LoadFrame`。)|  
|[COleIPFrameWndEx::OnCloseDockingPane](#onclosedockingpane)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)||  
|[COleIPFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|架構在作用中的快顯功能表處理 WM_DESTROY 訊息時所呼叫。|  
|[COleIPFrameWndEx::OnCmdMsg](#oncmdmsg)|(覆寫 `CFrameWnd::OnCmdMsg`。)|  
|[COleIPFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|架構在繪製與功能表項目相關聯的映像時所呼叫。|  
|[COleIPFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|由架構呼叫時[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)物件處理 WM_PAINT 訊息。|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|由架構呼叫時[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件會處理 WM_NCHITTEST 訊息。|  
|[COleIPFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)||  
|[COleIPFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。 (覆寫[CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode)。)|  
|[COleIPFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)||  
|[COleIPFrameWndEx::OnShowPanes](#onshowpanes)||  
|[COleIPFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|架構在啟動快顯功能表時所呼叫。|  
|[COleIPFrameWndEx::OnTearOffMenu](#ontearoffmenu)|架構在啟動有分割列的功能表時所呼叫。|  
|[COleIPFrameWndEx::PaneFromPoint](#panefrompoint)||  
|[COleIPFrameWndEx::PreTranslateMessage](#pretranslatemessage)|(覆寫 `COleIPFrameWnd::PreTranslateMessage`。)|  
|[COleIPFrameWndEx::RecalcLayout](#recalclayout)|(覆寫 `COleIPFrameWnd::RecalcLayout`。)|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)||  
|[COleIPFrameWndEx::SetDockState](#setdockstate)|將指定的停駐狀態套用到屬於框架視窗的窗格。|  
|[COleIPFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|藉由搜尋虛設項目並替換成指定的使用者定義項目，修改工具列物件。|  
|[COleIPFrameWndEx::ShowPane](#showpane)||  
|[COleIPFrameWndEx::WinHelpA](#winhelpa)|架構所呼叫以起始 WinHelp 應用程式或內容說明。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleIPFrameWndEx::InitUserToobars](#initusertoobars)|告知架構初始化指派給使用者定義工具列的控制項識別碼範圍。|  
  
## <a name="example"></a>範例  
 下例示範如何建立 `COleIPFrameWndEx` 類別的執行個體子類別並覆寫其方法。 此範例示範如何覆寫 `OnDestory` 方法、 `RepositionFrame` 方法、 `RecalcLayout` 方法和 `CalcWindowRect` 方法。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&1;](../../mfc/reference/codesnippet/cpp/coleipframewndex-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxoleipframewndex.h  
  
##  <a name="a-nameadddocksitea--coleipframewndexadddocksite"></a><a name="adddocksite"></a>COleIPFrameWndEx::AddDockSite  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AddDockSite();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddpanea--coleipframewndexaddpane"></a><a name="addpane"></a>COleIPFrameWndEx::AddPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 [in] `bTail`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameadjustdockinglayouta--coleipframewndexadjustdockinglayout"></a><a name="adjustdockinglayout"></a>COleIPFrameWndEx::AdjustDockingLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `hdwp`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedockpanea--coleipframewndexdockpane"></a><a name="dockpane"></a>COleIPFrameWndEx::DockPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 [in] `nDockBarID`  
 [in] `lpRect`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedockpaneleftofa--coleipframewndexdockpaneleftof"></a><a name="dockpaneleftof"></a>COleIPFrameWndEx::DockPaneLeftOf  
 將窗格停駐在另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要停駐窗格的指標。  
  
 [in] `pLeftOf`  
 此窗格，可做為原始指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`作業是否成功。 否則傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以停駐在預先定義的順序中的數個窗格物件。 這個方法所指定的窗格停駐於`pBar`左邊窗格中所指定的`pLeftOf`。  
  
##  <a name="a-nameenableautohidepanesa--coleipframewndexenableautohidepanes"></a><a name="enableautohidepanes"></a>COleIPFrameWndEx::EnableAutoHidePanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenabledockinga--coleipframewndexenabledocking"></a><a name="enabledocking"></a>COleIPFrameWndEx::EnableDocking  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenablepanemenua--coleipframewndexenablepanemenu"></a><a name="enablepanemenu"></a>COleIPFrameWndEx::EnablePaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly = FALSE,  
    BOOL bViewMenuShowsToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 [in] `uiCustomizeCmd`  
 [in] `strCustomizeLabel`  
 [in] `uiViewToolbarsMenuEntryID`  
 [in] `bContextMenuShowsToolbarsOnly`  
 [in] `bViewMenuShowsToolbarsOnly`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetactivepopupa--coleipframewndexgetactivepopup"></a><a name="getactivepopup"></a>COleIPFrameWndEx::GetActivePopup  
 傳回目前所顯示的快顯功能表上的指標。  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 變數的指標，作用中的快顯功能表。否則`NULL`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來取得的指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)目前顯示的物件。  
  
##  <a name="a-namegetcontainerframewindowa--coleipframewndexgetcontainerframewindow"></a><a name="getcontainerframewindow"></a>COleIPFrameWndEx::GetContainerFrameWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
COleCntrFrameWndEx* GetContainerFrameWindow();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetdefaultresida--coleipframewndexgetdefaultresid"></a><a name="getdefaultresid"></a>COleIPFrameWndEx::GetDefaultResId  
 傳回功能表資源識別碼所指定的框架視窗中載入功能表時。  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果框架視窗會不有任何功能表列會傳回 功能表上，則為 0 的資源識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取的資源 ID 所指定的框架視窗時載入的功能表資源藉由呼叫`COleIPFrameWndEx::LoadFrame`。  
  
##  <a name="a-namegetdockframea--coleipframewndexgetdockframe"></a><a name="getdockframe"></a>COleIPFrameWndEx::GetDockFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CFrameWnd* GetDockFrame();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetdockingmanagera--coleipframewndexgetdockingmanager"></a><a name="getdockingmanager"></a>COleIPFrameWndEx::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetmainframea--coleipframewndexgetmainframe"></a><a name="getmainframe"></a>COleIPFrameWndEx::GetMainFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CFrameWnd* GetMainFrame();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetmenubara--coleipframewndexgetmenubar"></a><a name="getmenubar"></a>COleIPFrameWndEx::GetMenuBar  
 將指標傳回到附加在框架視窗的功能表列物件。  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能表列物件指標。  
  
### <a name="remarks"></a>備註  
 使用此函數來擷取屬於功能表列物件的指標`COleIPFrameWndEx`物件。  
  
##  <a name="a-namegetpanea--coleipframewndexgetpane"></a><a name="getpane"></a>COleIPFrameWndEx::GetPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettearoffbarsa--coleipframewndexgettearoffbars"></a><a name="gettearoffbars"></a>COleIPFrameWndEx::GetTearOffBars  
 傳回分割狀態的窗格物件清單。  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考`CObList`物件，其中包含的指標集合[CBasePane 類別](../../mfc/reference/cbasepane-class.md)-衍生物件。  
  
### <a name="remarks"></a>備註  
 `COleIPFrameWndEx`物件會維護一份 tear-off 功能表集合[CBasePane 類別](../../mfc/reference/cbasepane-class.md)-衍生物件。 使用這個方法來擷取這份清單的參考。  
  
##  <a name="a-namegettoolbarbuttontooltiptexta--coleipframewndexgettoolbarbuttontooltiptext"></a><a name="gettoolbarbuttontooltiptext"></a>COleIPFrameWndEx::GetToolbarButtonToolTipText  
 架構先呼叫，再顯示工具提示按鈕。  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 按鈕的指標。  
  
 [in] `strTTText`  
 指標的工具提示文字。  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回 0。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可自訂的工具列按鈕上的工具提示顯示。  
  
##  <a name="a-nameinitusertoobarsa--coleipframewndexinitusertoobars"></a><a name="initusertoobars"></a>COleIPFrameWndEx::InitUserToobars  
 指定控制項 Id 範圍的架構會指派給使用者定義的工具列。  
  
```  
void InitUserToolbars(
    LPCTSTR lpszRegEntry,   
    UINT uiUserToolbarFirst,   
    UINT uiUserToolbarLast)  
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszRegEntry`  
 程式庫儲存使用者工具列設定登錄項目。  
  
 [in] `uiUserToolbarFirst`  
 指派給第一個使用者自訂工具列控制項的 ID。  
  
 [in] `uiUserToolbarLast`  
 指派給最後一個使用者自訂工具列控制項的 ID。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來初始化控制項 Id 範圍的指派給使用者以動態方式定義的工具列。 參數`uiUserToolbarFirst`和`uiUserToolbarLast`定義允許的工具列控制項 Id 的範圍。 若要停用建立使用者定義的工具列，將`uiUserToolbarFirst`或`uiUserToolbarLast`為-1。  
  
##  <a name="a-nameinsertpanea--coleipframewndexinsertpane"></a><a name="insertpane"></a>COleIPFrameWndEx::InsertPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 [in] `pTarget`  
 [in] `bAfter`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameismenubaravailablea--coleipframewndexismenubaravailable"></a><a name="ismenubaravailable"></a>COleIPFrameWndEx::IsMenuBarAvailable  
 決定是否不是功能表列物件的指標`NULL`  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果框架視窗的功能表列。否則傳回 0。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷是否要維護的框架視窗的非`NULL`其功能表列物件的指標。  
  
##  <a name="a-nameispointneardocksitea--coleipframewndexispointneardocksite"></a><a name="ispointneardocksite"></a>COleIPFrameWndEx::IsPointNearDockSite  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 [in] `dwBarAlignment`  
 [in] `bOuterEdge`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadframea--coleipframewndexloadframe"></a><a name="loadframe"></a>COleIPFrameWndEx::LoadFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIDResource`  
 [in] `dwDefaultStyle`  
 [in] `pParentWnd`  
 [in] `pContext`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonclosedockingpanea--coleipframewndexonclosedockingpane"></a><a name="onclosedockingpane"></a>COleIPFrameWndEx::OnCloseDockingPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane*);
```  
  
### <a name="parameters"></a>參數  
 [in] `CDockablePane*`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncloseminiframea--coleipframewndexoncloseminiframe"></a><a name="oncloseminiframe"></a>COleIPFrameWndEx::OnCloseMiniFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd*);
```  
  
### <a name="parameters"></a>參數  
 [in] `CPaneFrameWnd*`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonclosepopupmenua--coleipframewndexonclosepopupmenu"></a><a name="onclosepopupmenu"></a>COleIPFrameWndEx::OnClosePopupMenu  
 使用中的快顯功能表上處理時，由框架呼叫`WM_DESTROY`訊息。  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPopup`  
 快顯功能表物件的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以接收通知從`CMFCPopupMenu`物件時，它們會處理`WM_DESTROY`訊息。  
  
##  <a name="a-nameoncmdmsga--coleipframewndexoncmdmsg"></a><a name="oncmdmsg"></a>COleIPFrameWndEx::OnCmdMsg  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 [in] `nCode`  
 [in] `pExtra`  
 [in] `pHandlerInfo`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawmenuimagea--coleipframewndexondrawmenuimage"></a><a name="ondrawmenuimage"></a>COleIPFrameWndEx::OnDrawMenuImage  
 繪製功能表項目相關聯的映像時，由架構呼叫。  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標。  
  
 [in] `pMenuButton`  
 指標 [功能表] 按鈕。  
  
 [in] `rectImage`  
 功能表項目與關聯的影像。  
  
### <a name="return-value"></a>傳回值  
 預設實作不做任何動作，並傳回 0。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，如果您想要自訂映像繪製功能表項目所擁有的功能表列屬於`COleIPFrameWndEx`-衍生物件。  
  
##  <a name="a-nameondrawmenulogoa--coleipframewndexondrawmenulogo"></a><a name="ondrawmenulogo"></a>COleIPFrameWndEx::OnDrawMenuLogo  
 由架構呼叫時[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)物件處理程序`WM_PAINT`訊息。  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標。  
  
 [in] `pMenu`  
 快顯功能表上的物件指標。  
  
 [in] `rectLogo`  
 要顯示的標誌的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以顯示功能表列所擁有相關聯的快顯功能表上的標誌`COleIPFrameWndEx`-衍生物件。 預設實作不做任何動作。  
  
##  <a name="a-nameonmenubuttontoolhittesta--coleipframewndexonmenubuttontoolhittest"></a><a name="onmenubuttontoolhittest"></a>COleIPFrameWndEx::OnMenuButtonToolHitTest  
 由架構呼叫時[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件處理程序`WM_NCHITTEST`訊息。  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>參數  
 [] in pButton  
 功能表按鈕的指標。  
  
 [] out pTI  
 `TOOLINFO` 結構的指標。  
  
### <a name="return-value"></a>傳回值  
 預設實作不做任何動作，並傳回 0。 您的實作應該傳回非零值，如果它填滿`pTI`參數。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法以提供特定的功能表項目相關的工具提示資訊。  
  
##  <a name="a-nameonmoveminiframea--coleipframewndexonmoveminiframe"></a><a name="onmoveminiframe"></a>COleIPFrameWndEx::OnMoveMiniFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsetpreviewmodea--coleipframewndexonsetpreviewmode"></a><a name="onsetpreviewmode"></a>COleIPFrameWndEx::OnSetPreviewMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPreview`  
 [in] `pState`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonshowcustomizepanea--coleipframewndexonshowcustomizepane"></a><a name="onshowcustomizepane"></a>COleIPFrameWndEx::OnShowCustomizePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPane`  
 [in] `uiToolbarID`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonshowpanesa--coleipframewndexonshowpanes"></a><a name="onshowpanes"></a>COleIPFrameWndEx::OnShowPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonshowpopupmenua--coleipframewndexonshowpopupmenu"></a><a name="onshowpopupmenu"></a>COleIPFrameWndEx::OnShowPopupMenu  
 顯示快顯功能表時，由架構呼叫。  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>參數  
 `[in] pMenuPopup`  
 顯示快顯功能表上的指標。  
  
### <a name="return-value"></a>傳回值  
 預設實作不做任何動作，並傳回非零值。 您的實作應該會傳回`FALSE`如果無法顯示快顯功能表。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以自訂的快顯功能表上顯示。 比方說，您無法變更色彩功能表按鈕的功能表按鈕或初始化撕列。  
  
##  <a name="a-nameontearoffmenua--coleipframewndexontearoffmenu"></a><a name="ontearoffmenu"></a>COleIPFrameWndEx::OnTearOffMenu  
 當使用者選取有撕列 功能表上，由架構呼叫。  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuPopup`  
 使用者選取的快顯功能表指標。  
  
 [in] `pBar`  
 裝載功能表 窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果您想要啟用快顯功能表中，架構否則`FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂撕列的安裝程式會覆寫這個函式。  
  
##  <a name="a-namepanefrompointa--coleipframewndexpanefrompoint"></a><a name="panefrompoint"></a>COleIPFrameWndEx::PaneFromPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
 [in] `nSensitivity`  
 [in] `bExactBar`  
 [in] `pRTCBarType`  
 [in] `dwAlignment`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namepretranslatemessagea--coleipframewndexpretranslatemessage"></a><a name="pretranslatemessage"></a>COleIPFrameWndEx::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMsg`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerecalclayouta--coleipframewndexrecalclayout"></a><a name="recalclayout"></a>COleIPFrameWndEx::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNotify`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremovepanefromdockmanagera--coleipframewndexremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>COleIPFrameWndEx::RemovePaneFromDockManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
 [in] `bDestroy`  
 [in] `bAdjustLayout`  
 [in] `bAutoHide`  
 [in] `pBarReplacement`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdockstatea--coleipframewndexsetdockstate"></a><a name="setdockstate"></a>COleIPFrameWndEx::SetDockState  
 適用於指定的銜接狀態隸屬於框架視窗的窗格。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>參數  
 [in] `state`  
 指定的銜接狀態。  
  
### <a name="remarks"></a>備註  
 使用此函數來指定新的停駐狀態窗格隸屬於`COleIPFrameWndEx`物件。  
  
##  <a name="a-namesetuptoolbarmenua--coleipframewndexsetuptoolbarmenu"></a><a name="setuptoolbarmenu"></a>COleIPFrameWndEx::SetupToolbarMenu  
 藉由搜尋虛設項目並替換成指定的使用者定義項目，修改工具列物件。  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>參數  
 [in] `menu`  
 參考[CMenu](../../mfc/reference/cmenu-class.md)要修改的物件。  
  
 [in] `uiViewUserToolbarCmdFirst`  
 指定的使用者定義的第一個命令。  
  
 [in] `uiViewUserToolbarCmdLast`  
 指定的使用者定義的最後一個命令。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameshowpanea--coleipframewndexshowpane"></a><a name="showpane"></a>COleIPFrameWndEx::ShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 [in] `bShow`  
 [in] `bDelay`  
 [in] `bActivate`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namewinhelpaa--coleipframewndexwinhelpa"></a><a name="winhelpa"></a>COleIPFrameWndEx::WinHelpA  
 架構所呼叫以起始 WinHelp 應用程式或內容說明。  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>參數  
 [in] dwData  
 指定資料為 `nCmd`所指定之說明類型的必要項目。  
  
 [in] `nCmd`  
 指定要求的說明類型。 如需可能的值清單以及它們如何影響 `dwData` 參數的相關資訊，請參閱 Windows SDK 中的 [WinHelp 函式](http://msdn.microsoft.com/library/windows/desktop/bb762267) 。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [Cframewndex 則是類別](../../mfc/reference/cframewndex-class.md)   
 [Cmdiframewndex 是類別](../../mfc/reference/cmdiframewndex-class.md)

