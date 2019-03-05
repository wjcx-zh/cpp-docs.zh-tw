---
title: CFrameWnd 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
ms.openlocfilehash: 7bdb681754a500ab86538f3397b4c07284b850d0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300880"
---
# <a name="cframewnd-class"></a>CFrameWnd 類別

提供 Windows 單一文件介面 (SDI) 重疊或快顯框架視窗的功能，以及管理視窗的成員。

## <a name="syntax"></a>語法

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|建構 `CFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|對使用者的畫面格可看到和使用。|
|[CFrameWnd::BeginModalState](#beginmodalstate)|設定強制回應框架視窗。|
|[CFrameWnd::Create](#create)|建立和初始化相關聯的 Windows 框架視窗呼叫`CFrameWnd`物件。|
|[CFrameWnd::CreateView](#createview)|建立不衍生自內檢視`CView`。|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|停駐控制列。|
|[CFrameWnd::EnableDocking](#enabledocking)|可讓被停駐控制列。|
|[CFrameWnd::EndModalState](#endmodalstate)|結束框架視窗的強制回應狀態。 可讓所有停用 windows `BeginModalState`。|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|浮動控制列。|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|傳回現用`CDocument`物件。|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|傳回現用`CFrameWnd`物件。|
|[CFrameWnd::GetActiveView](#getactiveview)|傳回現用`CView`物件。|
|[CFrameWnd::GetControlBar](#getcontrolbar)|擷取控制列。|
|[CFrameWnd::GetDockState](#getdockstate)|擷取框架視窗停駐狀態。|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|擷取目前的 MFC 應用程式中的功能表的顯示狀態。|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|指出是否隱藏或顯示的功能表中目前的 MFC 應用程式的預設行為。|
|[CFrameWnd::GetMessageBar](#getmessagebar)|狀態列屬於框架視窗中傳回的指標。|
|[CFrameWnd::GetMessageString](#getmessagestring)|擷取訊息對應到命令識別碼。|
|[CFrameWnd::GetTitle](#gettitle)|擷取相關的控制列的標題。|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|會導致`OnInitialUpdate`屬於呼叫框架視窗中的所有檢視的成員函式。|
|[CFrameWnd::InModalState](#inmodalstate)|傳回值，指出在框架視窗處於強制回應狀態。|
|[CFrameWnd::IsTracking](#istracking)|決定是否分割列目前正在移動。|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|呼叫以載入快速鍵對應表。|
|[CFrameWnd::LoadBarState](#loadbarstate)|若要還原控制列設定的呼叫。|
|[CFrameWnd::LoadFrame](#loadframe)|若要以動態方式建立資源資訊的框架視窗呼叫。|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|會在框架視窗的框線空間的交涉。|
|[CFrameWnd::OnBarCheck](#onbarcheck)|只要指定的控制列上執行動作時呼叫。|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|處理 shift+f1 說明就地項目。|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|傳入和傳出預覽列印模式，請設定應用程式的主框架視窗。|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|更新相關聯的功能表時，由架構呼叫。|
|[CFrameWnd::RecalcLayout](#recalclayout)|重新置放控制列的`CFrameWnd`物件。|
|[CFrameWnd::SaveBarState](#savebarstate)|呼叫以儲存控制列的設定。|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|指定要使用 for Rich Preview 中的檢視指定的檢視。|
|[CFrameWnd::SetActiveView](#setactiveview)|設定作用`CView`物件。|
|[CFrameWnd::SetDockState](#setdockstate)|若要停駐在主視窗的框架視窗呼叫。|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|若要隱藏或顯示目前的 MFC 應用程式中設定功能表的顯示狀態。|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|在目前的 MFC 應用程式會隱藏或顯示設定 功能表的預設行為。|
|[CFrameWnd::SetMessageText](#setmessagetext)|設定標準的狀態列的文字。|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|設定顯示在工作列上的 Windows 7 進度列目前位置。|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|設定顯示在工作列上的 Windows 7 進度列範圍。|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|設定型別和進度列指示器在工作列按鈕上顯示的狀態。|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|多載。 適用於重疊的工作列按鈕，以指出應用程式狀態或使用者的通知。|
|[CFrameWnd::SetTitle](#settitle)|設定相關的控制列的標題。|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|呼叫以顯示控制列。|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|顯示所有視窗的下階`CFrameWnd`物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|建立用戶端視窗框架。|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|隱藏目前的 MFC 應用程式中的功能表之前呼叫。|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|在目前的 MFC 應用程式中的功能表會顯示之前呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|控制項的自動啟用和停用的功能表項目功能。|
|[CFrameWnd::rectDefault](#rectdefault)|傳遞此靜態`CRect`做為參數建立時`CFrameWnd`物件，以允許 Windows 選擇視窗的初始大小和位置。|

## <a name="remarks"></a>備註

若要建立有用的框架視窗以進行您的應用程式，衍生的類別`CFrameWnd`。 將成員變數新增至衍生的類別，以儲存您的應用程式特定的資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方式來建構框架視窗：

- 直接使用建構[建立](#create)。

- 直接使用建構[LoadFrame](#loadframe)。

- 間接建構使用文件範本。

您可以呼叫之前`Create`或是`LoadFrame`，您必須建構使用 c + + 堆積上的框架視窗物件**新**運算子。 然後再呼叫`Create`，您也可以註冊視窗類別[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函式，可將框架的圖示和類別樣式。

使用`Create`傳遞畫面格的建立參數為立即的引數的成員函式。

`LoadFrame` 需要較少的引數比`Create`，並改為擷取資源，包括畫面格的標題、 圖示、 快速鍵對應表，以及功能表中的大部分的預設值。 若要可供`LoadFrame`，所有這些資源必須有相同的資源識別碼 (例如，IDR_MAINFRAME)。

當`CFrameWnd`物件包含檢視表和文件，它們藉由間接的架構，而不是直接由程式設計師。 `CDocTemplate`物件用來協調建立框架的、 包含檢視中，建立和檢視，以適當的文件的連接。 參數`CDocTemplate`建構函式指定`CRuntimeClass`三個類別的相關 （文件、 框架和檢視）。 A `CRuntimeClass` framework 會使用物件以動態方式建立新的畫面格時由使用者 （例如，藉由使用新檔案的命令或多個文件介面 (MDI) 視窗中新的命令）。

框架視窗類別衍生自`CFrameWnd`必須宣告與 DECLARE_DYNCREATE，為了讓上述 RUNTIME_CLASS 機制才能正常運作。

A`CFrameWnd`包含一般的應用程式中執行 Windows 的主視窗的下列函式的預設實作：

- A`CFrameWnd`框架視窗會追蹤的目前使用的檢視，都是獨立的 Windows 使用中視窗或目前的輸入的焦點。 當框架就會重新啟動時，現用檢視表會收到通知，藉由呼叫`CView::OnActivateView`。

- 命令訊息和許多常見的畫面格通知訊息，包括由`OnSetFocus`， `OnHScroll`，並`OnVScroll`函式`CWnd`，委派所`CFrameWnd`框架視窗至目前使用中的檢視。

- 目前使用中的檢視 （或目前現用 MDI 子框架視窗，在 MDI 框架的情況下） 可以判斷標題的框架視窗。 關閉 FWS_ADDTOTITLE 樣式位元，框架視窗可以停用這項功能。

- A`CFrameWnd`框架視窗會管理控制列、 檢視和框架視窗的用戶端區域內其他子視窗的位置。 框架視窗也會執行更新的工具列和其他控制列按鈕的閒置時間。 A`CFrameWnd`框架視窗也會有切換開啟和關閉工具列和狀態列命令的預設實作。

- A`CFrameWnd`框架視窗會管理主功能表列。 出現快顯功能表時，框架視窗會使用 UPDATE_COMMAND_UI 機制來決定哪一個功能表項目應該啟用、 停用，或檢查。 當使用者選取功能表項目時，框架視窗會更新 [狀態] 列與代表該命令的訊息字串。

- A`CFrameWnd`框架視窗會有選擇性的快速鍵對應表，會自動將轉譯鍵盤快速鍵。

- A`CFrameWnd`框架視窗會有設定的選擇性說明 ID`LoadFrame`所用的即時線上說明。 框架視窗會組織 semimodal 狀態，例如即時線上說明 (SHIFT + F1)] 和 [預覽列印模式主要 orchestrator。

- A`CFrameWnd`框架視窗會開啟檔案管理員從其拖放在框架視窗上的檔案。 如果副檔名是註冊和應用程式相關聯，框架視窗會回應動態資料交換 (DDE) 開啟要求，當使用者開啟資料檔在檔案管理員或時發生`ShellExecute`呼叫 Windows 函式。

- 如果框架視窗是主應用程式視窗 (也就是`CWinThread::m_pMainWnd`)，當使用者關閉應用程式中，框架視窗會提示使用者儲存任何修改過的文件 (如`OnClose`和`OnQueryEndSession`)。

- 如果主應用程式視窗的框架視窗，框架視窗會是執行 WinHelp 的內容。 關閉框架視窗會關閉 WINHELP。如果它已針對此應用程式的啟動，EXE。

不使用 c + +**刪除**終結框架視窗的運算子。 請改用 `CWnd::DestroyWindow`。 `CFrameWnd`實作`PostNcDestroy`終結視窗時，將會刪除 c + + 物件。 當使用者關閉框架視窗時，預設值`OnClose`處理常式會呼叫`DestroyWindow`。

如需詳細資訊`CFrameWnd`，請參閱 <<c2> [ 框架 Windows](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame

呼叫此成員函式，來啟用和還原框架視窗，如此就可看到和使用的使用者。

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>參數

*nCmdShow*<br/>
指定要傳遞至參數[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。 根據預設，會顯示框架，並將其正確地還原中。

### <a name="remarks"></a>備註

此成員函式通常會在非使用者介面事件，例如 DDE、 OLE、 或其他可能會向使用者顯示的框架視窗或其內容的事件後呼叫。

預設實作會啟用框架和將它帶到疊置順序的頂端和，如有必要，執行相同的步驟，應用程式的主框架視窗。

覆寫此成員函式，若要變更啟動畫面格的方式。 例如，您可以強制要最大化的 MDI 子視窗。 加入適當的功能，然後呼叫基底類別版本，其明確*nCmdShow*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState

呼叫此成員函式以製作框架視窗強制回應。

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd

建構`CFrameWnd`物件，但不會建立可見的框架視窗。

```
CFrameWnd();
```

### <a name="remarks"></a>備註

呼叫`Create`建立可見的視窗。

##  <a name="create"></a>  CFrameWnd::Create

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

*lpszClassName*<br/>
指向以 null 結束的字元字串，可命名 Windows 類別。 類別名稱可以是任何名稱向`AfxRegisterWndClass`全域函式或`RegisterClass`Windows 函式。 如果是 NULL，會使用預先定義的預設`CFrameWnd`屬性。

*lpszWindowName*<br/>
指向以 null 結束的字元字串，表示視窗名稱。 用來作為文字的標題列。

*dwStyle*<br/>
指定時間範圍[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。 如果您想要的標題列，以自動顯示在視窗中表示文件的名稱，請包含 FWS_ADDTOTITLE 樣式。

*rect*<br/>
指定的大小和視窗的位置。 *RectDefault*值允許指定的大小和位置的新視窗中的 Windows。

*pParentWnd*<br/>
指定此框架視窗的父視窗。 這個參數應該是最上層框架視窗的 NULL。

*lpszMenuName*<br/>
識別要使用與視窗的功能表資源的名稱。 如果功能表的整數識別碼，而不是字串，請使用 MAKEINTRESOURCE。 這個參數可以是 NULL。

*dwExStyle*<br/>
指定時間範圍，擴充[樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)屬性。

*pContext*<br/>
指定的指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果初始化成功則為非零否則為 0。

### <a name="remarks"></a>備註

建構`CFrameWnd`兩個步驟中的物件。 首先，叫用的建構函式，建構`CFrameWnd`物件，然後再呼叫`Create`，這會建立 Windows 框架視窗，並將它附加至`CFrameWnd`物件。 `Create` 初始化視窗的類別名稱和視窗名稱，並註冊其樣式、 父代，以及相關的功能表的預設值。

使用`LoadFrame`而非`Create`載入框架視窗從的資源，而不是指定其引數。

##  <a name="createview"></a>  CFrameWnd::CreateView

呼叫`CreateView`建立範圍內的檢視。

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pContext*<br/>
指定檢視和文件的類型。

*nID*<br/>
檢視的識別碼。

### <a name="return-value"></a>傳回值

指標`CWnd`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

使用不是此成員函式來建立 「 檢視 」 `CView`-衍生的範圍內。 之後呼叫`CreateView`，您必須手動設定為 作用中的檢視，並將它設為可見; 這些工作不會自動執行由`CreateView`。

##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar

會導致要停駐在框架視窗的控制列。

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

*pBar*<br/>
若要停駐控制列指標。

*nDockBarID*<br/>
決定所要考量的停駐在框架視窗的哪一面。 它可以是 0，或一或多個項目：

- AFX_IDW_DOCKBAR_TOP 停駐於上方的框架視窗中。

- AFX_IDW_DOCKBAR_BOTTOM 停駐在框架視窗的底部。

- AFX_IDW_DOCKBAR_LEFT 停駐在框架視窗的左邊。

- AFX_IDW_DOCKBAR_RIGHT 停駐在框架視窗的右側。

如果為 0，則可以停駐控制列啟用停駐在目的地框架視窗中的任何一側。

*lpRect*<br/>
判斷在螢幕座標，其中將目的地框架視窗中非工作區停駐控制列。

### <a name="remarks"></a>備註

將停駐控制列，同時呼叫中指定的框架視窗側邊的其中一個[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)並[CFrameWnd::EnableDocking](#enabledocking)。 取決於所選的側邊*nDockBarID*。

##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking

呼叫此函式可啟用在框架視窗中的可停駐控制列。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDockStyle*<br/>
指定的框架視窗哪一邊可以做為停駐控制列的網站。 它可以是下列其中一個或多個項目：

- CBRS_ALIGN_TOP 可停駐在工作區頂端。

- CBRS_ALIGN_BOTTOM 可讓工作區底部的停駐。

- CBRS_ALIGN_LEFT 可讓用戶端區域左側停駐。

- CBRS_ALIGN_RIGHT 可讓用戶端區域右側的停駐。

- CBRS_ALIGN_ANY 可讓用戶端區域的任一邊的停駐。

### <a name="remarks"></a>備註

根據預設，控制列將會停駐的側邊的框架視窗中，依下列順序： 頂端、 底端、 左、 右。

### <a name="example"></a>範例

  範例，請參閱[CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create)。

##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState

呼叫此成員函式，將框架視窗從強制回應變更為非強制回應。

```
virtual void EndModalState();
```

### <a name="remarks"></a>備註

`EndModalState` 可讓所有視窗停用[BeginModalState](#beginmodalstate)。

##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar

呼叫此函式會導致不停駐在框架視窗的控制列。

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>參數

*pBar*<br/>
將控制列浮動點。

*point*<br/>
位置，在螢幕座標中放置控制列的左上的角。

*dwStyle*<br/>
指定是否要將控制列水平或垂直對齊其新的框架視窗內。 它可以是下列其中一項動作：

- CBRS_ALIGN_TOP 是控制列的垂直方向。

- CBRS_ALIGN_BOTTOM 是控制列的垂直方向。

- CBRS_ALIGN_LEFT 是控制列的水平方向。

- CBRS_ALIGN_RIGHT 是控制列的水平方向。

如果樣式傳遞指定水平和垂直方向，工具列方向是水平。

### <a name="remarks"></a>備註

一般而言，這是在應用程式啟動程式從上次執行還原的設定時。

當使用者會導致卸除作業不適用於停駐位置拖曳控制列時釋放滑鼠左鍵時，此函式是由架構呼叫。

##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument

呼叫此成員函式取得目前的指標`CDocument`附加至目前的現用檢視表。

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>傳回值

目前的指標[CDocument](../../mfc/reference/cdocument-class.md)。 如果沒有目前文件，會傳回 NULL。

##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame

呼叫此成員函式，來取得指向使用中的多個文件介面 (MDI) 子視窗的 MDI 框架視窗。

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>傳回值

現用的 MDI 子視窗指標。 如果應用程式是 SDI 應用程式，或 MDI 框架視窗有無使用中文件，隱含**這**會傳回指標。

### <a name="remarks"></a>備註

如果沒有使用中的 MDI 子系，或應用程式為單一文件介面 (SDI)，隱含**這**會傳回指標。

##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView

呼叫此成員函式，以取得使用中的檢視 （如果有的話） 附加至框架視窗的指標 ( `CFrameWnd`)。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>傳回值

目前的指標[CView](../../mfc/reference/cview-class.md)。 如果沒有任何目前的檢視，會傳回 NULL。

### <a name="remarks"></a>備註

此函式會傳回 NULL 呼叫 MDI 主框架視窗時 ( `CMDIFrameWnd`)。 在 MDI 應用程式，MDI 主框架視窗沒有與其相關聯的檢視。 相反地，每個個別的子視窗 ( `CMDIChildWnd`) 有一或多個相關聯的檢視。 先尋找作用中的 MDI 子視窗，然後再尋找該子視窗的 使用中的檢視，可以取得 MDI 應用程式中的現用檢視表。 您可以找到現用的 MDI 子視窗呼叫函式`MDIGetActive`或`GetActiveFrame`如下列所示：

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar

呼叫`GetControlBar`來存取與識別碼相關聯的控制列

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
一種控制列識別碼。

### <a name="return-value"></a>傳回值

與識別碼相關聯的控制列指標

### <a name="remarks"></a>備註

*NID*參數是指傳遞給唯一識別碼`Create`控制列的方法。 如需有關控制列的詳細資訊，請參閱主題[控制列](../../mfc/control-bars.md)。

`GetControlBar` 會傳回控制列，即使它浮點數，而且不是目前子視窗的框架。

##  <a name="getdockstate"></a>  CFrameWnd::GetDockState

呼叫此成員函式，來儲存狀態資訊中的框架視窗的控制列`CDockState`物件。

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>參數

*state*<br/>
包含在傳回的框架視窗的控制列的目前狀態。

### <a name="remarks"></a>備註

然後，您可以撰寫的內容`CDockState`若要使用儲存體`CDockState::SaveState`或`Serialize`。 如果您稍後想要還原至先前狀態的控制列，載入的狀態與`CDockState::LoadState`或是`Serialize`，然後呼叫`SetDockState`来套用至框架視窗的控制列的 先前的狀態。

##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState

擷取目前的 MFC 應用程式中的功能表的顯示狀態。

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>傳回值

傳回值可以是下列值：

- AFX_MBS_VISIBLE (0x01)-會顯示功能表。

- AFX_MBS_HIDDEN (0x02)-在隱藏功能表。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法偵錯模式中的判斷提示，並引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。

##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility

指出是否隱藏或顯示的功能表中目前的 MFC 應用程式的預設狀態。

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>傳回值

這個方法會傳回下列值之一：

- AFX_MBV_KEEPVISIBLE (0x01)-會顯示功能表完全時間，同時依預設未取得焦點。

- AFX_MBV_DISPLAYONFOCUS (0x02)-預設為隱藏功能表。 如果功能表隱藏的請按 ALT 鍵以顯示功能表，並給予焦點。 如果會顯示功能表，請按 alt 鍵或 ESC 鍵以將其隱藏。

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) （合 (OR)）-預設為隱藏功能表。 如果功能表隱藏的請按 F10 鍵，可顯示功能表，並給予焦點。 如果會顯示功能表，請按 F10 鍵來切換開啟或關閉功能表的焦點。 直到您按 alt 鍵或 ESC 鍵以將其隱藏，則會顯示功能表。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法偵錯模式中的判斷提示，並引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。

##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar

呼叫此成員函式，以取得 [狀態] 列的指標。

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>傳回值

[狀態列] 視窗的指標。

##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString

覆寫這個函式來提供自訂字串的命令 Id。

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
資源所需的訊息識別碼。

*rMessage*<br/>
`CString` 要放置訊息到其中的物件。

### <a name="remarks"></a>備註

預設實作只會載入所指定的字串*nID*從資源檔。 在狀態列中的訊息字串需要更新時，此函式是由架構呼叫。

##  <a name="gettitle"></a>  CFrameWnd::GetTitle

擷取視窗物件的標題。

```
CString GetTitle() const;
```

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，包含目前的視窗物件的標題。

##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame

呼叫`IntitialUpdateFrame`之後建立新的框架，具有`Create`。

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
文件框架視窗有相關聯的點。 可以是 NULL。

*bMakeVisible*<br/>
如果為 TRUE，表示框架都應該變成可見且作用中。 如果為 FALSE，則會顯示沒有子系。

### <a name="remarks"></a>備註

這可讓所有的檢視以接收該框架視窗中其`OnInitialUpdate`呼叫。

此外，如果有先前未使用中的檢視，框架視窗的主要檢視會使用中。 主要的檢視是具有子系識別碼的 AFX_IDW_PANE_FIRST 的檢視。 最後，框架視窗就會顯示如果*bMakeVisible*為非零值。 如果*bMakeVisible*是 0，則目前的焦點和框架視窗的可見狀態將保持不變。 您不需要呼叫此函式時使用的新檔案] 和 [開啟檔案架構的實作。

##  <a name="inmodalstate"></a>  CFrameWnd::InModalState

呼叫此成員函式，以檢查是否強制回應或非強制回應框架視窗。

```
BOOL InModalState() const;
```

### <a name="return-value"></a>傳回值

非零值，如果否。否則為 0。

##  <a name="istracking"></a>  CFrameWnd::IsTracking

呼叫以判斷目前正在移動視窗中的分隔器列是否此成員函式。

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>傳回值

如果分隔器作業正在進行則為非零否則為 0。

##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable

呼叫以載入指定的快速鍵對應表。

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
識別加速器資源的名稱。 如果整數 id 識別資源，使用 MAKEINTRESOURCE

### <a name="return-value"></a>傳回值

如果已成功載入快速鍵對應表，為非零否則為 0。

### <a name="remarks"></a>備註

只有一個資料表可以載入一次。

從資源載入快速鍵對應表會在應用程式終止時自動釋放。

如果您呼叫`LoadFrame`建立框架視窗，架構會載入快速鍵對應表的功能表和圖示的資源，以及與此成員函式的後續呼叫就不需要。

##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState

呼叫此函式以還原擁有的框架視窗的每個控制列的設定。

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
初始設定 (INI) 檔案中的區段或儲存狀態資訊的 Windows 登錄中的索引鍵的名稱。

### <a name="remarks"></a>備註

還原的資訊包括可見性、 水平或垂直方向、 停駐狀態和控制列位置。

您想要還原的設定必須寫入至登錄，才能呼叫`LoadBarState`。 寫入登錄中的資訊，藉由呼叫[CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)。 寫入 INI 檔案中的資訊，藉由呼叫[SaveBarState](#savebarstate)。

##  <a name="loadframe"></a>  CFrameWnd::LoadFrame

若要以動態方式建立資源資訊的框架視窗呼叫。

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
框架視窗相關聯的共用資源的識別碼。

*dwDefaultStyle*<br/>
框架[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果您想要的標題列，以自動顯示在視窗中表示文件的名稱，請包含 FWS_ADDTOTITLE 樣式。

*pParentWnd*<br/>
畫面格的父代指標。

*pContext*<br/>
指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是 NULL。

### <a name="remarks"></a>備註

建構`CFrameWnd`兩個步驟中的物件。 首先，叫用的建構函式，建構`CFrameWnd`物件，然後再呼叫`LoadFrame`，這會載入 Windows 框架視窗和相關聯的資源，並附加框架視窗至`CFrameWnd`物件。 *NIDResource*參數指定的功能表、 快速鍵對應表、 圖示和框架視窗的標題的字串資源。

使用`Create`成員函式而非`LoadFrame`想要指定所有框架視窗的建立參數時。

這個架構會呼叫`LoadFrame`當它建立框架視窗中使用文件範本物件。

架構會使用*pContext*引數來指定要連接到框架視窗中，包括任何物件所包含的檢視物件。 您可以設定*pContext*引數為 NULL，當您呼叫`LoadFrame`。

##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable

（這是預設值） 啟用此資料成員時，使用者提取功能表時自動停用沒有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 處理常式的功能表項目。

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>備註

有 ON_COMMAND 處理常式，但沒有 ON_UPDATE_COMMAND_UI 處理常式的功能表項目將會自動啟用。

當設定這個資料成員時，功能表項目會自動啟用啟用的工具列按鈕的方式相同。

> [!NOTE]
> `m_bAutoMenuEnable` 沒有任何作用，在最上層的功能表項目。

此資料成員會簡化根據目前的選取範圍的選擇性命令的實作，並減少需要撰寫 ON_UPDATE_COMMAND_UI 處理常式，啟用和停用功能表項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace

呼叫此成員函式，在 OLE 就地啟用期間交涉框線框架視窗中的空間。

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>參數

*nBorderCmd*<br/>
中的以下值的其中一個`enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
指標[RECT](/windows/desktop/api/windef/ns-windef-tagrect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定框線的座標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是`CFrameWnd`OLE 框線空間交涉的實作。

##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck

只要指定的控制列上執行動作時呼叫。

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
長條顯示控制項的 ID。

### <a name="return-value"></a>傳回值

控制列才會存在; 如果為非零否則為 0。

##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp

處理 shift+f1 說明就地項目。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>備註

若要啟用即時線上說明，您必須新增

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

陳述式，以您`CFrameWnd`類別訊息對應，以及將快速鍵對應表項目時，通常是 SHIFT + F1，以啟用此成員函式。

如果您的應用程式的 OLE 容器，`OnContextHelp`放至說明模式包含在框架視窗物件內的所有就地項目。 游標會變為有箭號和問號和使用者可以將滑鼠指標並按下滑鼠左的按鈕來選取 對話方塊、 視窗、 功能表或命令按鈕。 此成員函式會呼叫 Windows 函式`WinHelp`具有說明內容的游標下的物件。

##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient

在執行期間由架構呼叫`OnCreate`。

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
Windows 的指標[CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa)結構。

*pContext*<br/>
指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

永遠不會呼叫此函式。

此函式的預設實作會建立`CView`物件所提供的資訊*pContext*、 的話。

此函式來覆寫傳入的值會覆寫`CCreateContext`物件或方法控制項框架視窗的主要工作區中建立的變更。 `CCreateContext`您可以覆寫的成員所述[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)類別。

> [!NOTE]
>  並不會取代傳入值`CREATESTRUCT`結構。 它們是僅供內部使用。 如果您想要覆寫初始視窗矩形，比方說，覆寫`CWnd`成員函式[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。

##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar

當系統即將隱藏目前的 MFC 應用程式中的功能表列，會呼叫此函數。

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>備註

這個事件處理常式可讓您的應用程式，以執行自訂動作，當系統即將隱藏功能表。 無法防止 [] 功能表中隱藏，但比方說，您可以呼叫其他方法來擷取功能表樣式或狀態。

##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode

呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>參數

*bPreview*<br/>
指定要將應用程式放在預覽列印模式。 在預覽列印，FALSE 表示取消預覽模式中，將設定為 TRUE。

*pState*<br/>
指標`CPrintPreviewState`結構。

### <a name="remarks"></a>備註

預設實作會停用所有的標準工具列，並隱藏主功能表和 [主要用戶端] 視窗。 這會將 MDI 框架視窗變成暫時的 SDI 框架視窗。

覆寫此成員函式，以自訂的隱藏和顯示在預覽列印期間控制列和其他框架視窗組件。 呼叫基底類別實作從覆寫的版本中。

##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar

當系統即將顯示在目前的 MFC 應用程式中的功能表列，會呼叫此函數。

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>備註

這個事件處理常式可讓您的應用程式，以執行自訂動作，當功能表即將顯示時。 無法防止功能表顯示，但比方說，您可以呼叫其他方法來擷取功能表樣式或狀態。

##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu

更新相關聯的功能表時，由架構呼叫。

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件，代表產生更新命令的功能表。 更新處理常式呼叫[啟用](../../mfc/reference/ccmdui-class.md#enable)成員函式`CCmdUI`物件傳遞*pCmdUI*更新使用者介面。

##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout

當標準主控項列切換為開或關或框架視窗調整大小時，由架構呼叫。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*bNotify*<br/>
決定框架視窗的使用中就地項目是否接收的配置變更通知。 如果為 TRUE，則會收到通知的項目;否則為 FALSE。

### <a name="remarks"></a>備註

此成員函式的預設實作會呼叫`CWnd`成員函式`RepositionBars`重新定位的框架也在主要用戶端視窗中的所有控制列 (通常`CView`或 MDICLIENT)。

覆寫這個成員函式之後已變更的框架視窗版面配置控制項的外觀和行為的控制列。 例如，呼叫它時您開啟或關閉的控制列，或加入另一個控制列。

##  <a name="rectdefault"></a>  CFrameWnd::rectDefault

傳遞此靜態`CRect`做為參數建立視窗中，以允許 Windows 選擇視窗的初始大小和位置時。

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState

呼叫此函式可儲存由框架視窗擁有每個控制列的相關資訊。

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
中的初始設定檔案的區段或儲存狀態資訊的 Windows 登錄中的索引鍵的名稱。

### <a name="remarks"></a>備註

這項資訊可以從初始設定檔案使用讀取[LoadBarState](#loadbarstate)。 儲存的資訊包括停駐狀態和控制列位置的水平或垂直方向的可視性。

##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView

指定要使用 for Rich Preview 中的檢視指定的檢視。

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>參數

*pViewNew*<br/>
指標，要啟動的檢視。

### <a name="remarks"></a>備註

##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView

呼叫此成員函式，可以設定使用中的檢視。

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*pViewNew*<br/>
指定的指標[CView](../../mfc/reference/cview-class.md)物件或 NULL 表示沒有使用中的檢視。

*bNotify*<br/>
指定檢視是否收到的啟用通知。 如果為 TRUE，`OnActivateView`呼叫新的檢視; 如果為 FALSE，不是。

### <a name="remarks"></a>備註

架構會自動呼叫此函式，因為使用者將焦點變更至框架視窗內的檢視。 您可以明確呼叫`SetActiveView`若要將焦點變更至指定的檢視。

##  <a name="setdockstate"></a>  CFrameWnd::SetDockState

呼叫此成員函式，將狀態資訊儲存在套用`CDockState`框架視窗的控制列物件。

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>參數

*state*<br/>
適用於框架視窗的控制列的預存的狀態。

### <a name="remarks"></a>備註

若要還原的控制列先前的狀態，您可以載入與儲存的狀態`CDockState::LoadState`或是`Serialize`，然後使用`SetDockState`套用至框架視窗的控制列。 先前的狀態會儲存在`CDockState`物件 `GetDockState`

##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState

若要隱藏或顯示目前的 MFC 應用程式中設定功能表的顯示狀態。

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*nState*|[in]指定是否要顯示或隱藏功能表。 *NState*參數可以是下列值：<br /><br />-如果它隱藏的但是沒有任何作用，如果顯示，AFX_MBS_VISIBLE (0x01)-會顯示功能表。<br />-如果它是可見的但是沒有任何作用，如果它隱藏 AFX_MBS_HIDDEN (0x02-) 會隱藏功能表。|

### <a name="return-value"></a>傳回值

如果這個方法已成功變更功能表狀態，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法偵錯模式中的判斷提示，並引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。

##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility

在目前的 MFC 應用程式會隱藏或顯示設定 功能表的預設行為。

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*nStyle*|[in]指定功能表預設隱藏此項目，或為可見和具有焦點。 *NStyle*參數可以是下列值：<br /><br />-AFX_MBV_KEEPVISIBLE (0X01)-<br />     功能表會顯示任何時間，而且依預設未取得焦點。<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     預設為隱藏功能表。 如果功能表隱藏的請按 ALT 鍵以顯示功能表，並給予焦點。 如果會顯示功能表，請按 alt 鍵或 ESC 鍵以隱藏功能表。<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     （合 (OR)）-預設為隱藏功能表。 如果功能表隱藏的請按 F10 鍵，可顯示功能表，並給予焦點。 如果會顯示功能表，請按 F10 鍵來切換開啟或關閉功能表的焦點。 直到您按 alt 鍵或 ESC 鍵以將其隱藏，則會顯示功能表。|

### <a name="remarks"></a>備註

如果值*nStyle*參數不是有效的這個方法會判斷提示中偵錯模式而且引發[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)在發行模式中。 發生其他執行階段錯誤，這個方法偵錯模式中的判斷提示，並引發例外狀況衍生自[CException](../../mfc/reference/cexception-class.md)類別。

這個方法影響狀態的功能表中撰寫適用於 Windows Vista 和更新版本的應用程式。

##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText

呼叫此函式可將字串放在識別碼為 0 的狀態列窗格。

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要放在 [狀態] 列上的字串。

*nID*<br/>
字串的字串放在狀態列上的資源識別碼。

### <a name="remarks"></a>備註

這通常是最左邊，且最長的 [狀態] 列。

##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition

設定 Windows 7 進度列顯示在工作列上的目前位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*nProgressPos*<br/>
指定要設定的位置。 它必須是所設定的範圍內`SetProgressBarRange`。

### <a name="remarks"></a>備註

##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange

設定 Windows 7 進度列顯示在工作列上的範圍。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>參數

*nRangeMin*<br/>
最小值。

*nRangeMax*<br/>
最大值。

### <a name="remarks"></a>備註

##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState

設定型別和進度列指示器在工作列按鈕上顯示的狀態。

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>參數

*tbpFlags*<br/>
控制進度按鈕的目前狀態的旗標。 因為是互斥的所有狀態，請指定下列旗標的其中之一：TBPF_NOPROGRESS、 TBPF_INDETERMINATE、 TBPF_NORMAL、 TBPF_ERROR、 TBPF_PAUSED。

### <a name="remarks"></a>備註

##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon

多載。 適用於重疊的工作列按鈕，以指出應用程式狀態，或通知使用者。

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
指定將作為重疊圖示資源識別碼。 請參閱描述*hIcon*如需詳細資訊。

*lpcszDescr*<br/>
提供的覆疊，協助工具所傳達的資訊的替代文字版本的字串指標。

*hIcon*<br/>
將作為重疊圖示的控制代碼。 這應該是小型的圖示，並測量 16 x 16 像素，在 96 每英吋點數 (dpi)。 如果重疊圖示已套用至工作列按鈕中，會取代該現有的重疊。 這個值可以是 NULL。 處理 NULL 值的方式取決於是否在工作列按鈕代表單一視窗或 windows 群組。 它是以釋放呼叫的應用程式的責任*hIcon*不再需要時。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE如果作業系統版本低於 Windows 7，或設定圖示時，發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="settitle"></a>  CFrameWnd::SetTitle

設定視窗物件的標題。

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
包含標題的視窗物件的字元字串指標。

##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar

呼叫此成員函式，以顯示或隱藏控制列。

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>參數

*pBar*<br/>
要顯示或隱藏的控制列指標。

*bShow*<br/>
如果為 TRUE，指定控制列顯示。 如果為 FALSE，指定控制列設為隱藏。

*bDelay*<br/>
如果為 TRUE，會延遲顯示控制列。 如果為 FALSE，會顯示控制列 立即。

##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows

呼叫此成員函式，以顯示子系的所有 windows`CFrameWnd`物件。

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定擁有的 windows 是否要顯示或隱藏。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)
