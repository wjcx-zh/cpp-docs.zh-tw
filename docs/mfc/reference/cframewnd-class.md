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
ms.openlocfilehash: 5e40f08447d24eed51588b5c2dfa87e289d99eed
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561573"
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
|[CFrameWnd：： CFrameWnd](#cframewnd)|建構 `CFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFrameWnd：： ActivateFrame](#activateframe)|讓框架可見並可供使用者使用。|
|[CFrameWnd：： BeginModalState](#beginmodalstate)|將框架視窗設定為強制回應。|
|[CFrameWnd：： Create](#create)|呼叫以建立和初始化與物件相關聯的 Windows 框架視窗 `CFrameWnd` 。|
|[CFrameWnd：： CreateView](#createview)|在非衍生自的框架內建立一個視圖 `CView` 。|
|[CFrameWnd：:D ockControlBar](#dockcontrolbar)|停駐控制列。|
|[CFrameWnd：： EnableDocking](#enabledocking)|允許固定控制列。|
|[CFrameWnd：： EndModalState](#endmodalstate)|結束框架視窗的強制回應狀態。 啟用所有停用的視窗 `BeginModalState` 。|
|[CFrameWnd：： FloatControlBar](#floatcontrolbar)|浮動控制列。|
|[CFrameWnd：： GetActiveDocument](#getactivedocument)|傳回使用中的 `CDocument` 物件。|
|[CFrameWnd：： GetActiveFrame](#getactiveframe)|傳回使用中的 `CFrameWnd` 物件。|
|[CFrameWnd：： GetActiveView](#getactiveview)|傳回使用中的 `CView` 物件。|
|[CFrameWnd：： GetControlBar](#getcontrolbar)|抓取控制列。|
|[CFrameWnd：： GetDockState](#getdockstate)|抓取框架視窗的固定狀態。|
|[CFrameWnd：： GetMenuBarState](#getmenubarstate)|抓取目前 MFC 應用程式中功能表的顯示狀態。|
|[CFrameWnd：： GetMenuBarVisibility](#getmenubarvisibility)|指出目前 MFC 應用程式中功能表的預設行為是隱藏的或可見的。|
|[CFrameWnd：： GetMessageBar](#getmessagebar)|傳回屬於框架視窗之狀態列的指標。|
|[CFrameWnd：： GetMessageString](#getmessagestring)|抓取對應至命令識別碼的訊息。|
|[CFrameWnd：： GetTitle](#gettitle)|抓取相關控制列的標題。|
|[CFrameWnd：： InitialUpdateFrame](#initialupdateframe)|導致 `OnInitialUpdate` 呼叫屬於框架視窗中所有視圖的成員函式。|
|[CFrameWnd：： InModalState](#inmodalstate)|傳回值，指出框架視窗是否處於強制回應狀態。|
|[CFrameWnd：： IsTracking](#istracking)|判斷是否正在移動分隔器列。|
|[CFrameWnd：： LoadAccelTable](#loadacceltable)|呼叫以載入快速鍵對應表。|
|[CFrameWnd：： LoadBarState](#loadbarstate)|呼叫以還原 control bar 設定。|
|[CFrameWnd：： LoadFrame](#loadframe)|呼叫以從資源資訊動態建立框架視窗。|
|[CFrameWnd：： NegotiateBorderSpace](#negotiateborderspace)|在框架視窗中協調框線空間。|
|[CFrameWnd：： OnBarCheck](#onbarcheck)|每次在指定的控制列上執行動作時呼叫。|
|[CFrameWnd：： OnCoNtextHelp](#oncontexthelp)|處理就地專案的 SHIFT + F1 說明。|
|[CFrameWnd：： OnSetPreviewMode](#onsetpreviewmode)|將應用程式的主框架視窗移入和移出預覽列印模式。|
|[CFrameWnd：： OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|當相關聯的功能表更新時，由架構呼叫。|
|[CFrameWnd：： RecalcLayout](#recalclayout)|重新置放物件的控制列 `CFrameWnd` 。|
|[CFrameWnd：： SaveBarState](#savebarstate)|呼叫以儲存控制列設定。|
|[CFrameWnd：： SetActivePreviewView](#setactivepreviewview)|將指定的視圖指定為現用視圖，以進行 Rich Preview。|
|[CFrameWnd：： SetActiveView](#setactiveview)|設定使用中的 `CView` 物件。|
|[CFrameWnd：： SetDockState](#setdockstate)|呼叫將框架視窗停駐于主視窗中。|
|[CFrameWnd：： SetMenuBarState](#setmenubarstate)|將目前 MFC 應用程式中功能表的顯示狀態設定為 [隱藏] 或 [已顯示]。|
|[CFrameWnd：： SetMenuBarVisibility](#setmenubarvisibility)|將目前 MFC 應用程式中功能表的預設行為設定為隱藏或可見。|
|[CFrameWnd：： SetMessageText](#setmessagetext)|設定標準狀態列的文字。|
|[CFrameWnd：： SetProgressBarPosition](#setprogressbarposition)|設定工作列上顯示之 Windows 7 進度列的目前位置。|
|[CFrameWnd：： SetProgressBarRange](#setprogressbarrange)|設定工作列上顯示的 Windows 7 進度列範圍。|
|[CFrameWnd：： SetProgressBarState](#setprogressbarstate)|設定工作列按鈕上顯示之進度指示器的類型和狀態。|
|[CFrameWnd：： SetTaskbarOverlayIcon](#settaskbaroverlayicon)|多載。 將重迭套用至工作列按鈕，以指出應用程式狀態或使用者的通知。|
|[CFrameWnd：： SetTitle](#settitle)|設定相關控制列的標題。|
|[CFrameWnd：： ShowControlBar](#showcontrolbar)|呼叫以顯示控制列。|
|[CFrameWnd：： ShowOwnedWindows](#showownedwindows)|顯示屬於物件下階的所有視窗 `CFrameWnd` 。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CFrameWnd：： OnCreateClient](#oncreateclient)|建立框架的用戶端視窗。|
|[CFrameWnd：： OnHideMenuBar](#onhidemenubar)|在目前的 MFC 應用程式中隱藏功能表之前呼叫。|
|[CFrameWnd：： OnShowMenuBar](#onshowmenubar)|在目前的 MFC 應用程式中顯示功能表之前呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFrameWnd：： m_bAutoMenuEnable](#m_bautomenuenable)|控制功能表項目的自動啟用和停用功能。|
|[CFrameWnd：： rectDefault](#rectdefault)|`CRect`建立物件時，請將此靜態作為參數傳遞 `CFrameWnd` ，以允許 Windows 選擇視窗的初始大小和位置。|

## <a name="remarks"></a>備註

若要為您的應用程式建立有用的框架視窗，請從衍生類別 `CFrameWnd` 。 將成員變數加入至衍生類別，以儲存您應用程式的特定資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方式可建立框架視窗：

- 使用 [Create](#create)來直接建立。

- 使用 [LoadFrame](#loadframe)直接進行建立。

- 使用檔範本間接進行建立。

在您呼叫 `Create` 或之前 `LoadFrame` ，您必須使用 c + + 運算子，在堆積上建立框架視窗物件 **`new`** 。 在呼叫之前 `Create` ，您也可以使用 [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) 全域函式註冊視窗類別，以設定框架的圖示和類別樣式。

使用成員函式 `Create` ，將框架的建立參數傳遞為立即引數。

`LoadFrame` 比起需要較少的引數 `Create` ，並改為從資源中取出大部分的預設值，包括框架的標題、圖示、快速鍵對應表及功能表。 若要存取 `LoadFrame` ，所有這些資源都必須具有相同的資源識別碼 (例如 IDR_MAINFRAME) 。

當 `CFrameWnd` 物件包含視圖和檔時，架構會間接建立它們，而不是直接由程式設計人員所建立。 `CDocTemplate`物件會協調框架的建立、建立包含的視圖，以及將視圖連接到適當的檔。 此函式的參數會 `CDocTemplate` 指定 `CRuntimeClass` 三個相關類別的， (檔、框架和視圖) 。 `CRuntimeClass`當使用者指定時，架構會使用物件來動態建立新的框架 (例如，使用 [檔案新命令] 或 [多重文件介面] (MDI) 視窗新命令) 。

衍生自的框架視窗類別 `CFrameWnd` 必須以 DECLARE_DYNCREATE 宣告，上述 RUNTIME_CLASS 機制才能正常運作。

`CFrameWnd`包含在 Windows 的一般應用程式中執行下列主視窗功能的預設實作為：

- `CFrameWnd`框架視窗會持續追蹤目前的使用中視圖，此視窗與 Windows 使用中視窗或目前的輸入焦點無關。 當畫面格重新開機時，會藉由呼叫來通知現用視圖 `CView::OnActivateView` 。

- 命令訊息和許多常見的框架通知訊息，包括由的、和函式所處理的訊息， `OnSetFocus` `OnHScroll` `OnVScroll` `CWnd` 都會由 `CFrameWnd` 框架視窗委派給目前使用中的視圖。

- 目前使用中的 view (或目前作用中的 MDI 子框架視窗，如果是 MDI 框架，) 可以決定框架視窗的標題。 您可以關閉框架視窗的 FWS_ADDTOTITLE 樣式位，來停用這項功能。

- `CFrameWnd`框架視窗會在框架視窗的工作區中管理控制列、視圖及其他子視窗的位置。 框架視窗也會進行工具列和其他控制列按鈕的閒置時間更新。 `CFrameWnd`框架視窗也有命令的預設執行，可以切換工具列和狀態列。

- `CFrameWnd`框架視窗會管理主功能表列。 顯示快顯功能表時，框架視窗會使用 UPDATE_COMMAND_UI 機制來判斷應啟用、停用或選取哪些功能表項目。 當使用者選取功能表項目時，框架視窗會以該命令的訊息字串來更新狀態列。

- `CFrameWnd`框架視窗有選擇性的快速鍵對應表，可自動轉譯鍵盤快捷按鍵。

- `CFrameWnd`框架視窗具有使用設定的選擇性說明識別碼 `LoadFrame` ，可用於即時線上說明。 框架視窗是 semimodal 狀態的主要協調器，例如即時線上說明 (SHIFT + F1) 和預覽列印模式。

- `CFrameWnd`框架視窗會開啟從 [檔案管理員] 拖曳的檔案，並放在框架視窗上。 如果副檔名已註冊且與應用程式相關聯，則框架視窗會回應動態資料交換 (DDE) 開啟要求，這是使用者在檔案管理員中開啟資料檔案時，或在呼叫 Windows 函式時所發生 `ShellExecute` 。

- 如果框架視窗是主要的應用程式視窗 (也就是 `CWinThread::m_pMainWnd`) ，當使用者關閉應用程式時，框架視窗會提示使用者將任何修改過的檔儲存 (`OnClose` 和 `OnQueryEndSession`) 。

- 如果框架視窗是主應用程式視窗，框架視窗就是執行 WinHelp 的內容。 關閉框架視窗將會關閉 WINHELP.EXE 如果它已啟動以取得此應用程式的說明。

請勿使用 c + + **`delete`** 運算子來終結框架視窗。 請改用 `CWnd::DestroyWindow`。 `CFrameWnd`當終結視窗時，的執行 `PostNcDestroy` 會刪除 c + + 物件。 當使用者關閉框架視窗時，預設 `OnClose` 處理常式將會呼叫 `DestroyWindow` 。

如需的詳細資訊 `CFrameWnd` ，請參閱 [框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a> CFrameWnd：： ActivateFrame

呼叫此成員函式來啟動和還原框架視窗，讓使用者可以看到並使用它。

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>參數

*nCmdShow*<br/>
指定要傳遞至 [CWnd：： ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)的參數。 根據預設，畫面格會顯示並正確還原。

### <a name="remarks"></a>備註

此成員函式通常會在非使用者介面事件（例如 DDE、OLE 或其他事件）之後呼叫，而這些事件可能會向使用者顯示框架視窗或其內容。

預設的執行會啟動畫面格，並將其放到迭置順序的頂端，並視需要針對應用程式的主框架視窗執行相同的步驟。

覆寫這個成員函式，以變更框架的啟用方式。 例如，您可以強制讓 MDI 子視窗最大化。 新增適當的功能，然後以明確的 *nCmdShow*呼叫基類版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a> CFrameWnd：： BeginModalState

呼叫此成員函式以製作框架視窗強制回應。

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a> CFrameWnd：： CFrameWnd

`CFrameWnd`會建立物件，但不會建立可見的框架視窗。

```
CFrameWnd();
```

### <a name="remarks"></a>備註

呼叫 `Create` 以建立可見視窗。

## <a name="cframewndcreate"></a><a name="create"></a> CFrameWnd：： Create

呼叫以建立和初始化與物件相關聯的 Windows 框架視窗 `CFrameWnd` 。

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
指向以 null 結束的字元字串，該字串會為 Windows 類別命名。 類別名稱可以是任何以全域函式 `AfxRegisterWndClass` 或 Windows 函數註冊的名稱 `RegisterClass` 。 如果是 Null，則會使用預先定義的預設 `CFrameWnd` 屬性。

*lpszWindowName*<br/>
指向表示視窗名稱的以 null 結束的字元字串。 當做標題列的文字使用。

*dwStyle*<br/>
指定視窗 [樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 屬性。 如果您希望標題列自動顯示視窗中所表示的檔案名稱，請包含 FWS_ADDTOTITLE 樣式。

*矩形*<br/>
指定視窗的大小和位置。 *RectDefault*值可讓 Windows 指定新視窗的大小和位置。

*pParentWnd*<br/>
指定此框架視窗的父視窗。 最上層框架視窗的此參數應為 Null。

*lpszMenuName*<br/>
識別要與視窗一起使用之功能表資源的名稱。 如果功能表具有整數識別碼而非字串，請使用 MAKEINTRESOURCE。 這個參數可以是 Null。

*dwExStyle*<br/>
指定視窗擴充 [樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) 屬性。

*pContext*<br/>
指定 [CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md) 結構的指標。 這個參數可以是 Null。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為0。

### <a name="remarks"></a>備註

`CFrameWnd`以兩個步驟來建立物件。 首先，叫用函式來建立此 `CFrameWnd` 物件，然後呼叫 `Create` ，以建立 Windows 框架視窗並將其附加至 `CFrameWnd` 物件。 `Create` 初始化視窗的類別名稱和視窗名稱，並註冊其樣式、父系和關聯功能表的預設值。

使用 `LoadFrame` 而不是 `Create` 從資源載入框架視窗，而不是指定其引數。

## <a name="cframewndcreateview"></a><a name="createview"></a> CFrameWnd：： CreateView

呼叫 `CreateView` 來建立框架內的視圖。

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pContext*<br/>
指定視圖和檔的類型。

*nID*<br/>
視圖的 ID 編號。

### <a name="return-value"></a>傳回值

`CWnd`如果成功，則為物件的指標; 否則為 Null。

### <a name="remarks"></a>備註

您可以使用這個成員函式來建立不是 `CView` 在框架內衍生的「views」。 在呼叫之後 `CreateView` ，您必須手動將視圖設定為 [作用中]，並將它設定為可見; 這些工作不會自動執行 `CreateView` 。

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a> CFrameWnd：:D ockControlBar

使控制列停駐在框架視窗。

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指向要停駐的控制列。

*nDockBarID*<br/>
決定要考慮停駐的框架視窗的側邊。 它可以是0，或下列一或多項：

- AFX_IDW_DOCKBAR_TOP 停駐在框架視窗的頂端。

- AFX_IDW_DOCKBAR_BOTTOM 停駐在框架視窗的底部。

- AFX_IDW_DOCKBAR_LEFT 停駐在框架視窗的左邊。

- AFX_IDW_DOCKBAR_RIGHT 停駐在框架視窗的右側。

如果為0，則控制列可以停駐在目的框架視窗中已啟用的任何側邊停駐位置。

*lpRect*<br/>
決定在螢幕座標中，控制列將停駐于目的框架視窗的非工作區。

### <a name="remarks"></a>備註

控制列將會停駐在呼叫 [CControlBar：： EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) 和 [CFrameWnd：： EnableDocking](#enabledocking)所指定的框架視窗的其中一個邊。 選擇的側邊取決於 *nDockBarID*。

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a> CFrameWnd：： EnableDocking

呼叫此函式可在框架視窗中啟用可停駐控制列。

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDockStyle*<br/>
指定框架視窗的側邊可作為控制列的停駐網站。 它可以是下列其中一項或多項：

- CBRS_ALIGN_TOP 允許在工作區頂端停駐。

- CBRS_ALIGN_BOTTOM 允許在工作區底部停駐。

- CBRS_ALIGN_LEFT 允許位於工作區左邊的停駐位置。

- CBRS_ALIGN_RIGHT 允許在工作區右側停駐。

- CBRS_ALIGN_ANY 允許在工作區的任一側停駐。

### <a name="remarks"></a>備註

依預設，控制列將會停駐在框架視窗的側邊，順序如下：頂端、底部、左方、右邊。

### <a name="example"></a>範例

  請參閱 [CToolBar：： Create](../../mfc/reference/ctoolbar-class.md#create)的範例。

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a> CFrameWnd：： EndModalState

呼叫此成員函式，將框架視窗從強制回應變更為非強制回應。

```
virtual void EndModalState();
```

### <a name="remarks"></a>備註

`EndModalState` 啟用 [BeginModalState](#beginmodalstate)停用的所有 windows。

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a> CFrameWnd：： FloatControlBar

呼叫此函式，讓控制列不會停駐在框架視窗。

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指向要浮動的控制列。

*點*<br/>
位置（以螢幕座標為單位），將會在其中放置控制列的左上角。

*dwStyle*<br/>
指定是否要在新的框架視窗中水準或垂直對齊控制列。 它可以是下列其中一項：

- CBRS_ALIGN_TOP 會垂直排列控制列的方向。

- CBRS_ALIGN_BOTTOM 會垂直排列控制列的方向。

- CBRS_ALIGN_LEFT 水準排列控制列的方向。

- CBRS_ALIGN_RIGHT 水準排列控制列的方向。

如果傳遞的樣式同時指定水準和垂直方向，則會水準導向工具列。

### <a name="remarks"></a>備註

一般來說，當程式正在還原先前執行的設定時，就會在應用程式啟動時完成這項工作。

當使用者在將控制列拖曳至無法停駐的位置時，藉由釋放滑鼠左鍵時，架構會呼叫這個函式。

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a> CFrameWnd：： GetActiveDocument

呼叫這個成員函式，以取得目前的 `CDocument` 現用視圖目前附加的指標。

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>傳回值

目前 [CDocument](../../mfc/reference/cdocument-class.md)的指標。 如果沒有目前的檔，則會傳回 Null。

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a> CFrameWnd：： GetActiveFrame

呼叫這個成員函式，以取得使用中多重文件介面的指標 (mdi 框架視窗的 MDI) 子視窗。

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>傳回值

現用 MDI 子視窗的指標。 如果應用程式是 SDI 應用程式，或 MDI 框架視窗沒有使用中的檔，則 **`this`** 會傳回隱含指標。

### <a name="remarks"></a>備註

如果沒有作用中的 MDI 子系，或應用程式是 (SDI) 的單一檔介面，則 **`this`** 會傳回隱含指標。

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a> CFrameWnd：： GetActiveView

呼叫此成員函式，以取得使用中視圖的指標 (如果任何附加至框架視窗的)  ( `CFrameWnd`) 。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>傳回值

目前 [CView](../../mfc/reference/cview-class.md)的指標。 如果沒有目前的視圖，則會傳回 Null。

### <a name="remarks"></a>備註

當針對 MDI 主框架視窗呼叫時，此函式會傳回 Null， ( `CMDIFrameWnd`) 。 在 MDI 應用程式中，MDI 主框架視窗沒有相關聯的視圖。 相反地，每個個別的子視窗 ( `CMDIChildWnd`) 會有一個或多個相關聯的視圖。 您可以先尋找作用中的 MDI 子視窗，然後尋找該子視窗的現用視圖，藉以取得 MDI 應用程式中的現用視圖。 您可以藉由呼叫函式 `MDIGetActive` 或如下所示，找到作用中的 MDI 子視窗 `GetActiveFrame` ：

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a> CFrameWnd：： GetControlBar

呼叫 `GetControlBar` 以取得與識別碼相關聯之控制列的存取權。

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制列的 ID 號碼。

### <a name="return-value"></a>傳回值

與識別碼相關聯之控制列的指標。

### <a name="remarks"></a>備註

*NID*參數會參考傳遞給控制列之方法的唯一識別碼 `Create` 。 如需控制列的詳細資訊，請參閱標題為 [控制](../../mfc/control-bars.md)列的主題。

`GetControlBar` 即使是浮動的，也會傳回控制列，因此目前不是框架的子視窗。

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a> CFrameWnd：： GetDockState

呼叫這個成員函式，將框架視窗控制列的狀態資訊儲存在 `CDockState` 物件中。

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>參數

*state*<br/>
包含傳回時框架視窗控制列的目前狀態。

### <a name="remarks"></a>備註

然後，您可以使用或，將的內容寫入 `CDockState` 至儲存體 `CDockState::SaveState` `Serialize` 。 如果您稍後想要將控制列還原至先前的狀態，請使用或載入 `CDockState::LoadState` 狀態 `Serialize` ，然後呼叫 `SetDockState` 以將先前的狀態套用至框架視窗的控制列。

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a> CFrameWnd：： GetMenuBarState

抓取目前 MFC 應用程式中功能表的顯示狀態。

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>傳回值

傳回值可以具有下列值：

- AFX_MBS_VISIBLE (0x01) -可以看到功能表。

- AFX_MBS_HIDDEN (0x02) -隱藏功能表。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法會在偵錯工具模式中判斷提示，並引發衍生自 [CException](../../mfc/reference/cexception-class.md) 類別的例外狀況。

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a> CFrameWnd：： GetMenuBarVisibility

指出目前 MFC 應用程式中功能表的預設狀態為隱藏或可見。

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>傳回值

這個方法會傳回下列其中一個值：

- AFX_MBV_KEEPVISIBLE (0x01) -功能表會隨時顯示，且預設不會有焦點。

- AFX_MBV_DISPLAYONFOCUS (0x02) -預設會隱藏功能表。 如果功能表已隱藏，請按 ALT 鍵以顯示功能表並為其提供焦點。 如果顯示功能表，請按 ALT 或 ESC 鍵將它隱藏。

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)  (位組合 (或) # A7-預設會隱藏功能表。 如果功能表已隱藏，請按 F10 鍵以顯示功能表，並為其提供焦點。 如果顯示功能表，請按下 F10 鍵，將焦點切換到功能表上或關閉。 功能表會顯示，直到您按 ALT 或 ESC 鍵將它隱藏為止。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法會在偵錯工具模式中判斷提示，並引發衍生自 [CException](../../mfc/reference/cexception-class.md) 類別的例外狀況。

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a> CFrameWnd：： GetMessageBar

呼叫這個成員函式，以取得狀態列的指標。

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>傳回值

狀態列視窗的指標。

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a> CFrameWnd：： GetMessageString

覆寫此函式以提供命令識別碼的自訂字串。

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
所需訊息的資源識別碼。

*rMessage*<br/>
`CString` 要在其中放置訊息的物件。

### <a name="remarks"></a>備註

預設的實，只會從資源檔載入 *nID* 所指定的字串。 當狀態列中的訊息字串需要更新時，架構會呼叫這個函式。

## <a name="cframewndgettitle"></a><a name="gettitle"></a> CFrameWnd：： GetTitle

抓取視窗物件的標題。

```
CString GetTitle() const;
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，包含視窗物件的目前標題。

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a> CFrameWnd：： InitialUpdateFrame

`IntitialUpdateFrame`使用建立新框架之後的呼叫 `Create` 。

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>參數

*Pdoc->*<br/>
指向框架視窗相關聯的檔。 可以是 NULL。

*bMakeVisible*<br/>
若為 TRUE，表示框架應該為可見且使用中。 如果為 FALSE，則不會顯示任何子代。

### <a name="remarks"></a>備註

這會導致該框架視窗中的所有視圖都能接收其 `OnInitialUpdate` 呼叫。

此外，如果先前沒有使用中的視圖，框架視窗的主要視圖會成為作用中狀態。 主視圖是子系識別碼為 AFX_IDW_PANE_FIRST 的觀點。 最後，如果 *bMakeVisible* 為非零，則會顯示框架視窗。 如果 *bMakeVisible* 為0，框架視窗的目前焦點和可見狀態將保持不變。 使用 framework 的新檔案和檔案開啟時，不需要呼叫此函式。

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a> CFrameWnd：： InModalState

呼叫這個成員函式，以檢查框架視窗是否為強制回應或非模式。

```
BOOL InModalState() const;
```

### <a name="return-value"></a>傳回值

若為是，則為非零;否則為0。

## <a name="cframewndistracking"></a><a name="istracking"></a> CFrameWnd：： IsTracking

呼叫這個成員函式，以判斷視窗中的分隔器列是否目前正在移動中。

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>傳回值

如果分隔器作業正在進行中，則為非零;否則為0。

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a> CFrameWnd：： LoadAccelTable

呼叫以載入指定的快速鍵對應表。

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
識別加速器資源的名稱。 如果資源是以整數識別碼識別，請使用 MAKEINTRESOURCE。

### <a name="return-value"></a>傳回值

如果已成功載入快速鍵對應表，則為非零;否則為0。

### <a name="remarks"></a>備註

一次只能載入一個資料表。

當應用程式終止時，會自動釋放從資源載入的快速鍵對應表。

如果您呼叫 `LoadFrame` 來建立框架視窗，則架構會載入快速鍵對應表以及功能表和圖示資源，然後不需要後續呼叫這個成員函式。

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a> CFrameWnd：： LoadBarState

呼叫此函式可還原框架視窗所擁有之每個控制列的設定。

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
初始 (INI) 檔案中的區段名稱，或是儲存狀態資訊之 Windows 登錄中的金鑰。

### <a name="remarks"></a>備註

還原的資訊包括可見度、水準/垂直方向、銜接狀態和控制列位置。

您要還原的設定必須先寫入登錄，然後再呼叫 `LoadBarState` 。 藉由呼叫 [CWinApp：： SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)將資訊寫入登錄。 藉由呼叫 [SaveBarState](#savebarstate)將資訊寫入至 INI 檔案。

## <a name="cframewndloadframe"></a><a name="loadframe"></a> CFrameWnd：： LoadFrame

呼叫以從資源資訊動態建立框架視窗。

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
與框架視窗相關聯的共用資源識別碼。

*dwDefaultStyle*<br/>
框架的 [樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果您希望標題列自動顯示視窗中所表示的檔案名稱，請包含 FWS_ADDTOTITLE 樣式。

*pParentWnd*<br/>
框架父系的指標。

*pContext*<br/>
[CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。 這個參數可以是 Null。

### <a name="remarks"></a>備註

`CFrameWnd`以兩個步驟來建立物件。 首先，叫用用來建立物件的函式，然後 `CFrameWnd` 呼叫 `LoadFrame` ，這會載入 Windows 框架視窗和相關聯的資源，並將框架視窗附加至 `CFrameWnd` 物件。 *NIDResource*參數會指定功能表、快速鍵對應表、圖示，以及框架視窗標題的字串資源。

`Create` `LoadFrame` 當您想要指定所有框架視窗的建立參數時，請使用成員函式，而不是。

架構 `LoadFrame` 會在使用檔範本物件建立框架視窗時呼叫。

架構會使用 *pCoNtext* 引數來指定要連接到框架視窗的物件，包括任何包含的 view 物件。 當您呼叫時，可以將 *pCoNtext* 引數設定為 Null `LoadFrame` 。

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a> CFrameWnd：： m_bAutoMenuEnable

當這個資料成員已啟用時 (預設) 時，沒有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 處理常式的功能表項目會在使用者提取功能表時自動停用。

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>備註

具有 ON_COMMAND 處理常式但不會自動啟用 ON_UPDATE_COMMAND_UI 處理常式的功能表項目。

當設定此資料成員時，會自動啟用功能表項目，就像啟用工具列按鈕一樣。

> [!NOTE]
> `m_bAutoMenuEnable` 對最上層功能表項目沒有任何影響。

這個資料成員會根據目前的選取範圍簡化選擇性命令的執行，並減少寫入 ON_UPDATE_COMMAND_UI 處理常式來啟用和停用功能表項目的需求。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a> CFrameWnd：： NegotiateBorderSpace

呼叫這個成員函式，以在 OLE 就地啟用期間，在框架視窗中協調框線空間。

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>參數

*nBorderCmd*<br/>
包含下列其中一個值 `enum BorderCmd` ：

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標，該物件會指定框線的座標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是 `CFrameWnd` OLE 框線空間協商的實作為。

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a> CFrameWnd：： OnBarCheck

每次在指定的控制列上執行動作時呼叫。

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
所顯示之控制列的識別碼。

### <a name="return-value"></a>傳回值

如果控制列存在，則為非零;否則為0。

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a> CFrameWnd：： OnCoNtextHelp

處理就地專案的 SHIFT + F1 說明。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>備註

若要啟用即時線上說明，您必須加入

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

語句加入您的 `CFrameWnd` 類別訊息對應，也會加入快速鍵對應表專案（通常是 SHIFT + F1）來啟用此成員函式。

如果您的應用程式是 OLE 容器，則會 `OnContextHelp` 將包含在框架視窗物件內的所有就地專案放入說明模式中。 游標會變成箭號和問號，然後使用者可以移動滑鼠指標，然後按下滑鼠左鍵，以選取對話方塊、視窗、功能表或命令按鈕。 此成員函式會 `WinHelp` 使用游標下物件的說明內容來呼叫 Windows 函式。

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a> CFrameWnd：： OnCreateClient

在執行期間由架構呼叫 `OnCreate` 。

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*lpc*<br/>
Windows [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) 結構的指標。

*pContext*<br/>
[CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

絕不呼叫這個函式。

此函式的預設執行會 `CView` 盡可能從 *pCoNtext*中提供的資訊建立物件。

覆寫這個函式以覆寫在物件中傳遞的值， `CCreateContext` 或變更框架視窗主要工作區中控制項的建立方式。 `CCreateContext` [CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md)類別會描述您可以覆寫的成員。

> [!NOTE]
> 請勿取代在結構中傳遞的值 `CREATESTRUCT` 。 僅供參考之用。 例如，如果您想要覆寫初始視窗矩形，請覆寫 `CWnd` 成員函式 [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a> CFrameWnd：： OnHideMenuBar

當系統即將隱藏目前 MFC 應用程式中的功能表列時，會呼叫此函式。

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>備註

當系統即將隱藏功能表時，這個事件處理常式可讓您的應用程式執行自訂動作。 您無法防止功能表被隱藏，但是可以呼叫其他方法來抓取功能表樣式或狀態。

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a> CFrameWnd：： OnSetPreviewMode

呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>參數

*bPreview*<br/>
指定是否要將應用程式放在預覽列印模式中。 設定為 TRUE 會置於預覽列印中，FALSE 則會取消預覽模式。

*pState*<br/>
結構的指標 `CPrintPreviewState` 。

### <a name="remarks"></a>備註

預設的執行會停用所有標準工具列，並隱藏主功能表和主要用戶端視窗。 這會將 MDI 框架視窗變成暫存的 SDI 框架視窗。

覆寫這個成員函式，以自訂預覽列印期間隱藏和顯示控制列和其他框架視窗元件的功能。 從覆寫的版本中呼叫基類實作為。

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a> CFrameWnd：： OnShowMenuBar

當系統即將顯示目前 MFC 應用程式中的功能表列時，會呼叫此函式。

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>備註

此事件處理常式可讓您的應用程式在功能表即將顯示時執行自訂動作。 您無法防止顯示功能表，但是可以呼叫其他方法來抓取功能表樣式或狀態。

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a> CFrameWnd：： OnUpdateControlBarMenu

當相關聯的功能表更新時，由架構呼叫。

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標，代表產生 update 命令的功能表。 更新處理常式會透過 PCmdUI 呼叫物件的[Enable](../../mfc/reference/ccmdui-class.md#enable)成員函式 `CCmdUI` ，以更新使用者介面。 *pCmdUI*

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a> CFrameWnd：： RecalcLayout

當系統切換標準控制列或調整框架視窗大小時，由架構呼叫。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*bNotify*<br/>
判斷框架視窗的作用中就地專案是否會收到配置變更的通知。 若為 TRUE，則會通知專案;否則為 FALSE。

### <a name="remarks"></a>備註

此成員函式的預設執行會呼叫 `CWnd` 成員函式 `RepositionBars` ，以重新置放框架中的所有控制列以及主用戶端視窗 (通常是 `CView` 或 MDICLIENT) 。

覆寫這個成員函式，在框架視窗的版面配置變更之後，控制控制列的外觀和行為。 例如，當您開啟或關閉控制列或加入另一個控制列時呼叫它。

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a> CFrameWnd：： rectDefault

`CRect`建立視窗時，請將此靜態作為參數傳遞，以允許 Windows 選擇視窗的初始大小和位置。

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a> CFrameWnd：： SaveBarState

呼叫此函式可儲存框架視窗所擁有之每個控制列的相關資訊。

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
初始化檔案中的區段名稱，或是儲存狀態資訊之 Windows 登錄中的機碼。

### <a name="remarks"></a>備註

您可以使用 [LoadBarState](#loadbarstate)，從初始化檔讀取此資訊。 儲存的資訊包括可見度、水準/垂直方向、銜接狀態和控制列位置。

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a> CFrameWnd：： SetActivePreviewView

將指定的視圖指定為現用視圖，以進行 Rich Preview。

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>參數

*pViewNew*<br/>
要啟用之視圖的指標。

### <a name="remarks"></a>備註

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a> CFrameWnd：： SetActiveView

呼叫此成員函式以設定使用中的視圖。

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*pViewNew*<br/>
指定 [CView](../../mfc/reference/cview-class.md) 物件的指標，如果沒有使用中視圖，則為 Null。

*bNotify*<br/>
指定是否要在啟用時通知此視圖。 若為 TRUE， `OnActivateView` 則會針對新的視圖呼叫; 如果為 FALSE，則不會。

### <a name="remarks"></a>備註

當使用者將焦點變更為框架視窗內的視圖時，架構會自動呼叫此函數。 您可以明確地呼叫 `SetActiveView` ，將焦點變更為指定的視圖。

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a> CFrameWnd：： SetDockState

呼叫這個成員函式，將儲存在物件中的狀態資訊套用 `CDockState` 至框架視窗的控制列。

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>參數

*state*<br/>
將儲存的狀態套用至框架視窗的控制列。

### <a name="remarks"></a>備註

若要還原控制列的先前狀態，您可以使用或載入儲存的狀態 `CDockState::LoadState` `Serialize` ，然後使用將 `SetDockState` 它套用至框架視窗的控制列。 先前的狀態會儲存在物件中， `CDockState``GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a> CFrameWnd：： SetMenuBarState

將目前 MFC 應用程式中功能表的顯示狀態設定為 [隱藏] 或 [已顯示]。

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>參數

*nState*\
在指定是否要顯示或隱藏功能表。 *NState*參數可以有下列值：

- `AFX_MBS_VISIBLE` (0x01) -如果隱藏，則會顯示功能表，但如果顯示的話，則不會有任何作用。
- `AFX_MBS_HIDDEN` (0x02) -隱藏功能表（如果有的話）; 如果隱藏，則不會有任何作用。

### <a name="return-value"></a>傳回值

如果這個方法成功變更功能表狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果發生執行階段錯誤，這個方法會在偵錯工具模式中判斷提示，並引發衍生自 [CException](../../mfc/reference/cexception-class.md) 類別的例外狀況。

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a> CFrameWnd：： SetMenuBarVisibility

將目前 MFC 應用程式中功能表的預設行為設定為隱藏或可見。

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>參數

*nStyle*\
在指定功能表是否預設為隱藏，或是可見且具有焦點。 *NStyle*參數可以有下列值：

- `AFX_MBV_KEEPVISIBLE` (0x01) -功能表會隨時顯示，且預設不會有焦點。

- `AFX_MBV_DISPLAYONFOCUS` (0x02) -預設會隱藏功能表。 如果功能表已隱藏，請按 ALT 鍵以顯示功能表並為其提供焦點。 如果顯示功能表，請按 ALT 或 ESC 鍵以隱藏功能表。

- `AFX_MBV_DISPLAYONFOCUS` (0x02) &#124; `AFX_MBV_DISPLAYONF10` (0x04)  (位合 (或) # A7-依預設會隱藏功能表。 如果功能表已隱藏，請按 F10 鍵以顯示功能表，並為其提供焦點。 如果顯示功能表，請按下 F10 鍵，將焦點切換到功能表上或關閉。 功能表會顯示，直到您按 ALT 或 ESC 鍵將它隱藏為止。

### <a name="remarks"></a>備註

如果 *nStyle* 參數的值無效，則這個方法會在「偵測模式」中判斷提示，並在發行模式中引發 [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) 。 如果發生其他執行階段錯誤，這個方法會在「偵錯工具」模式中判斷提示，並引發衍生自 [CException](../../mfc/reference/cexception-class.md) 類別的例外狀況。

此方法會影響針對 Windows Vista 和更新版本所撰寫之應用程式中的功能表狀態。

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a> CFrameWnd：： SetMessageText

呼叫此函式，將字串放在識別碼為0的狀態列窗格中。

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要放置在狀態列上的字串。

*nID*<br/>
要放置在狀態列上之字串的字串資源識別碼。

### <a name="remarks"></a>備註

這通常是狀態列最左邊且最長的窗格。

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a> CFrameWnd：： SetProgressBarPosition

設定工作列上顯示之 Windows 7 進度列的目前位置。

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*nProgressPos*<br/>
指定要設定的位置。 它必須在設定的範圍內 `SetProgressBarRange` 。

### <a name="remarks"></a>備註

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a> CFrameWnd：： SetProgressBarRange

設定工作列上所顯示 Windows 7 進度列的範圍。

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>參數

*nRangeMin*<br/>
基本值。

*nRangeMax*<br/>
最大值。

### <a name="remarks"></a>備註

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a> CFrameWnd：： SetProgressBarState

設定工作列按鈕上顯示之進度指示器的類型和狀態。

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>參數

*tbpFlags*<br/>
控制進度按鈕目前狀態的旗標。 請只指定下列其中一個旗標，因為所有狀態都是互斥的： TBPF_NOPROGRESS、TBPF_INDETERMINATE、TBPF_NORMAL、TBPF_ERROR TBPF_PAUSED。

### <a name="remarks"></a>備註

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a> CFrameWnd：： SetTaskbarOverlayIcon

多載。 將重迭套用至工作列按鈕，以指出應用程式狀態或通知使用者。

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
指定要做為覆迭之圖示的資源識別碼。 如需詳細資料，請參閱 *hIcon* 的描述。

*lpcszDescr*<br/>
字串的指標，可針對協助工具用途提供覆迭所傳達之資訊的替代文字版本。

*hIcon*<br/>
要做為覆迭使用的圖示控制碼。 這應該是一個小圖示，以96點為單位測量16x16 圖元， (DPI) 。 如果已將覆迭圖示套用至工作列按鈕，則會取代現有的覆迭。 這個值可以是 Null。 Null 值的處理方式取決於工作列按鈕代表單一視窗或一組視窗。 當不再需要時，呼叫應用程式必須負責釋放 *hIcon* 。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE;如果作業系統版本小於 Windows 7，或如果發生錯誤，設定圖示，則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cframewndsettitle"></a><a name="settitle"></a> CFrameWnd：： SetTitle

設定視窗物件的標題。

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
字元字串的指標，其中包含 window 物件的標題。

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a> CFrameWnd：： ShowControlBar

呼叫這個成員函式，以顯示或隱藏控制列。

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>參數

*pBar*<br/>
要顯示或隱藏之控制列的指標。

*bShow*<br/>
若為 TRUE，表示要顯示控制列。 如果為 FALSE，則表示要隱藏控制列。

*bDelay*<br/>
若為 TRUE，則會顯示控制列的延遲。 如果為 FALSE，則會立即顯示控制列。

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a> CFrameWnd：： ShowOwnedWindows

呼叫這個成員函式，以顯示屬於物件下階的所有視窗 `CFrameWnd` 。

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定是否要顯示或隱藏擁有的視窗。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)
