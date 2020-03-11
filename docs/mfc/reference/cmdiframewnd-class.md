---
title: CMDIFrameWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: 20d74030cdc90ed2e1a7809c121967e74db21b4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866553"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 類別

提供 Windows 多重文件介面 (MDI) 框架視窗的功能，以及管理視窗的成員。

## <a name="syntax"></a>語法

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMDIFrameWnd：： CMDIFrameWnd](#cmdiframewnd)|建構 `CMDIFrameWnd`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDIFrameWnd：： CreateClient](#createclient)|建立此 `CMDIFrameWnd`的 Windows MDICLIENT 視窗。 由 `CWnd`的 `OnCreate` 成員函式呼叫。|
|[CMDIFrameWnd：： CreateNewChild](#createnewchild)|建立新的子視窗。|
|[CMDIFrameWnd：： GetWindowMenuPopup](#getwindowmenupopup)|傳回視窗快顯功能表。|
|[CMDIFrameWnd：： MDIActivate](#mdiactivate)|啟用不同的 MDI 子視窗。|
|[CMDIFrameWnd：： MDICascade](#mdicascade)|以串聯格式排列所有子視窗。|
|[CMDIFrameWnd：： MDIGetActive](#mdigetactive)|抓取目前作用中的 MDI 子視窗，以及指出子系是否最大化的旗標。|
|[CMDIFrameWnd：： MDIIconArrange](#mdiiconarrange)|排列所有最小化的檔子視窗。|
|[CMDIFrameWnd：： MDIMaximize](#mdimaximize)|將 MDI 子視窗最大化。|
|[CMDIFrameWnd：： MDINext](#mdinext)|在目前作用中的子視窗後方啟動子視窗，並將目前作用中的子視窗放在其他所有子視窗後面。|
|[CMDIFrameWnd：： MDIPrev](#mdiprev)|啟動上一個子視窗，並將目前作用中的子視窗立即放在其後方。|
|[CMDIFrameWnd：： MDIRestore](#mdirestore)|從最大化或最小化的大小還原 MDI 子視窗。|
|[CMDIFrameWnd：： MDISetMenu](#mdisetmenu)|取代 MDI 框架視窗、視窗快顯功能表或兩者的功能表。|
|[CMDIFrameWnd：： MDITile](#mditile)|以磚式格式排列所有子視窗。|

## <a name="remarks"></a>備註

若要為您的應用程式建立有用的 MDI 框架視窗，請從 `CMDIFrameWnd`衍生一個類別。 將成員變數加入至衍生類別，以儲存應用程式特定的資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

您可以藉由呼叫 `CFrameWnd`的[Create](../../mfc/reference/cframewnd-class.md#create)或[LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)成員函式來建立 MDI 框架視窗。

在您呼叫 `Create` 或 `LoadFrame`之前，您必須使用C++ **new**運算子，在堆積上建立框架視窗物件。 在呼叫 `Create` 您也可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式來註冊視窗類別，以設定框架的圖示和類別樣式。

使用 `Create` 成員函式，將框架的建立參數當做直接引數傳遞。

`LoadFrame` 所需的引數數目比 `Create`少，而是從資源中抓取大部分的預設值，包括框架的標題、圖示、快速鍵對應表和功能表。 若要 `LoadFrame`存取，所有這些資源都必須具有相同的資源識別碼（例如，IDR_MAINFRAME）。

雖然 `MDIFrameWnd` 衍生自 `CFrameWnd`，但衍生自 `CMDIFrameWnd` 的框架視窗類別不需要以 `DECLARE_DYNCREATE`宣告。

`CMDIFrameWnd` 類別從 `CFrameWnd`繼承大部分的預設實值。 如需這些功能的詳細清單，請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別描述。 `CMDIFrameWnd` 類別具有下列其他功能：

- MDI 框架視窗會管理 MDICLIENT 視窗，並將它與控制列重新置放在一起。 MDI 用戶端視窗是 MDI 子框架視窗的直接父系。 `CMDIFrameWnd` 上指定的 WS_HSCROLL 和 WS_VSCROLL 視窗樣式會套用至 MDI 用戶端視窗，而不是主框架視窗，讓使用者可以滾動 MDI 工作區（例如，在 Windows 程式管理員中）。

- 當沒有作用中的 MDI 子視窗時，MDI 框架視窗會擁有預設功能表，做為功能表列。 當有作用中的 MDI 子系時，mdi 框架視窗的功能表列會自動取代為 MDI 子視窗功能表。

- MDI 框架視窗會與目前的 MDI 子視窗搭配運作（如果有的話）。 比方說，在 MDI 框架視窗之前，命令訊息會委派給目前作用中的 MDI 子系。

- MDI 框架視窗具有下列標準 [視窗] 功能表命令的預設處理常式：

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- MDI 框架視窗也有 ID_WINDOW_NEW 的執行，它會在目前的檔上建立新的框架和視圖。 應用程式可以覆寫這些預設的命令執行，以自訂 MDI 視窗處理。

請勿使用C++ **delete**運算子來摧毀框架視窗。 請改用 `CWnd::DestroyWindow`。 `PostNcDestroy` 的 `CFrameWnd` 實作為終結視窗時C++ ，將會刪除物件。 當使用者關閉框架視窗時，預設 `OnClose` 處理常式會呼叫 `DestroyWindow`。

如需 `CMDIFrameWnd`的詳細資訊，請參閱[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cmdiframewnd"></a>CMDIFrameWnd：： CMDIFrameWnd

建構 `CMDIFrameWnd` 物件。

```
CMDIFrameWnd();
```

### <a name="remarks"></a>備註

呼叫 `Create` 或 `LoadFrame` 成員函式，以建立可見的 MDI 框架視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>CMDIFrameWnd：： CreateClient

建立用來管理 `CMDIChildWnd` 物件的 MDI 用戶端視窗。

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>參數

*lpCreateStruct*<br/>
[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)結構的長指標。

*pWindowMenu*<br/>
視窗快顯功能表的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果您直接覆寫 `OnCreate` 成員函式，則應呼叫這個成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>CMDIFrameWnd：： CreateNewChild

建立新的子視窗。

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>參數

*pClass*<br/>
要建立之子視窗的執行時間類別。

*U00a0 n 資源*<br/>
與子視窗相關聯之共用資源的識別碼。

*hMenu*<br/>
子視窗的功能表。

*hAccel*<br/>
子視窗的快速鍵。

### <a name="remarks"></a>備註

使用此函式來建立 MDI 框架視窗的子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>CMDIFrameWnd：： GetWindowMenuPopup

呼叫這個成員函式，以取得目前快顯功能表的控制碼，名稱為 "Window" （具有 MDI 視窗管理之功能表項目的快顯功能表）。

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>參數

*hMenuBar*<br/>
目前的功能表列。

### <a name="return-value"></a>傳回值

視窗快顯功能表（如果有的話）。否則為 Null。

### <a name="remarks"></a>備註

預設的執行會尋找快顯功能表，其中包含標準的視窗功能表命令，例如 ID_WINDOW_NEW 和 ID_WINDOW_TILE_HORZ。

如果您有不使用標準功能表命令識別碼的 [視窗] 功能表，請覆寫這個成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>CMDIFrameWnd：： MDIActivate

啟用不同的 MDI 子視窗。

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>參數

*pWndActivate*<br/>
指向要啟用的 MDI 子視窗。

### <a name="remarks"></a>備註

此成員函式會將[WM_MDIACTI加值稅E](../../mfc/reference/cwnd-class.md#onmdiactivate)訊息傳送至正在啟動的子視窗，並停用子視窗。

當使用者使用滑鼠或鍵盤將焦點變更為 MDI 子視窗時，這就是所傳送的相同訊息。

> [!NOTE]
>  MDI 子視窗會在 MDI 框架視窗之外獨立啟用。 當框架變成作用中時，最後啟動的子視窗會傳送[WM_NCACTI加值稅E](../../mfc/reference/cwnd-class.md#onncactivate)訊息，以繪製活動視窗框架和標題列，但不會收到另一個 WM_MDIACTI加值稅E 訊息。

### <a name="example"></a>範例

請參閱[CMDIFrameWnd：： GetWindowMenuPopup](#getwindowmenupopup)的範例。

##  <a name="mdicascade"></a>CMDIFrameWnd：： MDICascade

以 cascade 格式排列所有 MDI 子視窗。

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定 cascade 旗標。 只能指定下列旗標： MDITILE_SKIPDISABLED，這會防止停用的 MDI 子視窗進行串聯。

### <a name="remarks"></a>備註

第一版的 `MDICascade`，沒有參數，會將所有 MDI 子視窗（包括已停用的）串聯在一起。 如果您指定*nType*參數的 MDITILE_SKIPDISABLED，第二個版本選擇性地不會串聯停用的 MDI 子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>CMDIFrameWnd：： MDIGetActive

抓取目前作用中的 MDI 子視窗，以及指出子視窗是否最大化的旗標。

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>參數

*pbMaximized*<br/>
BOOL 傳回值的指標。 如果視窗最大化，則設定為 TRUE;否則為 FALSE。

### <a name="return-value"></a>傳回值

現用 MDI 子視窗的指標。

### <a name="example"></a>範例

請參閱[CMDIChildWnd：： MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)的範例。

##  <a name="mdiiconarrange"></a>CMDIFrameWnd：： MDIIconArrange

排列所有最小化的檔子視窗。

```
void MDIIconArrange();
```

### <a name="remarks"></a>備註

它不會影響未最小化的子視窗。

### <a name="example"></a>範例

請參閱[CMDIFrameWnd：： MDICascade](#mdicascade)的範例。

##  <a name="mdimaximize"></a>CMDIFrameWnd：： MDIMaximize

最大化指定的 MDI 子視窗。

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向要最大化的視窗。

### <a name="remarks"></a>備註

當子視窗最大化時，Windows 會將其調整大小，使其工作區填滿用戶端視窗。 Windows 會將子視窗的 [控制] 功能表放在框架的功能表列中，讓使用者可以還原或關閉子視窗。 它也會將子視窗的標題加入框架視窗標題。

如果在目前作用中的 MDI 子視窗最大化時啟動另一個 MDI 子視窗，Windows 會還原目前作用中的子系，並將新啟動的子視窗最大化。

### <a name="example"></a>範例

請參閱[CMDIChildWnd：： MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)的範例。

##  <a name="mdinext"></a>CMDIFrameWnd：： MDINext

在目前作用中的子視窗後方啟動子視窗，並將目前作用中的子視窗放在其他所有子視窗後面。

```
void MDINext();
```

### <a name="remarks"></a>備註

如果目前作用中的 MDI 子視窗最大化，成員函式會還原目前作用中的子系，並將新啟動的子系最大化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>CMDIFrameWnd：： MDIPrev

啟動上一個子視窗，並將目前作用中的子視窗立即放在其後方。

```
void MDIPrev();
```

### <a name="remarks"></a>備註

如果目前作用中的 MDI 子視窗最大化，成員函式會還原目前作用中的子系，並將新啟動的子系最大化。

##  <a name="mdirestore"></a>CMDIFrameWnd：： MDIRestore

從最大化或最小化的大小還原 MDI 子視窗。

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向要還原的視窗。

### <a name="example"></a>範例

請參閱[CMDIChildWnd：： MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)的範例。

##  <a name="mdisetmenu"></a>CMDIFrameWnd：： MDISetMenu

取代 MDI 框架視窗、視窗快顯功能表或兩者的功能表。

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>參數

*pFrameMenu*<br/>
指定新框架視窗功能表的功能表。 如果是 Null，則不會變更功能表。

*pWindowMenu*<br/>
指定新視窗快顯功能表的功能表。 如果是 Null，則不會變更功能表。

### <a name="return-value"></a>傳回值

此訊息所取代之框架視窗功能表的指標。 該指標可能是暫時性的，因此不應該儲存供日後使用。

### <a name="remarks"></a>備註

呼叫 `MDISetMenu`之後，應用程式必須呼叫 `CWnd` 的[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成員函式，以更新功能表列。

如果此呼叫取代視窗快顯功能表，則會從上一個視窗功能表中移除 MDI 子視窗功能表項目，並將其新增至新的視窗快顯功能表。

如果 MDI 子視窗最大化，而此呼叫取代了 MDI 框架視窗功能表，則會從上一個框架視窗功能表移除 [控制] 功能表和 [還原控制項]，並將其新增至 [新增] 功能表。

如果您使用架構來管理 MDI 子視窗，請勿呼叫這個成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>CMDIFrameWnd：： MDITile

以磚式格式排列所有子視窗。

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定並排旗標。 這個參數可以是下列任何一個旗標：

- MDITILE_HORIZONTAL 磚的 MDI 子視窗，讓一個視窗出現在另一個視窗上方。

- MDITILE_SKIPDISABLED 防止停用 MDI 子視窗的磚。

- MDITILE_VERTICAL 磚的 MDI 子視窗，讓一個視窗出現在另一個視窗旁。

### <a name="remarks"></a>備註

第一版的 `MDITile`，不含參數，會在 Windows 3.1 版和更新版本底下以垂直方式磚出視窗。 第二個版本會根據*nType*參數的值，以垂直或水準方式磚視窗。

### <a name="example"></a>範例

請參閱[CMDIFrameWnd：： MDICascade](#mdicascade)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)
