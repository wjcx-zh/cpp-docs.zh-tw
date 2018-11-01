---
title: CToolBar 類別
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: 4faa067f95f43939d6dbd05837f961b3baa7f17f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593241"
---
# <a name="ctoolbar-class"></a>CToolBar 類別

有一列點陣圖按鈕和選擇性分隔線的控制列。

## <a name="syntax"></a>語法

```
class CToolBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|建構 `CToolBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|傳回與指定的命令識別碼的按鈕索引|
|[CToolBar::Create](#create)|建立 Windows 工具列，並將它附加至`CToolBar`物件。|
|[CToolBar::CreateEx](#createex)|會建立`CToolBar`物件具有其他樣式的內嵌`CToolBarCtrl`物件。|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|擷取識別碼、 樣式和按鈕的影像數目。|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|擷取按鈕的樣式。|
|[CToolBar::GetButtonText](#getbuttontext)|擷取會出現在按鈕的文字。|
|[CToolBar::GetItemID](#getitemid)|傳回指定索引處的分隔符號或按鈕的命令識別碼。|
|[CToolBar::GetItemRect](#getitemrect)|擷取指定索引處的項目顯示矩形。|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|允許直接存取基礎的通用控制項。|
|[CToolBar::LoadBitmap](#loadbitmap)|載入包含點陣圖按鈕影像的點陣圖。|
|[CToolBar::LoadToolBar](#loadtoolbar)|載入使用資源編輯器建立工具列資源。|
|[CToolBar::SetBitmap](#setbitmap)|設定點陣圖的影像。|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|設定識別碼、 樣式和按鈕的影像數目。|
|[CToolBar::SetButtons](#setbuttons)|設定按鈕樣式和點陣圖內的按鈕影像的索引。|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|設定按鈕的樣式。|
|[CToolBar::SetButtonText](#setbuttontext)|設定按鈕的顯示文字。|
|[CToolBar::SetHeight](#setheight)|設定工具列的高度。|
|[CToolBar::SetSizes](#setsizes)|設定按鈕和其點陣圖的大小。|

## <a name="remarks"></a>備註

按鈕可以像是按鈕、 核取方塊按鈕或選項按鈕。 `CToolBar` 物件是通常是內嵌的框架視窗物件衍生自類別成員[CFrameWnd](../../mfc/reference/cframewnd-class.md)或是[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。

[CToolBar::GetToolBarCtrl](#gettoolbarctrl)，成員函式新增到 MFC 4.0 可讓您善加利用工具列自訂和其他功能的 Windows 通用控制項的支援。 `CToolBar` 成員函式可讓您大部分的 Windows 通用控制項; 的功能不過，當您呼叫`GetToolBarCtrl`，您可以提供給您工具列更多 Windows 95/98 工具列的特性。 當您呼叫`GetToolBarCtrl`，它會傳回參考`CToolBarCtrl`物件。 請參閱[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)如需有關設計使用 Windows 通用控制項的工具列。 更多一般通用控制項的詳細資訊，請參閱[通用控制項](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

Visual c + + 為您提供兩種方法可以建立工具列。 若要建立工具列資源使用資源編輯器，請遵循下列步驟：

1. 建立工具列資源。

1. 建構 `CToolBar` 物件。

1. 呼叫[Create](#create) (或[CreateEx](#createex)) 函式來建立 Windows 工具列，並將其附加至`CToolBar`物件。

1. 呼叫[LoadToolBar](#loadtoolbar)載入工具列資源。

否則，請遵循下列步驟：

1. 建構 `CToolBar` 物件。

1. 呼叫[Create](#create) (或[CreateEx](#createex)) 函式來建立 Windows 工具列，並將其附加至`CToolBar`物件。

1. 呼叫[LoadBitmap](#loadbitmap)載入點陣圖，其中包含工具列按鈕影像。

1. 呼叫[SetButtons](#setbuttons)將按鈕樣式設定，並將每個按鈕點陣圖中的映像產生關聯。

在工具列中的所有按鈕影像是都取自一個點陣圖，它必須包含每個按鈕的一個映像。 所有映像必須是相同的大小;預設值是 16 像素寬和高 15 像素。 映像必須在點陣圖中的並排顯示。

`SetButtons`函式都會接受的控制項 Id 和陣列中指定的項目數的整數陣列的指標。 函式每個按鈕的識別碼設定為對應的項目之陣列的值，並指派每個按鈕影像索引，指定點陣圖中的按鈕的影像位置。 如果陣列元素具有 ID_SEPARATOR 值時，會不指派任何映像索引。

點陣圖中的映像的順序通常是在其中繪製的畫面上，但您可以使用的順序[SetButtonInfo](#setbuttoninfo)函式來變更影像順序和繪圖順序之間的關聯性。

在工具列中的所有按鈕都都相同的大小。 預設值為 24 x 22 個像素為單位，根據*軟體設計的 Windows 介面指導方針*。 映像與按鈕維度之間任何額外的空間用來形成影像周圍的框線。

每個按鈕都有一個映像。 各種按鈕狀態和樣式 （已按下，清單中，已停用、 關閉、 停用和不定） 會產生從該一個映像。 雖然點陣圖可以是任何色彩，您可以達到最佳的結果中黑色和灰階映像。

> [!WARNING]
> `CToolBar` 支援的上限為 16 種色彩的點陣圖。 當您將映像載入工具列編輯器時，Visual Studio 自動必要時，會將影像轉換為 16 色的點陣圖，並顯示一則警告訊息，如果已轉換的映像。 如果您將映像使用超過 16 色 （使用外部編輯器編輯映像） 時，應用程式可能會出現非預期行為。

工具列按鈕會模擬預設按鈕。 不過，工具列按鈕也可以模擬核取方塊按鈕或選項按鈕。 核取方塊按鈕有三種狀態： 已核取、 已清除，並不確定。 選項按鈕有兩個狀態： 選取和清除。

若要設定個別的按鈕或分隔符號樣式，而不指向陣列，呼叫[GetButtonStyle](#getbuttonstyle)來擷取樣式，然後呼叫[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle` 當您想要在執行階段變更按鈕的樣式時，就是最有用。

若要將指派才會出現在按鈕上的文字，請呼叫[GetButtonText](#getbuttontext)擷取的文字會出現在 [] 按鈕，然後再呼叫[SetButtonText](#setbuttontext)設定文字。

建立核取方塊按鈕、 將它指派樣式 TBBS_CHECKBOX 或使用`CCmdUI`物件的`SetCheck`ON_UPDATE_COMMAND_UI 處理常式中的成員函式。 呼叫`SetCheck`按鈕會變成核取方塊按鈕。 傳遞`SetCheck`引數 0 已核取，或 2 的未選取，1 為不定。

若要建立的選項按鈕，請呼叫[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio) ON_UPDATE_COMMAND_UI 處理常式成員函式。 傳遞`SetRadio`未核取或非零值，檢查引數為 0。 為了提供的選項群組是互斥的行為，您必須擁有群組 ON_UPDATE_COMMAND_UI 所有按鈕的處理常式。

如需有關使用`CToolBar`，請參閱文章[MFC 工具列實作](../../mfc/mfc-toolbar-implementation.md)並[技術提示 31： 控制列](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

此成員函式會傳回第一個工具列按鈕，在位置 0，啟動命令 ID 符合索引`nIDFind`。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
工具列按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

的索引 按鈕，則為-1 沒有按鈕具有指定的命令識別碼。

##  <a name="create"></a>  CToolBar::Create

此成員函式會建立 Windows 工具列 （子視窗），並將它與`CToolBar`物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
工具列的父視窗的指標。

*cheaderctrl:: Create*<br/>
工具列的樣式。 支援的其他工具列樣式如下：

- CBRS_TOP 控制列是在框架視窗的頂端。

- CBRS_BOTTOM 控制列是在框架視窗的底部。

- 父代調整大小時，不會重新定位 CBRS_NOALIGN 控制列。

- CBRS_TOOLTIPS 控制列會顯示工具提示。

- CBRS_SIZE_DYNAMIC 控制列是動態的。

- 已修正 CBRS_SIZE_FIXED 控制列。

- 浮動 CBRS_FLOATING 控制列。

- CBRS_FLYBY 狀態列會顯示按鈕的相關資訊。

- CBRS_HIDE_INPLACE 控制列不會顯示給使用者。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它也會設定為預設值的工具列高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

呼叫此函式來建立 Windows 工具列 （子視窗） 和其關聯`CToolBar`物件。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
工具列的父視窗的指標。

*dwCtrlStyle*<br/>
建立內嵌的其他樣式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)物件。 根據預設，此值設為 TBSTYLE_FLAT。 Toolbar 樣式的完整清單，請參閱 < *cheaderctrl:: Create*。

*cheaderctrl:: Create*<br/>
工具列的樣式。 請參閱[工具列控制項和按鈕樣式](/windows/desktop/Controls/toolbar-control-and-button-styles)Windows SDK 中針對適當的樣式清單。

*rcBorders*<br/>
A [CRect](../../atl-mfc-shared/reference/crect-class.md)工具列視窗框線的寬度定義的物件。 預設值，進而導致無邊界 [工具列] 視窗會將這些框線設 0,0,0,0。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它也會設定為預設值的工具列高度。

使用`CreateEx`，而不是[建立](#create)，當特定樣式必須在內嵌的工具列控制項的建立期間存在。 例如，設定*dwCtrlStyle* TBSTYLE_FLAT 至&#124;TBSTYLE_TRANSPARENT 以建立類似於 Internet Explorer 4 工具列的工具列。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

此成員函式會建構`CToolBar`物件，並設定預設大小。

```
CToolBar();
```

### <a name="remarks"></a>備註

呼叫[建立](#create)成員函式來建立 [工具列] 視窗。

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

此成員函式擷取控制項 ID、 樣式和工具列按鈕或分隔符號所指定位置的映像索引*nIndex。*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
工具列按鈕或分隔符號是擷取其資訊的索引。

*nID*<br/>
設定按鈕的命令 ID 為 UINT 參考。

*nStyle*<br/>
設定按鈕的樣式為 UINT 參考。

*iImage*<br/>
設定為按鈕的影像點陣圖內的索引為整數的參考。

### <a name="remarks"></a>備註

這些值會指派給所參考的變數*nID*， *nStyle*，並*iImage*。 映像索引是包含所有工具列按鈕的影像點陣圖內影像的位置。 第一個映像位於位置 0。

如果*nIndex*指定的分隔符號*iImage*設分隔符號寬度，單位為像素。

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

呼叫此成員函式可擷取按鈕或工具列上的分隔符號的樣式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取的工具列按鈕或分隔符號樣式的索引。

### <a name="return-value"></a>傳回值

所指定的分隔符號之按鈕的樣式*nIndex*。

### <a name="remarks"></a>備註

按鈕的樣式會決定按鈕的顯示方式，以及它如何回應使用者輸入。 請參閱[SetButtonStyle](#setbuttonstyle)的按鈕樣式的範例。

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

呼叫此成員函式，來擷取顯示在按鈕的文字。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取之文字的索引。

*rString*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，包含要擷取的文字。

### <a name="return-value"></a>傳回值

A`CString`物件，其中包含按鈕的文字。

### <a name="remarks"></a>備註

這個成員的第二種形式的函式會填滿`CString`具有字串文字物件。

##  <a name="getitemid"></a>  CToolBar::GetItemID

此成員函式會傳回所指定的分隔符號之按鈕的命令 ID *nIndex*。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
ID 是要擷取之項目的索引。

### <a name="return-value"></a>傳回值

命令 ID 的按鈕或所指定的分隔符號*nIndex*。

### <a name="remarks"></a>備註

分隔符號傳回 ID_SEPARATOR。

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

此成員函式會填滿`RECT`結構中包含的位址*lpRect*的按鈕或分隔符號所指定的座標*nIndex*。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取之項目的索引 （按鈕或分隔符號） 的矩形座標的。

*lpRect*<br/>
位址[RECT](../../mfc/reference/rect-structure1.md)結構將會包含項目的座標。

### <a name="remarks"></a>備註

座標是像素為單位，相對於工具列的左上角。

使用`GetItemRect`以取得您想要使用下拉式方塊或其他控制項取代為分隔符號的座標。

### <a name="example"></a>範例

  範例，請參閱[CToolBar::SetSizes](#setsizes)。

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

此成員函式允許直接存取基礎的通用控制項。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>傳回值

對 `CToolBarCtrl` 物件的參考。

### <a name="remarks"></a>備註

使用`GetToolBarCtrl`利用 Windows 工具列通用控制項的功能，並利用支援[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供工具列自訂。

如需有關如何使用通用控制項的詳細資訊，請參閱[控制項](../../mfc/controls-mfc.md)並[通用控制項](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

呼叫此成員函式，將所指定的點陣圖`lpszResourceName`或`nIDResource`。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
要載入點陣圖的資源名稱的指標。

*nIDResource*<br/>
點陣圖的資源識別碼載入。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖應該包含一個映像，為每個工具列按鈕。 如果映像不是標準的大小 （16 像素寬、 高 15 像素），呼叫[SetSizes](#setsizes)設定按鈕大小和其映像。

> [!WARNING]
> `CToolBar` 支援的上限為 16 種色彩的點陣圖。 當您將映像載入工具列編輯器時，Visual Studio 自動必要時，會將影像轉換為 16 色的點陣圖，並顯示一則警告訊息，如果已轉換的映像。 如果您將映像使用超過 16 色 （使用外部編輯器編輯映像） 時，應用程式可能會出現非預期行為。

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

呼叫此成員函式，將所指定的工具列*lpszResourceName*或是*nIDResource*。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
[載入] 工具列的資源名稱的指標。

*nIDResource*<br/>
要載入 [資源] 工具列的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

請參閱[工具列編輯器](../../windows/toolbar-editor.md)中用於建立工具列資源的詳細資訊。

### <a name="example"></a>範例

  範例，請參閱[CToolBar::CreateEx](#createex)。

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

呼叫此成員函式，可以設定工具列的點陣圖影像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>參數

*hbmImageWell*<br/>
與工具列相關聯的點陣圖影像的控制代碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

例如，呼叫`SetBitmap`使用者採取動作的文件，變更按鈕的動作之後，變更點陣圖影像。

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

呼叫此成員函式，可以設定按鈕的命令 ID、 樣式和映像數目。

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
按鈕或分隔符號資訊為其設定的以零為起始的索引。

*nID*<br/>
設定按鈕的命令 ID 的值。

*nStyle*<br/>
將新的按鈕樣式。 支援下列的按鈕樣式：

- TBBS_BUTTON 標準按鈕 （預設值）

- TBBS_SEPARATOR 分隔符號

- TBBS_CHECKBOX 自動核取方塊按鈕

- TBBS_GROUP 標示開頭的一組按鈕

- TBBS_CHECKGROUP 標示的核取方塊按鈕群組的開頭

- TBBS_DROPDOWN 建立下拉式清單按鈕。

- TBBS_AUTOSIZE 會計算按鈕的寬度為基礎的按鈕，不在映像大小的文字。

- TBBS_NOPREFIX 按鈕的文字不會有與它相關聯的快速鍵對應前置詞。

*iImage*<br/>
按鈕的影像點陣圖內的新索引。

### <a name="remarks"></a>備註

此函式作為分隔符號，有樣式 TBBS_SEPARATOR，單位為像素中儲存的值設定分隔符號的寬度*iImage*。

> [!NOTE]
>  您也可以設定使用的按鈕狀態*nStyle*參數; 不過，因為按鈕狀態會受到[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)任何處理常式中，狀態使用設定`SetButtonInfo`將會遺失在下一步 的閒置處理。 請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)並[TN031： 控制列](../../mfc/tn031-control-bars.md)如需詳細資訊。

如需點陣圖影像和按鈕的資訊，請參閱[CToolBar](../../mfc/reference/ctoolbar-class.md)概觀並[CToolBar::LoadBitmap](#loadbitmap)。

##  <a name="setbuttons"></a>  CToolBar::SetButtons

此成員函式所對應的項目陣列的指定的值來設定每個工具列按鈕的命令 ID *lpIDArray*。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
命令識別碼的陣列指標。 它可以是 NULL，配置空的按鈕。

*nIDCount*<br/>
所指陣列中的項目數*lpIDArray*。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果陣列的項目值 ID_SEPARATOR，分隔符號被建立在對應工具列的位置。 此函式也會每個按鈕的樣式設定為 TBBS_BUTTON 和 TBBS_SEPARATOR，每個分隔符號的樣式，並將映像索引指派給每個按鈕。 映像索引指定按鈕的影像點陣圖內的位置。

您不需要負責在點陣圖中的分隔符號，因為此函式不會指派分隔符號的映像索引。 如果您的工具列有按鈕位於位置 0，1、 3 和分隔符號，以在位置 2，在您的點陣圖位置 0、 1 和 2 的映像會指派給按鈕位於位置 0、 1 和 3，分別。

如果*lpIDArray*是 NULL，此函式所指定的項目數目為分配空間*nIDCount*。 使用[SetButtonInfo](#setbuttoninfo)來設定每個項目的屬性。

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

呼叫此成員函式，來設定樣式的按鈕或分隔符號，或將按鈕分組。

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
按鈕或分隔符號設定為其資訊的索引。

*nStyle*<br/>
按鈕樣式。 支援下列的按鈕樣式：

- TBBS_BUTTON 標準按鈕 （預設值）

- TBBS_SEPARATOR 分隔符號

- TBBS_CHECKBOX 自動核取方塊按鈕

- TBBS_GROUP 標示開頭的一組按鈕

- TBBS_CHECKGROUP 標示的核取方塊按鈕群組的開頭

- TBBS_DROPDOWN 建立下拉式清單按鈕

- 按鈕的寬度會計算出的 TBBS_AUTOSIZE 根據按鈕，不是在映像的大小上的文字

- TBBS_NOPREFIX 按鈕的文字不會有與它相關聯的快速鍵對應前置詞

### <a name="remarks"></a>備註

按鈕的樣式會決定按鈕的顯示方式，以及它如何回應使用者輸入。

然後再呼叫`SetButtonStyle`，呼叫[GetButtonStyle](#getbuttonstyle)成員函式來擷取按鈕或分隔符號的樣式。

> [!NOTE]
>  您也可以設定使用的按鈕狀態*nStyle*參數; 不過，因為按鈕狀態會受到[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)任何處理常式中，狀態使用設定`SetButtonStyle`將會遺失在下一步 的閒置處理。 請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)並[TN031： 控制列](../../mfc/tn031-control-bars.md)如需詳細資訊。

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

呼叫此函式來設定按鈕的文字。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
設定為其文字的按鈕索引。

*lpszText*<br/>
指向要在按鈕上設定的文字。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CToolBar::GetToolBarCtrl](#gettoolbarctrl)。

##  <a name="setheight"></a>  CToolBar::SetHeight

此成員函式的值，單位為像素中指定設定工具列的高度*cyHeight*。

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>參數

*cyHeight*<br/>
像素為單位，工具列的高度。

### <a name="remarks"></a>備註

之後呼叫[SetSizes](#setsizes)，使用此成員函式來覆寫標準 工具列的高度。 如果高度太小，則按鈕會裁剪底部。

如果未呼叫此函式，架構會使用按鈕的大小，以判斷工具列高度。

##  <a name="setsizes"></a>  CToolBar::SetSizes

呼叫此成員函式，可以設定工具列的按鈕的大小，單位為像素中指定*sizeButton*。

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>參數

*sizeButton*<br/>
像素為單位的每個按鈕的大小。

*sizeImage*<br/>
像素為單位的每個映像大小。

### <a name="remarks"></a>備註

*SizeImage*參數必須包含大小，單位為像素的工具列點陣圖中的映像。 中的維度*sizeButton*必須足以儲存映像加上 7 個像素額外的寬度和 6 個像素額外的高度。 此函式也會設定成按鈕的工具列高度。

呼叫此成員函式只會針對未遵循的工具列*軟體設計的 Windows 介面指導方針*按鈕和映像大小的建議。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[MFC 範例 DLGCBR32](../../visual-cpp-samples.md)<br/>
[MFC 範例 DOCKTOOL](../../visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
