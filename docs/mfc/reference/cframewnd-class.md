---
title: "CFrameWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
dev_langs:
- C++
helpviewer_keywords:
- frame window classes, base class
- single document interface (SDI), frame windows
- frame windows, creating
- CFrameWnd class
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 06becdd593028e02d45ed68fb8fa5687e1e2dbd1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="cframewnd-class"></a>CFrameWnd 類別
提供 Windows 單一文件介面 (SDI) 重疊或快顯框架視窗的功能，以及管理視窗的成員。  
  
## <a name="syntax"></a>語法  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|建構 `CFrameWnd` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|對使用者的畫面格查看及使用。|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|將框架視窗設定為強制回應。|  
|[CFrameWnd::Create](#create)|建立和初始化相關聯的 Windows 框架視窗呼叫`CFrameWnd`物件。|  
|[CFrameWnd::CreateView](#createview)|建立不衍生自內檢視`CView`。|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|停駐控制列。|  
|[CFrameWnd::EnableDocking](#enabledocking)|可讓要停駐控制列。|  
|[CFrameWnd::EndModalState](#endmodalstate)|結束框架視窗的強制回應狀態。 可讓所有停用 windows `BeginModalState`。|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|浮動控制列。|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|傳回使用中**CDocument**物件。|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|傳回使用中`CFrameWnd`物件。|  
|[CFrameWnd::GetActiveView](#getactiveview)|傳回使用中`CView`物件。|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|擷取控制列。|  
|[CFrameWnd::GetDockState](#getdockstate)|擷取框架視窗停駐的狀態。|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|擷取目前的 MFC 應用程式中的功能表顯示狀態。|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|指出是否要隱藏或顯示為目前的 MFC 應用程式中的功能表的預設行為。|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|讓指標回到狀態列屬於框架視窗。|  
|[CFrameWnd::GetMessageString](#getmessagestring)|擷取訊息對應至一個命令 id。|  
|[CFrameWnd::GetTitle](#gettitle)|擷取相關的控制列的標題。|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|會導致`OnInitialUpdate`屬於框架視窗呼叫中的所有檢視的成員函式。|  
|[CFrameWnd::InModalState](#inmodalstate)|傳回值，指出框架視窗處於強制回應狀態。|  
|[CFrameWnd::IsTracking](#istracking)|判斷目前正在移動分隔列是否。|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|呼叫以載入快速鍵對應表。|  
|[CFrameWnd::LoadBarState](#loadbarstate)|呼叫控制列設定。|  
|[CFrameWnd::LoadFrame](#loadframe)|呼叫以動態方式建立框架視窗從資源資訊。|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|會在框架視窗的框線空間的交涉。|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|指定的控制列上執行某個動作時呼叫。|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|處理就地項目的 SHIFT + F1 說明。|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|預覽列印模式進出設定應用程式的主框架視窗。|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|更新相關的功能表時由架構呼叫。|  
|[CFrameWnd::RecalcLayout](#recalclayout)|重新置放控制列的`CFrameWnd`物件。|  
|[CFrameWnd::SaveBarState](#savebarstate)|呼叫以儲存控制列設定。|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|指定指定的檢視，以 for Rich Preview 現用檢視表。|  
|[CFrameWnd::SetActiveView](#setactiveview)|設定作用中`CView`物件。|  
|[CFrameWnd::SetDockState](#setdockstate)|若要停駐在主視窗的框架視窗呼叫。|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|若要隱藏或顯示目前的 MFC 應用程式中設定功能表顯示的狀態。|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|在目前的 MFC 應用程式可以隱藏或顯示設定 功能表的預設行為。|  
|[CFrameWnd::SetMessageText](#setmessagetext)|設定標準狀態列的文字。|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|設定 Windows 7 進度列顯示在工作列上的目前位置。|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|設定 Windows 7 進度列顯示在工作列上的範圍。|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|設定型別和進度列指示器顯示在工作列按鈕上的狀態。|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|多載。 適用於覆疊工作列按鈕，以指出應用程式狀態或使用者的通知。|  
|[CFrameWnd::SetTitle](#settitle)|設定相關的控制列的標題。|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|呼叫以顯示控制項列。|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|顯示所有視窗的子`CFrameWnd`物件。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|建立用戶端視窗框架。|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|隱藏目前的 MFC 應用程式中的功能表之前呼叫。|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|目前的 MFC 應用程式中的功能表會顯示之前呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|控制項的自動啟用和停用功能表項目的功能。|  
|[CFrameWnd::rectDefault](#rectdefault)|將此變數傳遞靜態`CRect`做為參數建立時`CFrameWnd`物件可讓 Windows 在選擇視窗的初始大小和位置。|  
  
## <a name="remarks"></a>備註  
 若要建立有用的框架視窗以進行您的應用程式，衍生自`CFrameWnd`。 將成員變數加入至衍生的類別，以儲存您的應用程式特有的資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。  
  
 有三種方法來建構框架視窗︰  
  
-   直接建構使用[建立](#create)。  
  
-   直接建構使用[LoadFrame](#loadframe)。  
  
-   間接建構使用文件範本。  
  
 您可以呼叫之前**建立**或`LoadFrame`，您必須建構使用 c + + 堆積上的框架視窗物件**新**運算子。 然後再呼叫**建立**，您也可以註冊視窗類別[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函式，可設定的畫面格的圖示和類別樣式。  
  
 使用**建立**傳遞畫面格的建立參數為立即引數的成員函式。  
  
 `LoadFrame`需要較少的引數比**建立**，並改為從資源，包括畫面格的標題、 圖示、 快速鍵對應表，以及功能表中擷取大部分其預設值。 若要可供`LoadFrame`，所有這些資源必須具有相同的資源識別碼 (例如， **IDR_MAINFRAME**)。  
  
 當`CFrameWnd`物件包含檢視表和文件時，會間接建立而不是直接由程式設計人員，架構。 `CDocTemplate`物件協調框架的建立、 包含檢視中，建立和檢視，以適當的文件的連接。 參數的`CDocTemplate`建構函式指定`CRuntimeClass`三個類別的涉及 （文件、 框架和檢視）。 A`CRuntimeClass`物件可由架構來動態建立新的框架時使用者所指定 （例如，藉由使用新檔案 命令或多個文件介面 (MDI) 視窗中新的命令）。  
  
 框架視窗類別衍生自`CFrameWnd`必須以宣告`DECLARE_DYNCREATE`為了讓上述`RUNTIME_CLASS`正常運作的機制。  
  
 A`CFrameWnd`包含要執行一般的應用程式中的主視窗的下列功能，適用於 Windows 的預設實作︰  
  
-   A`CFrameWnd`框架視窗會追蹤的目前使用的檢視無關的使用中視窗或目前的輸入的焦點。 當框架重新啟動時，使用中的檢視通知藉由呼叫`CView::OnActivateView`。  
  
-   命令訊息和許多常見的畫面格通知訊息，包括由`OnSetFocus`， `OnHScroll`，和`OnVScroll`函式的`CWnd`，委派的`CFrameWnd`框架視窗至目前使用的檢視。  
  
-   目前使用的檢視 （或目前作用中 MDI 子框架視窗，在 MDI 框架的情況下） 可以判斷框架視窗的標題。 可以停用此功能關閉**FWS_ADDTOTITLE**框架視窗的樣式位元。  
  
-   A`CFrameWnd`框架視窗負責控制列、 檢視和框架視窗的用戶端區域內的其他子視窗的位置。 框架視窗也會執行更新的工具列和其他控制項列按鈕的閒置時間。 A`CFrameWnd`框架視窗也會有預設實作的命令來切換開啟和關閉的工具列和狀態列。  
  
-   A`CFrameWnd`框架視窗會管理主功能表列。 框架視窗顯示快顯功能表時，會使用**UPDATE_COMMAND_UI**機制，判斷哪些功能表項目應該啟用、 停用，或檢查。 當使用者選取功能表項目時，框架視窗會更新 [狀態] 列與代表該命令的訊息字串。  
  
-   A`CFrameWnd`框架視窗會有選擇性的快速鍵對應表，會自動將轉譯鍵盤快速鍵。  
  
-   A`CFrameWnd`框架視窗具有選擇性說明 ID 與設定`LoadFrame`所用的即時線上說明。 框架視窗會組織 semimodal 狀態，例如即時線上說明 (SHIFT + F1)] 和 [預覽列印模式主要 orchestrator。  
  
-   A`CFrameWnd`框架視窗會開啟檔案，從檔案管理員拖放在框架視窗。 框架視窗是否已註冊副檔名，且應用程式相關聯，回應動態資料交換 (DDE) 開啟的要求，或在使用者開啟資料檔在檔案管理員時，就會發生**ShellExecute**呼叫 Windows 函式。  
  
-   如果框架視窗是主應用程式視窗 (也就是`CWinThread::m_pMainWnd`)，當使用者關閉應用程式中，框架視窗會提示使用者儲存任何已修改的文件 (如`OnClose`和`OnQueryEndSession`)。  
  
-   如果主應用程式視窗框架視窗，框架視窗會是執行 WinHelp 的內容。 關閉框架視窗會關閉 WINHELP。如果它的啟動此應用程式的，EXE。  
  
 不使用 c + +**刪除**終結框架視窗的運算子。 請改用 `CWnd::DestroyWindow` 。 `CFrameWnd`實作`PostNcDestroy`當視窗終結時，將會刪除 c + + 物件。 當使用者關閉框架視窗時，預設值`OnClose`處理常式會呼叫`DestroyWindow`。  
  
 如需有關`CFrameWnd`，請參閱[框架視窗](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="activateframe"></a>CFrameWnd::ActivateFrame  
 呼叫以啟動並還原框架視窗，以便使用者會看到並使用此成員函式。  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>參數  
 `nCmdShow`  
 指定要傳遞給參數[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。 根據預設，框架會顯示，並正確地還原。  
  
### <a name="remarks"></a>備註  
 此成員函式通常在非使用者介面事件，例如 DDE、 OLE 或其他可能對使用者顯示框架視窗或其內容的事件後呼叫。  
  
 預設實作會啟用框架並將它帶到疊置順序的頂端和，如有必要，執行相同的步驟，應用程式的主框架視窗。  
  
 覆寫此成員函式，若要變更啟動畫面格的方式。 例如，您可以強制要最大化的 MDI 子視窗。 新增適當的功能，然後呼叫其明確的基底類別版本`nCmdShow`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>CFrameWnd::BeginModalState  
 呼叫此成員函式以製作框架視窗強制回應。  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>CFrameWnd::CFrameWnd  
 建構`CFrameWnd`物件，但並不會建立顯示框架視窗。  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>備註  
 呼叫**建立**建立可見的視窗。  
  
##  <a name="create"></a>CFrameWnd::Create  
 建立和初始化相關聯的 Windows 框架視窗呼叫`CFrameWnd`物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CWnd* pParentWnd = NULL,  
    LPCTSTR lpszMenuName = NULL,  
    DWORD dwExStyle = 0,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 指向以 null 結束的字元字串，Windows 類別命名。 類別名稱可以是任何名稱登錄與`AfxRegisterWndClass`全域函式或**RegisterClass** Windows 函式。 如果**NULL**，會使用預先定義的預設`CFrameWnd`屬性。  
  
 `lpszWindowName`  
 指向以 null 結束的字元字串，表示視窗名稱。 做為標題列的文字。  
  
 `dwStyle`  
 指定視窗[樣式](../../mfc/reference/window-styles.md)屬性。 包含**FWS_ADDTOTITLE**樣式，如果您想要自動顯示在視窗中表示的文件名稱的標題列。  
  
 `rect`  
 指定的大小和視窗的位置。 `rectDefault`值，可讓 Windows，指定新的視窗位置與大小。  
  
 `pParentWnd`  
 指定此框架視窗的父視窗。 這個參數應該是**NULL**的最上層框架視窗。  
  
 *lpszMenuName*  
 識別功能表資源，以用於視窗的名稱。 使用**MAKEINTRESOURCE**如果的功能表還包含整數識別碼，而非字串。 這個參數可以是**NULL**。  
  
 `dwExStyle`  
 指定延伸的視窗[樣式](../../mfc/reference/extended-window-styles.md)屬性。  
  
 `pContext`  
 指定指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 建構`CFrameWnd`兩個步驟中的物件。 首先，叫用的建構函式，建構`CFrameWnd`物件，然後再呼叫**建立**，建立的 Windows 框架視窗，並將它附加至`CFrameWnd`物件。 **建立**初始化視窗的類別名稱和視窗名稱，並註冊其樣式、 父系及相關的功能表的預設值。  
  
 使用`LoadFrame`而**建立**載入框架視窗中的資源，而不是指定其引數。  
  
##  <a name="createview"></a>CFrameWnd::CreateView  
 呼叫`CreateView`建立檢視，在範圍內。  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 指定檢視和文件的類型。  
  
 `nID`  
 檢視的識別碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CWnd`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 使用不是此成員函式來建立 「 檢視 」 `CView`-衍生的範圍內。 在呼叫`CreateView`，您必須手動設定為 作用中的檢視，並將它設為可見，則這些工作不會自動執行的`CreateView`。  
  
##  <a name="dockcontrolbar"></a>CFrameWnd::DockControlBar  
 會導致要停駐在框架視窗的控制列。  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pBar`  
 指向要停駐控制列。  
  
 `nDockBarID`  
 決定哪些邊時應考量的停駐在框架視窗。 它可以是 0，或其中一個或多個項目︰  
  
- `AFX_IDW_DOCKBAR_TOP`停駐在框架視窗的頂端。  
  
- **AFX_IDW_DOCKBAR_BOTTOM**固定至框架視窗的底部。  
  
- `AFX_IDW_DOCKBAR_LEFT`停駐在框架視窗的左半部。  
  
- `AFX_IDW_DOCKBAR_RIGHT`停駐於框架視窗的右側。  
  
 如果為 0，則可以停駐控制列啟用停駐目的地框架視窗中的任一側。  
  
 `lpRect`  
 判斷在螢幕座標，其中將目的地框架視窗中非工作區停駐控制列。  
  
### <a name="remarks"></a>備註  
 同時呼叫中指定的框架視窗的側邊的其中一個會停駐控制列[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd::EnableDocking](#enabledocking)。 選擇的一端由`nDockBarID`。  
  
##  <a name="enabledocking"></a>CFrameWnd::EnableDocking  
 呼叫此函式可啟用在框架視窗中的可停駐控制列。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwDockStyle`  
 指定的框架視窗哪一邊可以做為停駐控制列的網站。 它可以是下列一或多個項目︰  
  
- `CBRS_ALIGN_TOP`可讓用戶端區域頂端停駐。  
  
- `CBRS_ALIGN_BOTTOM`可讓用戶端區域底部停駐。  
  
- `CBRS_ALIGN_LEFT`可讓用戶端區域左側停駐。  
  
- `CBRS_ALIGN_RIGHT`可讓用戶端區域右邊的停駐。  
  
- `CBRS_ALIGN_ANY`可讓用戶端區域的任何側邊停駐。  
  
### <a name="remarks"></a>備註  
 根據預設，控制列將會停駐於框架視窗，以下列順序的一邊︰ 頂端、 底端、 左、 右。  
  
### <a name="example"></a>範例  
  請參閱範例的[CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create)。  
  
##  <a name="endmodalstate"></a>CFrameWnd::EndModalState  
 呼叫此成員函式，將框架視窗從強制回應變更為非強制回應。  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>備註  
 `EndModalState`可讓所有停用 windows [BeginModalState](#beginmodalstate)。  
  
##  <a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar  
 呼叫此函式會造成不停駐在框架視窗的控制列。  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>參數  
 `pBar`  
 指向要浮動控制列。  
  
 `point`  
 位置，在螢幕座標中放置控制列的左上的角。  
  
 `dwStyle`  
 指定是否要在其新的框架視窗水平或垂直對齊控制列。 它可以是下列其中一項動作︰  
  
- `CBRS_ALIGN_TOP`將垂直導向控制列。  
  
- `CBRS_ALIGN_BOTTOM`將垂直導向控制列。  
  
- `CBRS_ALIGN_LEFT`水平 會將控制列。  
  
- `CBRS_ALIGN_RIGHT`水平 會將控制列。  
  
 如果樣式傳遞指定水平和垂直方向，工具列會導向水平。  
  
### <a name="remarks"></a>備註  
 一般而言，這是在應用程式啟動程式從上一個執行還原的設定時。  
  
 當使用者透過放開滑鼠左鍵同時透過不適用於停駐位置拖曳控制列導致卸除作業時，此函式是由架構呼叫。  
  
##  <a name="getactivedocument"></a>CFrameWnd::GetActiveDocument  
 呼叫此成員函式，以取得要與目前的指標**CDocument**附加至目前的現用檢視。  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>傳回值  
 目前的指標[CDocument](../../mfc/reference/cdocument-class.md)。 如果沒有目前的文件，會傳回**NULL**。  
  
##  <a name="getactiveframe"></a>CFrameWnd::GetActiveFrame  
 呼叫此成員函式可取得指向作用中的多個文件介面 (MDI) 子視窗的 MDI 框架視窗。  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>傳回值  
 作用中的 MDI 子視窗指標。 如果應用程式是 SDI 應用程式，或 MDI 框架視窗有任何作用中的文件，隱含**這**將傳回的指標。  
  
### <a name="remarks"></a>備註  
 如果沒有使用中的 MDI 子系或應用程式是單一文件介面 (SDI)，隱含**這**會傳回指標。  
  
##  <a name="getactiveview"></a>CFrameWnd::GetActiveView  
 呼叫此成員函式，以取得使用中的檢視 （如果有的話） 附加至框架視窗的指標 ( `CFrameWnd`)。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的指標[CView](../../mfc/reference/cview-class.md)。 如果沒有目前的檢視，會傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 此函數會傳回**NULL** MDI 主框架視窗呼叫時 ( `CMDIFrameWnd`)。 在 MDI 應用程式，MDI 主框架視窗沒有與其相關聯的檢視。 相反地，每個個別的子視窗 ( `CMDIChildWnd`) 有一或多個相關聯的檢視。 可取得 MDI 應用程式中使用中的檢視，可以先尋找作用中的 MDI 子視窗再尋找該子視窗的 使用中的檢視。 可以找到現用 MDI 子視窗呼叫函式`MDIGetActive`或**GetActiveFrame**如下列所示︰  
  
 [!code-cpp[NVC_MFCWindowing # 2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>CFrameWnd::GetControlBar  
 呼叫`GetControlBar`來取得存取權與識別碼相關聯的控制列  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制列識別碼。  
  
### <a name="return-value"></a>傳回值  
 控制列識別碼相關聯的指標  
  
### <a name="remarks"></a>備註  
 `nID`參數是指傳遞給唯一識別碼**建立**控制列的方法。 針對多個控制列的詳細資訊，請參閱標題為主題[控制列](../../mfc/control-bars.md)。  
  
 `GetControlBar`將傳回控制列，即使它浮動窗格，而且不是目前子視窗的框架。  
  
##  <a name="getdockstate"></a>CFrameWnd::GetDockState  
 呼叫此成員函式，來儲存狀態資訊在框架視窗的控制列`CDockState`物件。  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>參數  
 `state`  
 包含傳回時的框架視窗的控制列的目前狀態。  
  
### <a name="remarks"></a>備註  
 然後，您可以撰寫的內容`CDockState`儲存體使用`CDockState::SaveState`或`Serialize`。 如果您稍後想要還原至先前狀態的控制列，負載平衡的狀態與`CDockState::LoadState`或`Serialize`，然後呼叫`SetDockState`框架視窗的控制列來套用先前的狀態。  
  
##  <a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState  
 擷取目前的 MFC 應用程式中的功能表顯示狀態。  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值可以是下列值︰  
  
-   AFX_MBS_VISIBLE (0x01)-功能表會顯示。  
  
-   AFX_MBS_HIDDEN (0x02)-隱藏功能表。  
  
### <a name="remarks"></a>備註  
 如果發生執行階段錯誤，此方法偵錯模式中的判斷提示，而且會引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。  
  
##  <a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility  
 指出是否在目前的 MFC 應用程式功能表的預設狀態為隱藏或顯示。  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>傳回值  
 這個方法會傳回下列值之一︰  
  
-   AFX_MBV_KEEPVISIBLE (0x01)-顯示功能表時會完全次，並依預設並沒有焦點。  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02)-預設為隱藏功能表。 如果隱藏功能表上，按下 ALT 鍵以顯示功能表，並將焦點提供。 如果顯示的功能表上，按 alt 鍵或 ESC 鍵隱藏它。  
  
-   AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0x04) （合 (OR)）-預設為隱藏功能表。 如果隱藏功能表上，按 F10 鍵，顯示功能表，並將焦點提供。 如果顯示的功能表上，按 F10 鍵來切換開啟或關閉功能表的焦點。 直到您按 alt 鍵或 ESC 鍵，以便隱藏，則會顯示功能表。  
  
### <a name="remarks"></a>備註  
 如果發生執行階段錯誤，此方法偵錯模式中的判斷提示，而且會引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。  
  
##  <a name="getmessagebar"></a>CFrameWnd::GetMessageBar  
 呼叫此成員函式可取得 [狀態] 列的指標。  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>傳回值  
 狀態列 視窗的指標。  
  
##  <a name="getmessagestring"></a>CFrameWnd::GetMessageString  
 覆寫此函式可提供自訂字串的命令 Id。  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 資源所需的訊息識別碼。  
  
 `rMessage`  
 `CString`要放置訊息物件。  
  
### <a name="remarks"></a>備註  
 預設實作只會載入所指定的字串`nID`從資源檔。 在狀態列中的訊息字串需要更新時，此函式是由架構呼叫。  
  
##  <a name="gettitle"></a>CFrameWnd::GetTitle  
 擷取視窗物件的標題。  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含目前視窗物件的標題。  
  
##  <a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame  
 呼叫**IntitialUpdateFrame**之後建立新的框架與**建立**。  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>參數  
 `pDoc`  
 指向文件框架視窗是相關聯。 可以是**NULL**。  
  
 `bMakeVisible`  
 如果**TRUE**，表示框架都應該變成可見且作用中。 如果**FALSE**，沒有下階都已成為可見。  
  
### <a name="remarks"></a>備註  
 這可讓所有的檢視以接收該框架視窗中其`OnInitialUpdate`呼叫。  
  
 此外，如果有不是先前作用中的檢視，框架視窗的主要檢視變成使用中。 主要的檢視是檢視的子識別碼**AFX_IDW_PANE_FIRST**。 最後，框架視窗也會看到如果`bMakeVisible`為非零值。 如果`bMakeVisible`是 0，則目前的焦點和框架視窗的可見狀態會保持不變。 您不需要使用新檔案並開啟舊檔架構的實作時，呼叫此函式。  
  
##  <a name="inmodalstate"></a>CFrameWnd::InModalState  
 呼叫此成員函式，來檢查框架視窗是否為獨佔式或非強制回應。  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是，則為非零否則便是 0。  
  
##  <a name="istracking"></a>CFrameWnd::IsTracking  
 呼叫以判斷目前正在移動視窗中的分隔列是否此成員函式。  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果分隔器作業正在進行中，則為非零否則便是 0。  
  
##  <a name="loadacceltable"></a>CFrameWnd::LoadAccelTable  
 呼叫以載入指定的快速鍵對應表。  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 識別快速鍵資源的名稱。 使用**MAKEINTRESOURCE**如果資源識別出具有整數識別碼。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功載入快速鍵對應表。否則便是 0。  
  
### <a name="remarks"></a>備註  
 只有一個資料表可以載入一次。  
  
 應用程式終止時，會自動釋放從資源載入的快速鍵對應表。  
  
 如果您呼叫`LoadFrame`若要建立框架視窗，架構會載入快速鍵對應表的功能表和圖示資源，以及和就不需要此成員函式的後續呼叫。  
  
##  <a name="loadbarstate"></a>CFrameWnd::LoadBarState  
 呼叫此函式可還原的每個框架視窗所擁有的控制列的設定。  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>參數  
 `lpszProfileName`  
 初始設定 (INI) 檔案中的區段或儲存狀態資訊的 Windows 登錄中的索引鍵的名稱。  
  
### <a name="remarks"></a>備註  
 還原的資訊包括可見性、 水平或垂直方向、 停駐狀態和控制列位置。  
  
 您想要還原的設定必須寫入至登錄，才能呼叫`LoadBarState`。 將資訊寫入登錄，藉由呼叫[CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)。 將資訊寫入 INI 檔案，藉由呼叫[SaveBarState](#savebarstate)。  
  
##  <a name="loadframe"></a>CFrameWnd::LoadFrame  
 呼叫以動態方式建立框架視窗從資源資訊。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nIDResource`  
 框架視窗相關聯的共用資源的識別碼。  
  
 *dwDefaultStyle*  
 畫面格的[樣式](../../mfc/reference/window-styles.md)。 包含**FWS_ADDTOTITLE**樣式，如果您想要自動顯示在視窗中表示的文件名稱的標題列。  
  
 `pParentWnd`  
 畫面格的父指標。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是**NULL**。  
  
### <a name="remarks"></a>備註  
 建構`CFrameWnd`兩個步驟中的物件。 首先，叫用的建構函式，建構`CFrameWnd`物件，然後再呼叫`LoadFrame`，其中會載入 Windows 框架視窗和相關聯的資源，並附加框架視窗至`CFrameWnd`物件。 `nIDResource`參數指定 [] 功能表、 快速鍵對應表、 圖示和框架視窗標題的字串資源。  
  
 使用**建立**成員函式而非`LoadFrame`當您想要指定所有框架視窗的建立參數。  
  
 這個架構會呼叫`LoadFrame`它會建立使用文件範本物件，在框架視窗。  
  
 架構會使用`pContext`引數來指定要連接至框架視窗，包括任何物件所包含的檢視物件。 您可以設定`pContext`引數**NULL**當您呼叫`LoadFrame`。  
  
##  <a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable  
 （這是預設值） 啟用此資料成員時，功能表項目，並沒有`ON_UPDATE_COMMAND_UI`或`ON_COMMAND`處理常式會自動停用使用者提取下功能表。  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>備註  
 具有功能表項目`ON_COMMAND`處理常式但不是`ON_UPDATE_COMMAND_UI`處理常式將會自動啟用。  
  
 設定此資料成員時，功能表項目會自動啟用啟用的工具列按鈕的方式相同。  
  
> [!NOTE]
> `m_bAutoMenuEnable`不沒有最上層功能表項目上的任何作用。  
  
 此資料成員簡化依據目前的選取範圍的選擇性命令的實作，並減少需要撰寫`ON_UPDATE_COMMAND_UI`啟用和停用功能表項目處理常式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace  
 呼叫此成員函式在 OLE 就地啟用期間交涉框線空間框架視窗中。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>參數  
 *nBorderCmd*  
 中的以下值的其中一個**列舉 BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 指標[RECT](../../mfc/reference/rect-structure1.md)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定框線的座標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是**CFrameWnd** OLE 框線空間交涉的實作。  
  
##  <a name="onbarcheck"></a>CFrameWnd::OnBarCheck  
 指定的控制列上執行某個動作時呼叫。  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制列所顯示的識別碼。  
  
### <a name="return-value"></a>傳回值  
 控制列才會存在; 如果為非零否則便是 0。  
  
##  <a name="oncontexthelp"></a>CFrameWnd::OnContextHelp  
 處理就地項目的 SHIFT + F1 說明。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>備註  
 若要啟用即時線上說明，您必須加入  
  
 [!code-cpp[NVC_MFCDocViewSDI # 16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 陳述式，以您`CFrameWnd`類別訊息對應，以及將快速鍵對應表項目時，通常是 SHIFT + F1，以啟用此成員函式。  
  
 如果您的應用程式是 OLE 容器，`OnContextHelp`放至說明模式包含在框架視窗物件內的所有就地項目。 游標會變為箭號和問號和使用者可以將滑鼠指標並按下滑鼠左的按鈕來選取 對話方塊、 視窗、 功能表或命令按鈕。 此成員函式會呼叫 Windows 函式`WinHelp`之說明內容的資料指標下的物件。  
  
##  <a name="oncreateclient"></a>CFrameWnd::OnCreateClient  
 在執行期間由架構呼叫`OnCreate`。  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>參數  
 `lpcs`  
 Windows 的指標[CREATESTRUCT](../../mfc/reference/createstruct-structure.md)結構。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 永遠不會呼叫此函式。  
  
 此函式的預設實作會建立`CView`物件所提供的資訊`pContext`如果可能。  
  
 覆寫此函數來覆寫傳入值`CCreateContext`物件或方法控制項框架視窗的主要工作區中建立的變更。 `CCreateContext`可以覆寫的成員如下所述[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)類別。  
  
> [!NOTE]
>  不會取代傳入的值`CREATESTRUCT`結構。 它們是僅供參考之用。 如果您想要覆寫初始視窗矩形，比方說，覆寫`CWnd`成員函式[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。  
  
##  <a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar  
 系統即將隱藏功能表列中目前的 MFC 應用程式時，會呼叫此函數。  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>備註  
 這個事件處理常式可讓您的應用程式，以隱藏功能表系統時，執行自訂動作。 無法防止功能表隱藏，但是您可以比方說，呼叫其他方法來擷取的功能表樣式或狀態。  
  
##  <a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode  
 呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 *bPreview*  
 指定要將應用程式放在預覽列印模式。 設定為**TRUE**預覽列印中放置**FALSE**取消預覽模式。  
  
 `pState`  
 指標**CPrintPreviewState**結構。  
  
### <a name="remarks"></a>備註  
 預設實作會停用所有標準工具列，並隱藏主功能表以及在用戶端主視窗。 這會變成暫時的 SDI 框架視窗 MDI 框架視窗。  
  
 覆寫此成員函式，以自訂的隱藏和顯示在預覽列印期間控制列和其他框架視窗部分。 呼叫基底類別實作從覆寫的版本中。  
  
##  <a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar  
 系統即將顯示功能表列中目前的 MFC 應用程式時，會呼叫此函數。  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>備註  
 這個事件處理常式可讓您的應用程式功能表即將顯示時執行自訂動作。 無法防止功能表顯示，但是您可以比方說，呼叫其他方法來擷取的功能表樣式或狀態。  
  
##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu  
 更新相關的功能表時由架構呼叫。  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件，代表產生更新命令的功能表。 更新處理常式呼叫[啟用](../../mfc/reference/ccmdui-class.md#enable)成員函式`CCmdUI`物件透過`pCmdUI`更新使用者介面。  
  
##  <a name="recalclayout"></a>CFrameWnd::RecalcLayout  
 當標準主控項列切換為開啟或關閉，或調整框架視窗的大小時，由架構呼叫。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bNotify`  
 決定框架視窗的使用中就地項目是否要接收的版面配置變更通知。 如果**TRUE**，項目，則通知，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 此成員函式的預設實作會呼叫`CWnd`成員函式`RepositionBars`重新定位的框架也在主要用戶端視窗中的所有控制列 (通常`CView`或**MDICLIENT**)。  
  
 覆寫此成員函式，來控制框架視窗的版面配置變更後的外觀和行為的控制列。 例如，呼叫它時開啟或關閉的控制列，或加入另一個控制列。  
  
##  <a name="rectdefault"></a>CFrameWnd::rectDefault  
 將此變數傳遞靜態`CRect`做為參數建立的視窗，可讓 Windows 在選擇視窗的初始大小和位置時。  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>CFrameWnd::SaveBarState  
 呼叫此函式可儲存每個框架視窗所擁有的控制列的相關資訊。  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpszProfileName`  
 初始設定檔案中的區段或儲存狀態資訊的 Windows 登錄中的索引鍵的名稱。  
  
### <a name="remarks"></a>備註  
 這項資訊可以從初始設定檔案使用讀取[LoadBarState](#loadbarstate)。 儲存的資訊包括可見性，水平或垂直方向，停駐狀態和控制列位置。  
  
##  <a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView  
 指定指定的檢視，以 for Rich Preview 現用檢視表。  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>參數  
 `pViewNew`  
 檢視，以啟用指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setactiveview"></a>CFrameWnd::SetActiveView  
 呼叫此成員函式，設定作用中的檢視。  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pViewNew*  
 指定指向[CView](../../mfc/reference/cview-class.md)物件，或**NULL**沒有作用中的檢視。  
  
 `bNotify`  
 指定檢視是否以收到的啟用通知。 如果**TRUE**，`OnActivateView`呼叫新的檢視; 如果**FALSE**，它不是。  
  
### <a name="remarks"></a>備註  
 架構會自動呼叫此函式，因為使用者將焦點變更到檢視，框架視窗內。 您可以明確地呼叫`SetActiveView`若要將焦點變更為指定的檢視。  
  
##  <a name="setdockstate"></a>CFrameWnd::SetDockState  
 呼叫此成員函式中所儲存的狀態資訊適用於`CDockState`框架視窗的控制列的物件。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>參數  
 `state`  
 將預存的狀態套用至框架視窗的控制列。  
  
### <a name="remarks"></a>備註  
 若要還原的控制列先前的狀態，您可以載入儲存的狀態與`CDockState::LoadState`或`Serialize`，然後使用`SetDockState`以套用至框架視窗的控制列。 先前的狀態會儲存在`CDockState`物件`GetDockState`  
  
##  <a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState  
 若要隱藏或顯示目前的 MFC 應用程式中設定功能表顯示的狀態。  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nState`|指定是否要顯示或隱藏功能表。 `nState`參數可以是下列值︰<br /><br /> -如果它隱藏的但如果它會顯示就沒有作用，AFX_MBS_VISIBLE (0x01)-會顯示功能表。<br />-如果它是可見的但沒有任何作用，如果它隱藏 AFX_MBS_HIDDEN (0x02)-會隱藏功能表。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果此方法已成功變更功能表檢視狀態。，否則， `false`。  
  
### <a name="remarks"></a>備註  
 如果發生執行階段錯誤，此方法偵錯模式中的判斷提示，而且會引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。  
  
##  <a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility  
 在目前的 MFC 應用程式可以隱藏或顯示設定 功能表的預設行為。  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nStyle`|指定功能表預設隱藏此項目，或為可見和具有焦點。 `nStyle`參數可以是下列值︰<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)-<br />     功能表會顯示在任何時候，而依預設並沒有焦點。<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     預設隱藏功能表。 如果隱藏功能表上，按下 ALT 鍵以顯示功能表，並將焦點提供。 如果顯示的功能表上，按 alt 鍵或 ESC 鍵以隱藏功能表。<br />-AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0X04)<br />     （合 (OR)）-預設為隱藏功能表。 如果隱藏功能表上，按 F10 鍵，顯示功能表，並將焦點提供。 如果顯示的功能表上，按 F10 鍵來切換開啟或關閉功能表的焦點。 直到您按 alt 鍵或 ESC 鍵，以便隱藏，則會顯示功能表。|  
  
### <a name="remarks"></a>備註  
 如果值`nStyle`參數不是有效的這個方法會判斷提示中偵錯模式而且引發[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)在發行模式中。 發生其他執行階段錯誤時，這個方法偵錯模式中的判斷提示，並引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。  
  
 這個方法會影響狀態中撰寫的應用程式的功能表[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]和更新版本。  
  
##  <a name="setmessagetext"></a>CFrameWnd::SetMessageText  
 呼叫此函式可將字串放在識別碼為 0 的狀態列窗格。  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 指向要放在 [狀態] 列上的字串。  
  
 `nID`  
 字串放置在 [狀態] 列上的資源識別碼的字串。  
  
### <a name="remarks"></a>備註  
 這通常是 [狀態] 列的最左邊，且最長，窗格。  
  
##  <a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition  
 設定 Windows 7 進度列顯示在工作列上的目前位置。  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>參數  
 `nProgressPos`  
 指定要設定的位置。 它必須是所設定的範圍內`SetProgressBarRange`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange  
 Windows 7 進度列顯示在工作列上的範圍設定。  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>參數  
 `nRangeMin`  
 最小值。  
  
 `nRangeMax`  
 最大值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState  
 設定型別和進度列指示器顯示在工作列按鈕上的狀態。  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>參數  
 `tbpFlags`  
 控制進度按鈕的目前狀態的旗標。 指定的下列其中之一旗標，因為所有的狀態為互斥︰ TBPF_NOPROGRESS、 TBPF_INDETERMINATE、 TBPF_NORMAL、 TBPF_ERROR、 TBPF_PAUSED。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon  
 多載。 適用於覆疊工作列按鈕，以指出應用程式狀態，或通知使用者。  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>參數  
 `nIDResource`  
 指定要做為重疊圖示的資源識別碼。 請參閱描述`hIcon`以取得詳細資料。  
  
 `lpcszDescr`  
 提供重疊，協助工具所傳達的資訊的替代文字版本的字串指標。  
  
 `hIcon`  
 要做為重疊圖示的控制代碼。 這應該是一個小型的圖示，測量 16 x 16 像素 96 dpi (dpi)。 如果重疊圖示已經套用到工作列按鈕時，就會取代該現有的覆疊。 這個值可以是 `NULL`。 如何`NULL`值的處理方式取決於是否工作列按鈕代表單一視窗或 windows 群組。 要釋放的呼叫應用程式負責`hIcon`不再需要時。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`如果 OS 版本比 Windows 7，或設定圖示時，發生錯誤。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settitle"></a>CFrameWnd::SetTitle  
 設定視窗物件的標題。  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>參數  
 `lpszTitle`  
 包含視窗物件的標題為字元字串指標。  
  
##  <a name="showcontrolbar"></a>CFrameWnd::ShowControlBar  
 呼叫此成員函式，以顯示或隱藏控制列。  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>參數  
 `pBar`  
 將控制列來顯示或隱藏指標。  
  
 `bShow`  
 如果**TRUE**，指定要顯示控制項列。 如果**FALSE**，指定要隱藏控制列。  
  
 *bDelay*  
 如果**TRUE**，顯示控制項列的延遲時間。 如果**FALSE**，顯示列立即的控制項。  
  
##  <a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows  
 呼叫此成員函式，以顯示所有視窗的子`CFrameWnd`物件。  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `bShow`  
 指定擁有的 windows 是否要顯示或隱藏。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)

