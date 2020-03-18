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
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421482"
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
|[CToolBar：： CToolBar](#ctoolbar)|建構 `CToolBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolBar：： CommandToIndex](#commandtoindex)|傳回具有指定命令識別碼之按鈕的索引。|
|[CToolBar：： Create](#create)|建立 Windows 工具列，並將它附加至 `CToolBar` 物件。|
|[CToolBar：： CreateEx](#createex)|建立具有內嵌 `CToolBarCtrl` 物件之其他樣式的 `CToolBar` 物件。|
|[CToolBar：： GetButtonInfo](#getbuttoninfo)|抓取按鈕的識別碼、樣式和影像編號。|
|[CToolBar：： GetButtonStyle](#getbuttonstyle)|抓取按鈕的樣式。|
|[CToolBar：： GetButtonText](#getbuttontext)|抓取將出現在按鈕上的文字。|
|[CToolBar：： GetItemID](#getitemid)|傳回指定索引處之按鈕或分隔符號的命令識別碼。|
|[CToolBar：： GetItemRect](#getitemrect)|抓取指定索引處之專案的顯示矩形。|
|[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)|允許直接存取基礎通用控制項。|
|[CToolBar：： LoadBitmap](#loadbitmap)|載入包含點陣圖按鈕影像的點陣圖。|
|[CToolBar：： LoadToolBar](#loadtoolbar)|載入使用資源編輯器所建立的工具列資源。|
|[CToolBar：： SetBitmap](#setbitmap)|設定點陣圖影像。|
|[CToolBar：： SetButtonInfo](#setbuttoninfo)|設定按鈕的識別碼、樣式和影像編號。|
|[CToolBar：： SetButtons](#setbuttons)|在點陣圖內設定按鈕樣式和按鈕影像的索引。|
|[CToolBar：： SetButtonStyle](#setbuttonstyle)|設定按鈕的樣式。|
|[CToolBar：： SetButtonText](#setbuttontext)|設定將顯示在按鈕上的文字。|
|[CToolBar：： SetHeight](#setheight)|設定工具列的高度。|
|[CToolBar：： SetSizes](#setsizes)|設定按鈕和其點陣圖的大小。|

## <a name="remarks"></a>備註

按鈕的作用就像是 [普通]、[核取方塊按鈕] 或 [選項按鈕]。 `CToolBar` 物件通常是衍生自類別[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)之框架視窗物件的內嵌成員。

[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)是 MFC 4.0 的新成員函式，可讓您充分利用 Windows 通用控制項對工具列自訂的支援，以及其他功能。 `CToolBar` 成員函式可為您提供 Windows 通用控制項的大部分功能;不過，當您呼叫 `GetToolBarCtrl`時，您可以為工具列提供更多 Windows 95/98 工具列的特性。 當您呼叫 `GetToolBarCtrl`時，它會傳回 `CToolBarCtrl` 物件的參考。 如需使用 Windows 通用控制項來設計工具列的詳細資訊，請參閱[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 。 如需有關通用控制項的一般資訊，請參閱 Windows SDK 中的[通用控制項](/windows/win32/Controls/common-controls-intro)。

[ C++視覺效果] 提供您兩種方法來建立工具列。 若要使用資源編輯器來建立工具列資源，請遵循下列步驟：

1. 建立工具列資源。

1. 建構 `CToolBar` 物件。

1. 呼叫[create](#create) （或[CreateEx](#createex)）函式來建立 Windows 工具列，並將它附加至 `CToolBar` 物件。

1. 呼叫[LoadToolBar](#loadtoolbar)以載入工具列資源。

否則，請遵循下列步驟：

1. 建構 `CToolBar` 物件。

1. 呼叫[create](#create) （或[CreateEx](#createex)）函式來建立 Windows 工具列，並將它附加至 `CToolBar` 物件。

1. 呼叫[LoadBitmap](#loadbitmap)以載入包含工具列按鈕影像的點陣圖。

1. 呼叫[SetButtons](#setbuttons)以設定按鈕樣式，並將每個按鈕與點陣圖中的影像產生關聯。

工具列中的所有按鈕影像都會取自一個點陣圖，每個按鈕都必須包含一個影像。 所有影像都必須是相同的大小;預設值為16圖元寬和15圖元高。 影像在點陣圖中必須並存。

`SetButtons` 函式會採用控制項識別碼陣列的指標，以及指定陣列中元素數目的整數。 函式會將每個按鈕的識別碼設定為數組之對應元素的值，並為每個按鈕指派影像索引，以指定按鈕影像在點陣圖中的位置。 如果陣列元素的值 ID_SEPARATOR，則不會指派任何影像索引。

點陣圖中的影像順序通常是在螢幕上繪製的順序，但是您可以使用[SetButtonInfo](#setbuttoninfo)函式來變更影像順序和繪圖順序之間的關聯性。

工具列中的所有按鈕大小都相同。 預設值為 24 x 22 圖元，符合*軟體設計的 Windows 介面方針*。 影像和按鈕維度之間的任何額外空間會用來形成影像周圍的框線。

每個按鈕都有一個影像。 各種按鈕狀態和樣式（已按下、向上、向下、已停用、已停用及不定）都會從該影像產生。 雖然點陣圖可以是任何色彩，但是您可以使用黑白影像的黑色和陰影來達到最佳效果。

> [!WARNING]
> `CToolBar` 支援最多16個色彩的點陣圖。 當您將影像載入工具列編輯器時，Visual Studio 會自動將影像轉換成16色點陣圖（如有必要），並在影像已轉換時顯示警告訊息。 如果您使用的影像有16個以上的色彩（使用外部編輯器來編輯影像），應用程式可能會發生非預期的行為。

工具列按鈕預設會模擬按鈕。 不過，工具列按鈕也可以模仿核取方塊按鈕或選項按鈕。 核取方塊按鈕有三種狀態： [已核取]、[已清除] 和 [確定]。 選項按鈕只有兩個狀態： [已核取] 和 [已清除]。

若要設定個別的按鈕或分隔符號樣式，而不指向陣列，請呼叫[GetButtonStyle](#getbuttonstyle)來抓取樣式，然後呼叫[SetButtonStyle](#setbuttonstyle) ，而不是 `SetButtons`。 當您想要在執行時間變更按鈕的樣式時，`SetButtonStyle` 是最有用的。

若要指派文字顯示在按鈕上，請呼叫[GetButtonText](#getbuttontext)來抓取要出現在按鈕上的文字，然後呼叫[SetButtonText](#setbuttontext)來設定文字。

若要建立核取方塊按鈕，請將樣式指派 TBBS_CHECKBOX 或在 ON_UPDATE_COMMAND_UI 處理常式中使用 `CCmdUI` 物件的 `SetCheck` 成員函式。 呼叫 `SetCheck` 會將按鍵轉換成核取方塊按鈕。 傳遞 `SetCheck` 0 的引數以取消核取，1代表已檢查，或2表示不定。

若要建立選項按鈕，請從 ON_UPDATE_COMMAND_UI 處理常式呼叫[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成員函式。 傳遞 `SetRadio` 0 的引數，表示已核取或非零。 為了提供無線電群組的互斥行為，您必須擁有群組中所有按鈕的 ON_UPDATE_COMMAND_UI 處理常式。

如需使用 `CToolBar`的詳細資訊，請參閱[MFC 工具列執行](../../mfc/mfc-toolbar-implementation.md)和[技術提示31：控制](../../mfc/tn031-control-bars.md)列一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h。h

##  <a name="commandtoindex"></a>CToolBar：： CommandToIndex

此成員函式會傳回第一個工具列按鈕的索引，從位置0開始，其命令識別碼符合 `nIDFind`。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
工具列按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

按鈕的索引，如果沒有按鈕則有指定的命令 ID，則為-1。

##  <a name="create"></a>CToolBar：： Create

此成員函式會建立 Windows 工具列（子視窗），並將它與 `CToolBar` 物件產生關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指向工具列父系之視窗的指標。

*dwStyle*<br/>
工具列樣式。 支援的其他工具列樣式包括：

- CBRS_TOP 控制列位於框架視窗的頂端。

- CBRS_BOTTOM 控制列位於框架視窗的底部。

- 當父代調整大小時，不會重新置放 CBRS_NOALIGN 控制列。

- CBRS_TOOLTIPS 控制列會顯示工具提示。

- CBRS_SIZE_DYNAMIC 控制列是動態的。

- 已修正 CBRS_SIZE_FIXED 控制列。

- CBRS_FLOATING 控制條是浮動的。

- CBRS_FLYBY 狀態列會顯示按鈕的相關資訊。

- 不會對使用者顯示 CBRS_HIDE_INPLACE 控制列。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它也會將工具列高度設定為預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>CToolBar：： CreateEx

呼叫此函式以建立 Windows 工具列（子視窗），並將它與 `CToolBar` 物件建立關聯。

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
指向工具列父系之視窗的指標。

*dwCtrlStyle*<br/>
建立內嵌[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)物件的其他樣式。 根據預設，這個值會設定為 TBSTYLE_FLAT。 如需工具列樣式的完整清單，請參閱*dwStyle*。

*dwStyle*<br/>
工具列樣式。 如需適當樣式的清單，請參閱 Windows SDK 中的[工具列控制項和按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)。

*rcBorders*<br/>
定義工具列視窗框線寬度的[CRect](../../atl-mfc-shared/reference/crect-class.md)物件。 根據預設，這些框線會設定為0，0，0，0，因此會產生沒有框線的工具列視窗。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它也會將工具列高度設定為預設值。

在建立內嵌工具列控制項時，如果需要有特定樣式，請使用 `CreateEx`，而不是[建立](#create)。 例如，將*dwCtrlStyle*設定為 TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT 來建立類似 Internet Explorer 4 工具列的工具列。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>CToolBar：： CToolBar

此成員函式會建立 `CToolBar` 物件，並設定預設大小。

```
CToolBar();
```

### <a name="remarks"></a>備註

呼叫[create](#create)成員函式來建立工具列視窗。

##  <a name="getbuttoninfo"></a>CToolBar：： GetButtonInfo

此成員函式會在 NIndex 所指定的位置上，抓取工具列按鈕或分隔符號的控制項 ID、樣式和影像索引 *。*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其資訊之工具列按鈕或分隔符號的索引。

*nID*<br/>
UINT 的參考，設定為按鈕的命令 ID。

*nStyle*<br/>
參考設定為按鈕樣式的 UINT。

*iImage*<br/>
參考設定為點陣圖內按鈕影像索引的整數。

### <a name="remarks"></a>備註

這些值會指派給*nID*、 *nStyle*和*iImage*所參考的變數。 影像索引是點陣圖內影像的位置，其中包含所有工具列按鈕的影像。 第一個影像位於位置0。

如果*nIndex*指定分隔符號， *iImage*會設定為分隔符號寬度（以圖元為單位）。

##  <a name="getbuttonstyle"></a>CToolBar：： GetButtonStyle

呼叫這個成員函式，以取得工具列上的按鈕或分隔符號的樣式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取的工具列按鈕或分隔符號樣式的索引。

### <a name="return-value"></a>傳回值

*NIndex*所指定之按鈕或分隔符號的樣式。

### <a name="remarks"></a>備註

按鈕的樣式會決定按鈕的顯示方式，以及它如何回應使用者輸入。 如需按鈕樣式的範例，請參閱[SetButtonStyle](#setbuttonstyle) 。

##  <a name="getbuttontext"></a>CToolBar：： GetButtonText

呼叫這個成員函式，以取出出現在按鈕上的文字。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要取出的文字索引。

*rString*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考，其中將包含要抓取的文字。

### <a name="return-value"></a>傳回值

包含按鈕文字的 `CString` 物件。

### <a name="remarks"></a>備註

此成員函式的第二種形式會以字串文字填入 `CString` 物件。

##  <a name="getitemid"></a>CToolBar：： GetItemID

此成員函式會傳回*nIndex*所指定之按鈕或分隔符號的命令識別碼。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其識別碼之專案的索引。

### <a name="return-value"></a>傳回值

*NIndex*所指定之按鈕或分隔符號的命令識別碼。

### <a name="remarks"></a>備註

分隔符號會傳回 ID_SEPARATOR。

##  <a name="getitemrect"></a>CToolBar：： GetItemRect

此成員函式會以*nIndex*所指定之按鈕或分隔符號的座標，填入*lpRect*中包含位址的 `RECT` 結構。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其矩形座標的專案（按鈕或分隔符號）索引。

*lpRect*<br/>
將包含專案座標之[RECT](/windows/win32/api/windef/ns-windef-rect)結構的位址。

### <a name="remarks"></a>備註

座標是以圖元為單位，相對於工具列的左上角。

使用 `GetItemRect` 來取得您想要以下拉式方塊或其他控制項取代之分隔符號的座標。

### <a name="example"></a>範例

  請參閱[CToolBar：： SetSizes](#setsizes)的範例。

##  <a name="gettoolbarctrl"></a>CToolBar：： GetToolBarCtrl

這個成員函式可讓您直接存取基礎通用控制項。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>傳回值

`CToolBarCtrl` 物件的參考。

### <a name="remarks"></a>備註

使用 [`GetToolBarCtrl`] 可利用 Windows 工具列通用控制項的功能，並利用 [支援[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) ] 提供的自訂工具列。

如需使用通用控制項的詳細資訊，請參閱 Windows SDK 中的文章[控制項](../../mfc/controls-mfc.md)和[通用控制項](/windows/win32/Controls/common-controls-intro)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>CToolBar：： LoadBitmap

呼叫這個成員函式以載入 `lpszResourceName` 或 `nIDResource`所指定的點陣圖。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
要載入之點陣圖的資源名稱的指標。

*nIDResource*<br/>
要載入之點陣圖的資源識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖應該包含每個工具列按鈕的一個影像。 如果影像不是標準大小（16圖元寬和15圖元高），請呼叫[SetSizes](#setsizes)來設定按鈕大小和其影像。

> [!WARNING]
> `CToolBar` 支援最多16個色彩的點陣圖。 當您將影像載入工具列編輯器時，Visual Studio 會自動將影像轉換成16色點陣圖（如有必要），並在影像已轉換時顯示警告訊息。 如果您使用的影像有16個以上的色彩（使用外部編輯器來編輯影像），應用程式可能會發生非預期的行為。

##  <a name="loadtoolbar"></a>CToolBar：： LoadToolBar

呼叫這個成員函式以載入*lpszResourceName*或*nIDResource*所指定的工具列。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
要載入之工具列的資源名稱的指標。

*nIDResource*<br/>
要載入之工具列的資源識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如需有關建立工具列資源的詳細資訊，請參閱中的[工具列編輯器](../../windows/toolbar-editor.md)。

### <a name="example"></a>範例

  請參閱[CToolBar：： CreateEx](#createex)的範例。

##  <a name="setbitmap"></a>CToolBar：： SetBitmap

呼叫這個成員函式可設定工具列的點陣圖影像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>參數

*hbmImageWell*<br/>
與工具列相關聯之點陣圖影像的控制碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

例如，在使用者對變更按鈕動作的檔採取動作之後，呼叫 `SetBitmap` 來變更點陣圖影像。

##  <a name="setbuttoninfo"></a>CToolBar：： SetButtonInfo

呼叫這個成員函式，以設定按鈕的命令識別碼、樣式和影像編號。

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其資訊的按鈕或分隔符號之以零為基底的索引。

*nID*<br/>
按鈕的命令 ID 所設定的值。

*nStyle*<br/>
新的按鈕樣式。 支援下列按鈕樣式：

- TBBS_BUTTON 標準按鍵（預設值）

- TBBS_SEPARATOR 分隔符號

- TBBS_CHECKBOX 自動核取方塊按鈕

- TBBS_GROUP 標示按鈕群組的開頭

- TBBS_CHECKGROUP 標示覆選框按鈕群組的開頭

- TBBS_DROPDOWN 會建立下拉式清單按鈕。

- TBBS_AUTOSIZE 按鈕的寬度將根據按鈕的文字來計算，而不是以影像大小為依據。

- TBBS_NOPREFIX 按鈕文字將不會有相關聯的快速鍵前置詞。

*iImage*<br/>
點陣圖內按鈕影像的新索引。

### <a name="remarks"></a>備註

針對具有樣式 TBBS_SEPARATOR 的分隔符號，此函式會將分隔符號的寬度設定為以圖元為單位，表示*iImage*中儲存的值。

> [!NOTE]
>  您也可以使用*nStyle*參數來設定按鈕狀態;不過，因為按鈕狀態是由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)處理常式所控制，所以您使用 `SetButtonInfo` 設定的任何狀態都會在下一次閒置處理期間遺失。 如需詳細資訊，請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控制](../../mfc/tn031-control-bars.md)列。

如需點陣圖影像和按鈕的詳細資訊，請參閱[CToolBar](../../mfc/reference/ctoolbar-class.md)總覽和[CToolBar：： LoadBitmap](#loadbitmap)。

##  <a name="setbuttons"></a>CToolBar：： SetButtons

此成員函式會將每個工具列按鈕的命令識別碼設定為數組*lpIDArray*之對應元素所指定的值。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
命令識別碼陣列的指標。 可以是 Null 來配置空的按鈕。

*nIDCount*<br/>
*LpIDArray*中所指向之陣列中的元素數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果陣列的元素具有 ID_SEPARATOR 的值，則會在工具列的對應位置中建立分隔符號。 此函式也會將每個按鈕的樣式設定為 TBBS_BUTTON，並將每個分隔符號的樣式設為 TBBS_SEPARATOR，並將影像索引指派給每個按鈕。 影像索引會指定按鈕影像在點陣圖中的位置。

您不需要考慮點陣圖中的分隔符號，因為此函式不會指派分隔符號的影像索引。 如果您的工具列有位置為0、1、3的按鈕，以及位於位置2的分隔符號，則點陣圖中位置0、1和2的影像會分別指派給位置為0、1和3的按鈕。

如果*lpIDArray*為 Null，則此函式會為*nIDCount*所指定的專案數配置空間。 使用[SetButtonInfo](#setbuttoninfo)來設定每個專案的屬性。

##  <a name="setbuttonstyle"></a>CToolBar：： SetButtonStyle

呼叫這個成員函式可設定按鈕或分隔符號的樣式，或群組按鈕。

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其資訊的按鈕或分隔符號的索引。

*nStyle*<br/>
按鈕樣式。 支援下列按鈕樣式：

- TBBS_BUTTON 標準按鍵（預設值）

- TBBS_SEPARATOR 分隔符號

- TBBS_CHECKBOX 自動核取方塊按鈕

- TBBS_GROUP 標示按鈕群組的開頭

- TBBS_CHECKGROUP 標示覆選框按鈕群組的開頭

- TBBS_DROPDOWN 建立下拉式清單按鈕

- TBBS_AUTOSIZE 按鈕的寬度將根據按鈕的文字來計算，而不是根據影像大小

- TBBS_NOPREFIX 按鈕文字不會有相關聯的快速鍵前置詞

### <a name="remarks"></a>備註

按鈕的樣式會決定按鈕的顯示方式，以及它如何回應使用者輸入。

在呼叫 `SetButtonStyle`之前，請先呼叫[GetButtonStyle](#getbuttonstyle)成員函式來抓取按鈕或分隔符號樣式。

> [!NOTE]
>  您也可以使用*nStyle*參數來設定按鈕狀態;不過，因為按鈕狀態是由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)處理常式所控制，所以您使用 `SetButtonStyle` 設定的任何狀態都會在下一次閒置處理期間遺失。 如需詳細資訊，請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控制](../../mfc/tn031-control-bars.md)列。

##  <a name="setbuttontext"></a>CToolBar：： SetButtonText

呼叫此函式可設定按鈕上的文字。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其文字之按鈕的索引。

*lpszText*<br/>
指向要在按鈕上設定的文字。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)的範例。

##  <a name="setheight"></a>CToolBar：： SetHeight

此成員函式會將工具列的高度設定為*cyHeight*中指定的值（以圖元為單位）。

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>參數

*cyHeight*<br/>
工具列的高度（以圖元為單位）。

### <a name="remarks"></a>備註

呼叫[SetSizes](#setsizes)之後，請使用這個成員函式來覆寫標準工具列高度。 如果高度太小，則按鈕會在底部裁剪。

如果未呼叫此函式，架構會使用按鈕的大小來決定工具列高度。

##  <a name="setsizes"></a>CToolBar：： SetSizes

呼叫這個成員函式，將工具列的按鈕設定為*sizeButton*中所指定的大小（以圖元為單位）。

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>參數

*sizeButton*<br/>
每個按鈕的大小（以圖元為單位）。

*sizeImage*<br/>
每個影像的大小（以圖元為單位）。

### <a name="remarks"></a>備註

*SizeImage*參數必須包含工具列點陣圖中影像的大小（以圖元為單位）。 *SizeButton*中的維度必須足以容納影像加上7圖元額外的寬度和6圖元額外的高度。 此函式也會設定工具列高度以符合按鈕。

僅針對不遵循*Windows 介面方針*的工具列，針對按鈕和影像大小提供軟體設計建議，呼叫此成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
