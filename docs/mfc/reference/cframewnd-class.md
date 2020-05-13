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
ms.openlocfilehash: 3bb93420b39be5d6fb9a6691cec8300fdccb0e73
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754971"
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
|[CFramewnd:CFramewnd](#cframewnd)|建構 `CFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFramewnd::啟動幀](#activateframe)|使幀可見且可供使用者使用。|
|[CFramewnd::開始模式狀態](#beginmodalstate)|將框架窗口設置為模態。|
|[CFramewnd::創建](#create)|調用以創建和初始化與`CFrameWnd`物件關聯的 Windows 框架視窗。|
|[CFramewnd::創建檢視](#createview)|在框架中創建未派生自`CView`的視圖。|
|[CFramewnd::Dock控制欄](#dockcontrolbar)|停靠控制欄。|
|[CFramewnd::啟用停靠](#enabledocking)|允許停靠控制欄。|
|[CFramewnd::結束模式狀態](#endmodalstate)|結束幀視窗的模態狀態。 啟用`BeginModalState`由禁用的所有視窗。|
|[CFramewnd::浮動控制欄](#floatcontrolbar)|浮動控制欄。|
|[CFramewnd:取得活動文件](#getactivedocument)|返回活動`CDocument`物件。|
|[CFramewnd:取得活動幀](#getactiveframe)|返回活動`CFrameWnd`物件。|
|[CFramewnd:取得活動檢視](#getactiveview)|返回活動`CView`物件。|
|[CFramewnd::獲取控制欄](#getcontrolbar)|檢索控制欄。|
|[CFramewnd::GetDockstate](#getdockstate)|檢索框架視窗的停靠狀態。|
|[CFramewnd::獲取菜單巴州](#getmenubarstate)|檢索目前 MFC 應用程式中功能表的顯示狀態。|
|[CFramewnd::獲取菜單欄可見性](#getmenubarvisibility)|指示當前 MFC 應用程式中功能表的預設行為是隱藏還是可見。|
|[CFramewnd::獲取消息列](#getmessagebar)|返回指向屬於框架視窗的狀態列的指標。|
|[CFramewnd::獲取消息字串](#getmessagestring)|檢索與命令 ID 對應的消息。|
|[CFramewnd::獲取標題](#gettitle)|檢索相關控制欄的標題。|
|[CFramewnd::初始更新框架](#initialupdateframe)|`OnInitialUpdate`使成員函數屬於框架視窗中的所有檢視。|
|[Cframewnd::在莫里狀態](#inmodalstate)|返回指示框架視窗是否處於模態狀態的值。|
|[CFramewnd:正在跟蹤](#istracking)|確定當前是否正在移動拆分條。|
|[CFramewnd::載入AccelTable](#loadacceltable)|調用以載入加速器表。|
|[CFramewnd::載入欄](#loadbarstate)|調用以恢復控制欄設置。|
|[CFramewnd::載入幀](#loadframe)|調用從資源資訊動態創建幀視窗。|
|[CFramewnd::談判邊界空間](#negotiateborderspace)|協商框架視窗中的邊框空間。|
|[CFramewnd::在巴鍵](#onbarcheck)|每當對指定的控制欄執行操作時,都會調用。|
|[CFramewnd::在上下文説明](#oncontexthelp)|處理就地專案 SHIFT_F1説明。|
|[CFramewnd::打開預覽模式](#onsetpreviewmode)|將應用程式的主框架視窗設置到列印預覽模式和列印預覽模式。|
|[CFramewnd::更新控制欄菜表](#onupdatecontrolbarmenu)|更新關聯功能表時由框架調用。|
|[CFramewnd:recalclayout](#recalclayout)|重新置`CFrameWnd`放 物件的控制欄。|
|[CFramewnd::保存巴爾邦](#savebarstate)|調用以保存控制欄設置。|
|[CFramewnd::設置主動預覽視圖](#setactivepreviewview)|將指定的檢視指定為「富預覽」的活動檢視。|
|[CFramewnd::設置活動檢視](#setactiveview)|設置活動`CView`物件。|
|[CFramewnd::SetDockState](#setdockstate)|調用以停靠主視窗中的幀視窗。|
|[CFramewnd::設置選單欄](#setmenubarstate)|將目前的 MFC 應用程式中選單的顯示狀態設定為隱藏或顯示。|
|[CFramewnd::設置功能表欄可見性](#setmenubarvisibility)|將目前的 MFC 應用程式中選單的預設行為設為隱藏或可見。|
|[CFramewnd::設定消息文字](#setmessagetext)|設定標準狀態列的文本。|
|[CFramewnd::設定進度列位置](#setprogressbarposition)|設定任務列上顯示的 Windows 7 進度列的目前位置。|
|[CFramewnd::設定進度列範圍](#setprogressbarrange)|設置任務列上顯示的 Windows 7 進度列的範圍。|
|[CFramewnd::設置進度列](#setprogressbarstate)|設置任務列按鈕上顯示的進度指示器的類型和狀態。|
|[CFramewnd::設置任務列重疊圖示](#settaskbaroverlayicon)|已多載。 將疊加應用於任務欄按鈕以指示應用程式狀態或通知使用者。|
|[CFramewnd::設置標題](#settitle)|設置相關控制欄的標題。|
|[CFramewnd::顯示控制欄](#showcontrolbar)|呼叫以顯示控制欄。|
|[CFramewnd::顯示擁有的視窗](#showownedwindows)|顯示`CFrameWnd`物件後代的所有視窗。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CFramewnd::打開建立用戶端](#oncreateclient)|為框架創建用戶端視窗。|
|[CFramewnd::打開隱藏選單欄](#onhidemenubar)|在目前的 MFC 應用程式中的選單隱藏之前調用。|
|[CFramewnd::在顯示菜單欄](#onshowmenubar)|在目前的 MFC 應用程式中的功能表顯示之前呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFramewnd::m_bAutoMenuEnable](#m_bautomenuenable)|控制功能表項的自動啟用和禁用功能。|
|[CFramewnd::重新預設](#rectdefault)|創建`CFrameWnd`物件`CRect`時 ,將此靜態作為參數傳遞,以允許 Windows 選擇視窗的初始大小和位置。|

## <a name="remarks"></a>備註

要為應用程式創建有用的框架視窗,請從`CFrameWnd`派生類。 將成員變數添加到派生類以存儲特定於應用程式的數據。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方法可以建構框架視窗:

- 使用 直接建構使用[建立](#create)。

- 使用[LoadFrame](#loadframe)直接構造它。

- 使用文檔範本間接構造它。

在調用`Create``LoadFrame`或之前,必須使用C++**新**運算符在堆上構造幀視窗物件。 在調用`Create`之前,您還可以使用[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函數註冊視窗類,以設置框架的圖示和類樣式。

使用`Create`成員函數將幀的創建參數作為即時參數傳遞。

`LoadFrame`需要的參數少於`Create`,而是從資源檢索其大部分預設值,包括框架的標題、圖示、快速鍵表和菜單。 要被`LoadFrame`訪問,所有這些資源必須具有相同的資源 ID(例如,IDR_MAINFRAME)。

當物件`CFrameWnd`包含檢視和文檔時,它們由框架間接創建,而不是由程式師直接創建。 該`CDocTemplate`物件協調框架的創建、包含檢視的創建以及檢視與相應文件的連接。 建構函數的`CDocTemplate`參數指定所涉及的`CRuntimeClass`三 個類(文檔、框架和檢視)的參數。 框架`CRuntimeClass`使用物件在使用者指定時動態創建新框架(例如,通過使用File New命令或多個文檔介面 (MDI) Window New 命令)。

必須用DECLARE_DYNCREATE聲明派生的`CFrameWnd`幀視窗類,以便上述RUNTIME_CLASS機制正常工作。

A`CFrameWnd`包含預設實現,用於在 Windows 的典型應用程式執行主視窗的以下功能:

- `CFrameWnd`框架視窗跟蹤獨立於 Windows 活動視窗或當前輸入焦點的當前活動檢視。 重新啟動幀時,通過調用`CView::OnActivateView`通知活動視圖。

- 命令`OnSetFocus`消息 和許多常見的幀通知消息(包括`OnHScroll``OnVScroll`由的 和`CWnd`函`CFrameWnd`數處理的消息 )由 幀視窗委派到當前活動視圖。

- 當前活動檢視(或當前活動的 MDI 子框架視窗(在 MDI 幀的情況下)可以確定幀視窗的標題。 可以通過關閉框架視窗的FWS_ADDTOTITLE樣式位來禁用此功能。

- `CFrameWnd`框架視窗管理控制欄、檢視和其他子視窗在框架視窗工作區中的定位。 框架視窗還執行工具列和其他控制欄按鈕的空閒時間更新。 `CFrameWnd`框架視窗還具有用於在工具列和狀態列上下切換的命令的預設實現。

- `CFrameWnd`框架視窗管理主功能表列。 顯示彈出式功能表時,框架視窗使用UPDATE_COMMAND_UI機制來確定應啟用、禁用或檢查哪些功能表項。 當使用者選擇功能表項時,框架視窗會更新具有該命令的消息字串的狀態列。

- `CFrameWnd`框架視窗具有自動轉換鍵盤快速鍵的可選快速鍵表。

- `CFrameWnd`框架視窗具有用於上下文相關説明的可選説明`LoadFrame`ID 集。 幀視窗是半模態狀態的主要協調器,例如上下文敏感的説明 (SHIFT_F1) 和列印預覽模式。

- `CFrameWnd`框架視窗將打開從檔管理器拖動的檔並丟棄在幀視窗中。 如果檔副檔名已註冊並與應用程式關聯,則幀視窗將回應使用者在檔案管理器中打開數據檔或調`ShellExecute`用 Windows 函數時發生的動態數據交換 (DDE) 打開請求。

- 如果框架視窗是主應用程式視窗(即`CWinThread::m_pMainWnd`),當使用者關閉應用程式時,框架視窗會提示使用者保存任何修改的文檔`OnClose`(for 和`OnQueryEndSession`)。

- 如果框架視窗是主應用程式視窗,則框架視窗是運行 WinHelp 的上下文。 關閉幀視窗將關閉 WINHELP。EXE,如果它被啟動,以尋求此應用程式的説明。

請勿使用C++**刪除**運算元來破壞框架視窗。 請改用 `CWnd::DestroyWindow`。 當`CFrameWnd`視窗`PostNcDestroy`被破壞時,將刪除C++物件。 當使用者關閉畫面視窗時,預設`OnClose`處理程式將呼`DestroyWindow`叫 。

有關 的詳細`CFrameWnd`資訊 ,請參閱[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFramewnd::啟動幀

調用此成員函數以啟動和還原框架視窗,以便它可見且可供使用者使用。

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>參數

*nCmdShow*<br/>
指定要傳遞[CWnd 的參數::顯示視窗](../../mfc/reference/cwnd-class.md#showwindow)。 默認情況下,將顯示框架並正確還原。

### <a name="remarks"></a>備註

此成員函數通常在非使用者介面事件(如 DDE、OLE 或其他可能向用戶顯示幀視窗或其內容的事件)之後調用。

默認實現啟動幀並將其帶到 Z 順序的頂部,並在必要時對應用程式的主框架視窗執行相同的步驟。

重寫此成員函數以更改幀的啟動方式。 例如,您可以強制最大化 MDI 子視窗。 添加適當的功能,然後使用顯式*nCmdShow*調用基類版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFramewnd::開始模式狀態

呼叫此成員函式以製作框架視窗強制回應。

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFramewnd:CFramewnd

建構`CFrameWnd`物件,但不創建可見的框架視窗。

```
CFrameWnd();
```

### <a name="remarks"></a>備註

呼叫`Create`以建立可見視窗。

## <a name="cframewndcreate"></a><a name="create"></a>CFramewnd::創建

調用以創建和初始化與`CFrameWnd`物件關聯的 Windows 框架視窗。

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

*lpszClass 名稱*<br/>
指向命名 Windows 類的 null 連接字串。 類名稱可以是註冊到`AfxRegisterWndClass`全域函數或`RegisterClass`Windows 函數的任何名稱。 如果為 NULL,則使用`CFrameWnd`預 定義的預設屬性。

*lpsz 視窗名稱*<br/>
指向表示視窗名稱的 null 連接字串。 用作標題列的文字。

*dwStyle*<br/>
指定視窗[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。 如果希望標題列自動顯示視窗中表示的文檔的名稱,請包括FWS_ADDTOTITLE樣式。

*矩形*<br/>
指定視窗的大小和位置。 *rectDefault*值允許 Windows 指定新視窗的大小和位置。

*pparentwnd*<br/>
指定此框架視窗的父視窗。 對於頂級框架視窗,此參數應為 NULL。

*lpszMenu名稱*<br/>
標識要與視窗一起使用的功能表資源的名稱。 如果選單具有整數 ID 而不是字串,請使用 MAKEINTRESOURCE。 此參數可以是 NULL。

*dwExStyle*<br/>
指定視窗延伸[樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)屬性。

*pContext*<br/>
指定指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。 此參數可以是 NULL。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

分兩`CFrameWnd`步構造物件。 首先,調用構造函數,該構造函數構造`CFrameWnd`物件,然後調`Create`用 ,該構造函數創建 Windows 框架視窗`CFrameWnd`並將其附加到 物件。 `Create`初始化視窗的類名稱和視窗名稱,並註冊其樣式、父功能表和關聯的菜單的預設值。

使用`LoadFrame``Create`而不是從資源載入幀視窗,而不是指定其參數。

## <a name="cframewndcreateview"></a><a name="createview"></a>CFramewnd::創建檢視

調用`CreateView`以在幀內創建視圖。

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pContext*<br/>
指定檢視和文件的類型。

*nID*<br/>
視圖的 ID 號。

### <a name="return-value"></a>傳回值

指標指向`CWnd`物件(如果成功);否則 NULL。

### <a name="remarks"></a>備註

使用此成員函數可以創建框架中未`CView`派生的「檢視」。 調用`CreateView`後,必須手動將視圖設置為活動視圖,並將其設置為可見視圖;這些任務不會由`CreateView`自動執行。

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFramewnd::Dock控制欄

導致控制欄停靠到框架視窗。

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指向要停靠的控制欄。

*nDockBarID*<br/>
確定要考慮停靠的幀視窗的哪一側。 它可以是 0,也可以是以下一個或多個:

- AFX_IDW_DOCKBAR_TOP停靠到框架視窗的頂側。

- AFX_IDW_DOCKBAR_BOTTOM停靠到框架視窗的底部。

- AFX_IDW_DOCKBAR_LEFT停靠在框架視窗的左側。

- AFX_IDW_DOCKBAR_RIGHT停靠在框架視窗的右側。

如果為 0,則控制欄可以停靠到啟用的停靠目標幀視窗中的任何一側。

*lpRect*<br/>
在螢幕座標中確定控制欄將停靠在目標幀視窗的非工作區中的位置。

### <a name="remarks"></a>備註

控制列將停靠到呼叫 CControlBar 時指定的畫面視窗的一側[::啟用停靠](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd::啟用停靠](#enabledocking)。 選擇的一側由*nDockBarID*決定。

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFramewnd::啟用停靠

呼叫此函數以在框架視窗中啟用可停靠的控制欄。

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDock 風格*<br/>
指定框架視窗的哪一側可用作控制欄的停靠點。 它可以是以下一個或多個:

- CBRS_ALIGN_TOP 允許在工作區的頂部停靠。

- CBRS_ALIGN_BOTTOM允許在工作區的底部停靠。

- CBRS_ALIGN_LEFT 允許在工作區左側停靠。

- CBRS_ALIGN_RIGHT允許在工作區的右側停靠。

- CBRS_ALIGN_ANY 允許在工作區的任何一側停靠。

### <a name="remarks"></a>備註

默認情況下,控制項將按以下順序停靠到框架視窗的一側:頂部、底部、左側、右側。

### <a name="example"></a>範例

  請參考[CToolBar 的範例:建立](../../mfc/reference/ctoolbar-class.md#create)。

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFramewnd::結束模式狀態

呼叫此成員函式，將框架視窗從強制回應變更為非強制回應。

```
virtual void EndModalState();
```

### <a name="remarks"></a>備註

`EndModalState`啟用[由 BeginModalState](#beginmodalstate)禁用的所有視窗。

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFramewnd::浮動控制欄

調用此函數可使控制欄不停靠到框架視窗。

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指向要浮動的控制欄。

*點*<br/>
控制件列左上角的位置,位於螢幕座標中。

*dwStyle*<br/>
指定是在其新框架視窗中水平對齊還是垂直對齊控制欄。 它可以是以下任一項:

- CBRS_ALIGN_TOP垂直定向控制條。

- CBRS_ALIGN_BOTTOM垂直定向控制條。

- CBRS_ALIGN_LEFT水準定向控制條。

- CBRS_ALIGN_RIGHT水準定向控制條。

如果傳遞樣式,指定水準和垂直方向,工具列將水準方向。

### <a name="remarks"></a>備註

通常,當程式從以前的執行還原設置時,在應用程式啟動時完成此操作。

當用戶通過釋放滑鼠左鍵,同時將控制欄拖動到無法停靠的位置,由框架調用此功能。

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFramewnd:取得活動文件

呼叫此成員函數以獲取附加到當前活動檢視的電流`CDocument`的指標。

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>傳回值

指向當前[CDocument](../../mfc/reference/cdocument-class.md)的指標。 如果沒有當前文件,則返回 NULL。

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFramewnd:取得活動幀

呼叫此成員函數以獲取指向 MDI 框架視窗的活動多個文件介面 (MDI) 子視窗的指標。

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>傳回值

指向活動 MDI 子視窗的指標。 如果應用程式是 SDI 應用程式,或者 MDI 框架視窗沒有活動文件,則將返回隱式**此**指標。

### <a name="remarks"></a>備註

如果沒有活動 MDI 子項,或者應用程式是單個文檔介面 (SDI),則返回隱式**此**指標。

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFramewnd:取得活動檢視

呼叫此成員函數以獲取附加到框架視窗 ()`CFrameWnd`的活動檢視(如果有)的指標。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>傳回值

指向當前[CView](../../mfc/reference/cview-class.md)的指標。 如果沒有當前檢視,則返回 NULL。

### <a name="remarks"></a>備註

當呼叫 MDI 主框架視窗`CMDIFrameWnd`時, 此功能將傳回 NULL。 在 MDI 應用程式中,MDI 主框架視窗沒有與其關聯的檢視。 相反,每個單獨的子視窗`CMDIChildWnd`( ) 具有一個或多個關聯的檢視。 可以通過首先查找活動 MDI 子視窗,然後查找該子視窗的活動檢視來獲取 MDI 應用程式中的活動檢視。 可以通過調用函`MDIGetActive`數 找到活動 MDI`GetActiveFrame`子視窗,如下 所示:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFramewnd::獲取控制欄

調用`GetControlBar`以訪問與 ID 關聯的控制欄。

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制件欄的 ID 號。

### <a name="return-value"></a>傳回值

指向與 ID 關聯的控制件欄的指標。

### <a name="remarks"></a>備註

*nID*參數是指傳遞給控制`Create`欄 方法的唯一標識碼。 有關控制欄的詳細資訊,請參閱標題為[「控制欄](../../mfc/control-bars.md)」的主題。

`GetControlBar`將返回控制欄,即使它是浮動的,因此當前不是框架的子視窗。

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFramewnd::GetDockstate

調用此成員函數以在`CDockState`物件中存儲有關幀視窗控制欄的狀態資訊。

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>參數

*state*<br/>
在返回時包含幀視窗控制欄的當前狀態。

### <a name="remarks"></a>備註

然後,可以使用`CDockState``CDockState::SaveState`或`Serialize`將的內容寫入存儲。 如果以後希望將控制欄還原到以前的狀態,請使用`CDockState::LoadState``Serialize`或載入狀態,然後調`SetDockState`用 以將以前的狀態應用於框架視窗的控制欄。

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFramewnd::獲取菜單巴州

檢索目前 MFC 應用程式中功能表的顯示狀態。

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>傳回值

傳回值可以具有以下值:

- AFX_MBS_VISIBLE (0x01) - 選單可見。

- AFX_MBS_HIDDEN (0x02) - 選單已隱藏。

### <a name="remarks"></a>備註

如果發生運行時錯誤,此方法在調試模式下斷言,並引發從[CException](../../mfc/reference/cexception-class.md)類派生的異常。

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFramewnd::獲取菜單欄可見性

指示目前 MFC 應用程式中功能表的預設狀態是隱藏還是可見。

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>傳回值

這個方法會傳回下列其中一個值：

- AFX_MBV_KEEPVISIBLE (0x01) - 選單隨時顯示,默認情況下沒有焦點。

- AFX_MBV_DISPLAYONFOCUS (0x02) - 預設情況下,功能表處於隱藏狀態。 如果功能表處於隱藏狀態,請按 ALT 鍵顯示功能表並賦予其焦點。 如果顯示功能表,請按 ALT 或 ESC 鍵將其隱藏。

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124;AFX_MBV_DISPLAYONF10 (0x04) (位元組合 (OR) - 預設情況下,功能表是隱藏的。 如果功能表處於隱藏狀態,請按 F10 鍵顯示功能表並賦予其焦點。 如果顯示功能表,請按 F10 鍵切換功能表上或功能表外的焦點。 選單將顯示,直到您按 ALT 或 ESC 鍵來隱藏它。

### <a name="remarks"></a>備註

如果發生運行時錯誤,此方法在調試模式下斷言,並引發從[CException](../../mfc/reference/cexception-class.md)類派生的異常。

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFramewnd::獲取消息列

調用此成員函數以獲取指向狀態列的指標。

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>傳回值

指向狀態列視窗的指標。

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFramewnd::獲取消息字串

重寫此函數以為命令指示指示提供自定義字串。

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
所需消息的資源識別碼。

*rMessage*<br/>
`CString`要將消息放入的物件。

### <a name="remarks"></a>備註

預設實現只需從資源檔載入*nID*指定的字串。 當狀態列中的消息字串需要更新時,框架將調用此功能。

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFramewnd::獲取標題

檢索視窗物件的標題。

```
CString GetTitle() const;
```

### <a name="return-value"></a>傳回值

包含視窗物件的當前標題的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFramewnd::初始更新框架

使用`IntitialUpdateFrame``Create`建立新的幀後呼叫 。

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向框架視窗關聯的文檔。 可以是 NULL。

*b 使可見*<br/>
如果為 TRUE,則指示幀應變為可見且處於活動狀態。 如果 FALSE,則不使後代可見。

### <a name="remarks"></a>備註

這將導致該幀視窗中的所有檢視接收其`OnInitialUpdate`話務。

此外,如果以前沒有活動檢視,則框架視窗的主視圖將變為活動狀態。 主視圖是具有 AFX_IDW_PANE_FIRST 子 ID 的檢視。 最後,如果*bMakeVisible*是非零,則幀視窗變得可見。 如果*bMakeVisible*為 0,則幀視窗的當前焦點和可見狀態將保持不變。 使用框架的「檔案新建」和「檔案打開」實現時,不必呼叫此功能。

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>Cframewnd::在莫里狀態

調用此成員函數以檢查幀視窗是模態還是無模式。

```
BOOL InModalState() const;
```

### <a name="return-value"></a>傳回值

如果是則非零;否則 0。

## <a name="cframewndistracking"></a><a name="istracking"></a>CFramewnd:正在跟蹤

呼叫此成員函數以確定視窗中的拆分器條當前是否正在移動。

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>傳回值

如果拆分器操作正在進行,則非零;否則 0。

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFramewnd::載入AccelTable

調用以載入指定的加速器表。

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>參數

*lpsz 資源名稱*<br/>
標識加速器資源的名稱。 如果資源使用整數 ID 標識,請使用 MAKEINTRESOURCE。

### <a name="return-value"></a>傳回值

如果已成功載入加速器表,則非零;否則 0。

### <a name="remarks"></a>備註

一次只能載入一個表。

當應用程式終止時,從資源載入的加速器表將自動釋放。

如果調用`LoadFrame`以創建框架視窗,框架將載入一個快速鍵表以及功能表和圖示資源,然後不需要隨後調用此成員函數。

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFramewnd::載入欄

調用此函數以還原幀窗口擁有的每個控制欄的設置。

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
初始化 (INI) 檔案中的節的名稱或儲存狀態資訊的 Windows 註冊表中的鍵的名稱。

### <a name="remarks"></a>備註

恢復的資訊包括可見性、水準/垂直方向、停靠狀態和控制欄位置。

在調用`LoadBarState`之前,必須將要還原的設置寫入註冊表。 通過調用[CWinApp::setRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)將資訊寫入註冊表。 通過呼叫[SaveBarState](#savebarstate)將資訊寫入 INI 檔案。

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFramewnd::載入幀

調用從資源資訊動態創建幀視窗。

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*nID資源*<br/>
與框架視窗關聯的共享資源的 ID。

*dwDefault 樣式*<br/>
框架[的樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果希望標題列自動顯示視窗中表示的文檔的名稱,請包括FWS_ADDTOTITLE樣式。

*pparentwnd*<br/>
指向幀父級的指標。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。 此參數可以是 NULL。

### <a name="remarks"></a>備註

分兩`CFrameWnd`步構造物件。 首先,調用構造函數,該構造函數構造`CFrameWnd`物件,然後調`LoadFrame`用 ,該構造函數載入 Windows 框架視窗和相關資源,並將`CFrameWnd`框架視窗附加到 物件。 *nIDResource*參數指定框架視窗標題的功能表、快速鍵表、圖示和字串資源。

使用`Create`成員函數,而不是`LoadFrame`指定幀視窗的所有創建參數時。

當框架使用`LoadFrame`文檔範本物件創建框架視窗時,它將調用它。

框架使用*pContext*參數指定要連接到框架視窗的物件,包括任何包含的檢視物件。 呼叫`LoadFrame`時,可以將*pContext*參數設定為 NULL。

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFramewnd::m_bAutoMenuEnable

啟用此數據成員(預設值)時,當使用者拉下功能表時,將會自動禁用沒有ON_UPDATE_COMMAND_UI或ON_COMMAND處理程式的菜單項。

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>備註

將自動啟用具有ON_COMMAND處理程式但沒有ON_UPDATE_COMMAND_UI處理程式的功能表項。

設置此資料成員時,功能表項將自動啟用,其方式與啟用工具列按鈕的方式相同。

> [!NOTE]
> `m_bAutoMenuEnable`對頂級功能表項沒有影響。

此數據成員簡化了基於當前選擇的可選命令的實現,並減少了編寫ON_UPDATE_COMMAND_UI處理程式以啟用和禁用功能表項的需要。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFramewnd::談判邊界空間

調用此成員函數以在 OLE 就地激活期間協商框架視窗中的邊框空間。

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>參數

*nBorderCmd*<br/>
包含 以下值之一`enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lprect邊框*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)結構或指定邊框座標的[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數是`CFrameWnd`實現 OLE 邊界空間協商。

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFramewnd::在巴鍵

每當對指定的控制欄執行操作時,都會調用。

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
顯示的控制欄的 ID。

### <a name="return-value"></a>傳回值

如果存在控制條,則非零;否則 0。

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFramewnd::在上下文説明

處理就地專案 SHIFT_F1説明。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>備註

要啟用上下文相關的幫助,必須添加

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

語句到`CFrameWnd`類消息映射,並添加一個快捷表條目(通常 SHIFT_F1)以啟用此成員函數。

如果應用程式是 OLE`OnContextHelp`容器, 則將幀視窗物件中包含的所有就地專案放入説明模式。 游標將變為箭頭和問號,然後使用者可以移動滑鼠指標並按滑鼠左鍵選擇對話框、視窗、功能表或命令按鈕。 此成員函數使用游標下物件的`WinHelp`説明上下文調用 Windows 函數。

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFramewnd::打開建立用戶端

在執行 期間由框架呼`OnCreate`叫 。

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
指向 Windows [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)結構的指標。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

切勿調用此函數。

如果可能,此函數的預設實現`CView`將創建一個物件,該消息來自*pContext*中提供的資訊。

重寫此函數以覆蓋`CCreateContext`物件中傳遞的值或更改框架視窗主工作區中的控制項的創建方式。 可以`CCreateContext`重寫的成員在[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)類中描述。

> [!NOTE]
> 不要替換結構中`CREATESTRUCT`傳遞的值。 它們僅供參考使用。 例如,如果要覆蓋初始視窗矩形,請重寫`CWnd`成員函數[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFramewnd::打開隱藏選單欄

當系統要隱藏當前 MFC 應用程式中的功能表欄時,將調用此功能。

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>備註

此事件處理程式使應用程式能夠在系統要隱藏功能表時執行自訂操作。 不能阻止功能表被隱藏,但例如,您可以調用其他方法來檢索功能表樣式或狀態。

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFramewnd::打開預覽模式

呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>參數

*b預覽*<br/>
指定是否將應用程式置於列印預覽模式。 設置為 TRUE 以放置在列印預覽中,FALSE 設置為取消預覽模式。

*pState*<br/>
指向結構的`CPrintPreviewState`指標。

### <a name="remarks"></a>備註

預設實現禁用所有標準工具列並隱藏主功能表和主用戶端視窗。 這將將 MDI 框架視窗轉換為臨時 SDI 框架視窗。

覆蓋此成員功能以自訂列印預覽期間控制欄和其他框架視窗部件的隱藏和顯示。 從重寫版本內調用基類實現。

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFramewnd::在顯示菜單欄

當系統要在當前 MFC 應用程式中顯示功能表欄時,將調用此功能。

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>備註

此事件處理程式使應用程式能夠在菜單即將顯示時執行自定義操作。 不能阻止顯示功能表,但例如,您可以調用其他方法來檢索功能表樣式或狀態。

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFramewnd::更新控制欄菜表

更新關聯功能表時由框架調用。

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新命令的功能表的[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。 更新處理程式透過*pCmdUI*`CCmdUI`呼叫物件的[啟用](../../mfc/reference/ccmdui-class.md#enable)成員函數以更新使用者介面。

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFramewnd:recalclayout

當標準控制欄打開或關閉或調整框架視窗大小時,由框架調用。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*b 通知*<br/>
確定框架視窗的活動就地專案是否接收佈局更改通知。 如果為 TRUE,則會通知該專案;如果為 TRUE,則通知該專案。否則 FALSE。

### <a name="remarks"></a>備註

此成員函數的預設實現調用`CWnd`成員函`RepositionBars`數 重新定位幀和主用戶端視窗中的所有控制欄(通常`CView`為 a 或 MDICLIENT)。

重寫此成員函數以在幀視窗佈局更改后控制控制欄的外觀和行為。 例如,在打開或關閉控制欄或添加其他控制欄時調用它。

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFramewnd::重新預設

建立視窗時`CRect`,將此靜態作為參數傳遞,以允許 Windows 選擇視窗的初始大小和位置。

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFramewnd::保存巴爾邦

調用此函數以存儲有關幀窗口擁有的每個控制欄的資訊。

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
初始化檔中的節的名稱或儲存狀態資訊的 Windows 註冊表中的鍵的名稱。

### <a name="remarks"></a>備註

此資訊可以使用[LoadBarState](#loadbarstate)從初始化檔中讀取。 儲存的資訊包括可見性、水準/垂直方向、停靠狀態和控制欄位置。

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFramewnd::設置主動預覽視圖

將指定的檢視指定為「富預覽」的活動檢視。

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>參數

*pView New*<br/>
指向要啟動的視圖的指標。

### <a name="remarks"></a>備註

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFramewnd::設置活動檢視

調用此成員函數以設置活動檢視。

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*pView New*<br/>
指定指向[CView](../../mfc/reference/cview-class.md)物件的指標,為無活動檢視指定 NULL。

*b 通知*<br/>
指定是否通知檢視啟動。 如果為`OnActivateView`TRUE,則呼叫新檢視;如果為"TRUE",則為 "TRUE",則為"TRUE",為"TRUE"請求如果 FALSE,則不是。

### <a name="remarks"></a>備註

當使用者將焦點更改為框架視窗中的檢視時,框架將自動調用此函數。 您可以顯式調用`SetActiveView`以將焦點更改為指定的檢視。

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFramewnd::SetDockState

調用此成員函數將存儲在物件中`CDockState`的狀態資訊應用於幀視窗的控制欄。

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>參數

*state*<br/>
將存儲的狀態應用於框架視窗的控制欄。

### <a name="remarks"></a>備註

要還原控制列欄的先前狀態,可以使用`CDockState::LoadState``Serialize`或載入儲存的狀態,然後使用`SetDockState`它 將其應用於框架視窗的控制欄。 以前的狀態存儲在物件中`CDockState`,`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFramewnd::設置選單欄

將目前的 MFC 應用程式中選單的顯示狀態設定為隱藏或顯示。

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*n州*|[在]指定是顯示還是隱藏選單。 *nState*參數可以具有以下值:<br /><br />- AFX_MBS_VISIBLE (0x01) - 如果選單處於隱藏狀態,則顯示該功能表,但如果菜單可見,則無效果。<br />- AFX_MBS_HIDDEN (0x02) - 如果選單可見,則隱藏菜單,但如果該功能表隱藏,則無效。|

### <a name="return-value"></a>傳回值

如果此方法成功更改功能表狀態,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果發生運行時錯誤,此方法在調試模式下斷言,並引發從[CException](../../mfc/reference/cexception-class.md)類派生的異常。

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFramewnd::設置功能表欄可見性

將目前的 MFC 應用程式中選單的預設行為設為隱藏或可見。

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*nStyle*|[在]指定功能表在預設情況下是隱藏的,還是可見的,並且具有焦點。 *nStyle*參數可以具有以下值:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     功能表隨時顯示,默認情況下沒有焦點。<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     默認情況下,功能表處於隱藏狀態。 如果功能表處於隱藏狀態,請按 ALT 鍵顯示功能表並賦予其焦點。 如果顯示功能表,請按 ALT 或 ESC 鍵隱藏選單。<br />- AFX_MBV_顯示器 (0x02) &#124;AFX_MBV_DISPLAYONF10 (0x04)<br />     (位元組 (OR)) - 預設情況下,功能表是隱藏的。 如果功能表處於隱藏狀態,請按 F10 鍵顯示功能表並賦予其焦點。 如果顯示功能表,請按 F10 鍵切換功能表上或功能表外的焦點。 選單將顯示,直到您按 ALT 或 ESC 鍵來隱藏它。|

### <a name="remarks"></a>備註

如果*nStyle*參數的值無效,則此方法在調試模式下斷言,並在釋放模式下引發[CInvalidArgexception。](../../mfc/reference/cinvalidargexception-class.md) 如果出現其他運行時錯誤,此方法在調試模式下斷言,並引發從[CException](../../mfc/reference/cexception-class.md)類派生的異常。

此方法會影響為 Windows Vista 和更高版本的應用程式中功能表的狀態。

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFramewnd::設定消息文字

呼叫此函數以在 ID 為 0 的狀態列窗格中放置字串。

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要放置在狀態列上的字串。

*nID*<br/>
要放置在狀態列上的字串資源 ID。

### <a name="remarks"></a>備註

這通常是狀態列中最左側且最長的窗格。

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFramewnd::設定進度列位置

設定任務列上顯示的 Windows 7 進度列的目前位置。

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*n 進步Pos*<br/>
指定要設置的位置。 它必須在設置`SetProgressBarRange`的範圍內。

### <a name="remarks"></a>備註

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFramewnd::設定進度列範圍

設置任務列上顯示的 Windows 7 進度列的範圍。

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>參數

*恩朗明*<br/>
最小值。

*nRangeMax*<br/>
最大值。

### <a name="remarks"></a>備註

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFramewnd::設置進度列

設置任務列按鈕上顯示的進度指示器的類型和狀態。

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>參數

*tbpFlags*<br/>
控制進度按鈕的當前狀態的標誌。 只指定以下標誌之一,因為所有狀態都是互斥的:TBPF_NOPROGRESS、TBPF_INDETERMINATE、TBPF_NORMAL、TBPF_ERRORTBPF_PAUSED。

### <a name="remarks"></a>備註

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFramewnd::設置任務列重疊圖示

已多載。 將疊加應用於任務欄按鈕以指示應用程式狀態或通知使用者。

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>參數

*nID資源*<br/>
指定要用作疊加的圖示的資源 ID。 有關詳細資訊,請參閱*hIcon*的說明。

*lpcszDescr*<br/>
指向字串的指標,該字串提供疊加所傳達的資訊的 alt 文本版本,用於輔助功能。

*hIcon*<br/>
用作疊加的圖示的句柄。 這應該是一個小圖示,每英寸 96 點(dpi)測量 16x16 圖元。 如果疊加圖示已應用於任務欄按鈕,則替換現有疊加。 此值可以是 NULL。 NULL 值的處理方式取決於任務列按鈕是表示單個視窗還是一組視窗。 調用應用程式有責任在不再需要*hIcon*時釋放它。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE;如果操作系統版本小於 Windows 7 或出現錯誤,則設置圖示。

### <a name="remarks"></a>備註

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFramewnd::設置標題

設置視窗物件的標題。

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
指向包含視窗物件標題的字串的指標。

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFramewnd::顯示控制欄

呼叫此成員函數以顯示或隱藏控制欄。

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指向要顯示或隱藏的控制欄的指標。

*b 顯示*<br/>
如果為 TRUE,則指定要顯示控制欄。 如果 FALSE,則指定要隱藏控制欄。

*bDelay*<br/>
如果為 TRUE,則延遲顯示控制條。 如果 FALSE,則立即顯示控制欄。

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFramewnd::顯示擁有的視窗

呼叫此成員函數以顯示`CFrameWnd`物件後代的所有視窗。

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
指定是顯示還是隱藏擁有的視窗。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)
