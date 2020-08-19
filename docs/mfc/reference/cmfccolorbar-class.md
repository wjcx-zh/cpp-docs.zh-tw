---
title: CMFCColorBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: ca28f8a07938e787fcf2d91d714c9dc82092194f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561033"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 類別

`CMFCColorBar`類別代表可在檔或應用程式中選取色彩的停駐控制列。

## <a name="syntax"></a>語法

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorBar：： CMFCColorBar](#cmfccolorbar)|建構 `CMFCColorBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorBar：： CoNtextToSize](#contexttosize)|計算在色軸控制項上包含按鈕所需的垂直和水準邊界，然後調整這些按鈕的位置。|
|[CMFCColorBar：： CreateControl](#createcontrol)|建立色軸控制項視窗、將其附加至 `CMFCColorBar` 物件，並調整控制項的大小以包含指定的色彩調色板。|
|[CMFCColorBar：： Create](#create)|建立色軸控制項視窗，並將其附加至 `CMFCColorBar` 物件。|
|[CMFCColorBar：： EnableAutomaticButton](#enableautomaticbutton)|顯示或隱藏 [自動] 按鈕。|
|[CMFCColorBar：： EnableOtherButton](#enableotherbutton)|啟用或停用對話方塊的顯示，讓使用者選取更多色彩。|
|[CMFCColorBar：： GetColor](#getcolor)|抓取目前選取的色彩。|
|[CMFCColorBar：： GetCommandID](#getcommandid)|抓取目前的色軸控制項的命令 ID。|
|[CMFCColorBar：： GetHighlightedColor](#gethighlightedcolor)|抓取表示色彩按鈕具有焦點的色彩;也就是，按鈕是 *熱*的。|
|[CMFCColorBar：： GetHorzMargin](#gethorzmargin)|抓取水準邊界，也就是左右色儲存格與用戶端區域界限之間的空間。|
|[CMFCColorBar：： GetVertMargin](#getvertmargin)|抓取垂直邊界，也就是頂端或底部色彩儲存格與用戶端區域界限之間的間距。|
|[CMFCColorBar：： IsTearOff](#istearoff)|指出目前的色軸是否為可停駐。|
|[CMFCColorBar：： SetColor](#setcolor)|設定目前選取的色彩。|
|[CMFCColorBar：： SetColorName](#setcolorname)|為指定的色彩設定新的名稱。|
|[CMFCColorBar：： SetCommandID](#setcommandid)|為色軸控制項設定新的命令識別碼。|
|[CMFCColorBar：： SetDocumentColors](#setdocumentcolors)|設定目前檔中使用的色彩清單。|
|[CMFCColorBar：： SetHorzMargin](#sethorzmargin)|設定水準邊界，也就是左右色儲存格與用戶端區域界限之間的空間。|
|[CMFCColorBar：： SetVertMargin](#setvertmargin)|設定垂直邊界，也就是頂端或底部色彩儲存格與用戶端區域界限之間的間距。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorBar：： AdjustLocations](#adjustlocations)|調整色軸控制項上色彩按鈕的位置。|
|[CMFCColorBar：： AllowChangeTextLabels](#allowchangetextlabels)|指出色彩按鈕的文字標籤是否可以變更。|
|[CMFCColorBar：： AllowShowOnList](#allowshowonlist)|指出在自訂程式中，是否可以在工具列清單中顯示色軸控制項物件。|
|[CMFCColorBar：： CalcSize](#calcsize)|由架構在版面配置計算過程中呼叫。|
|[CMFCColorBar：： CreatePalette](#createpalette)|使用指定之色彩陣列中的色彩，初始化調色板。|
|[CMFCColorBar：： GetColorGridSize](#getcolorgridsize)|計算色軸控制項方格中的資料列和資料行數目。|
|[CMFCColorBar：： GetExtraHeight](#getextraheight)|計算目前的色軸需要的額外高度，以顯示其他使用者介面元素，例如 [ **其他** ] 按鈕、檔色彩等等。|
|[CMFCColorBar：： InitColors](#initcolors)|使用指定之調色板或系統預設調色板中的色彩，初始化色彩的陣列。|
|[CMFCColorBar：： OnKey](#onkey)|當使用者按下鍵盤按鈕時，由架構呼叫。|
|[CMFCColorBar：： OnSendCommand](#onsendcommand)|由架構呼叫以關閉快顯視窗控制項的階層架構。|
|[CMFCColorBar：： OnUpdateCmdUI](#onupdatecmdui)|由架構呼叫，以在顯示專案之前啟用或停用色軸控制項的使用者介面專案。|
|[CMFCColorBar：： OpenColorDialog](#opencolordialog)|開啟 [色彩] 對話方塊。|
|[CMFCColorBar：： Rebuild](#rebuild)|完全重繪色軸控制項。|
|[CMFCColorBar：： SelectPalette](#selectpalette)|將指定之裝置內容的邏輯調色板，設定為目前色軸控制項之父按鈕的選擇區。|
|[CMFCColorBar：： SetPropList](#setproplist)|將 `m_pWndPropList` 受保護的資料成員設定為屬性方格控制項的指定指標。|
|[CMFCColorBar：： ShowCommandMessageString](#showcommandmessagestring)|要求擁有色軸控制項的框架視窗，以更新狀態列中的訊息行。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|`m_bInternal`|決定是否處理滑鼠事件的布林值欄位。 一般而言，當這個欄位為 TRUE 且自訂模式為 FALSE 時，就會處理滑鼠事件。|
|`m_bIsEnabled`|指出是否已啟用控制項的布林值。|
|`m_bIsTearOff`|指出色軸控制項是否支援銜接的布林值。|
|`m_BoxSize`|[CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定色軸格線中的儲存格大小。|
|`m_bShowDocColorsWhenDocked`|指出是否要在停駐色軸時顯示檔色彩的布林值。 如需詳細資訊，請參閱 [CMFCColorBar：： SetDocumentColors](#setdocumentcolors)。|
|`m_bStdColorDlg`|指出是否要顯示標準系統色彩對話方塊或 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 對話方塊的布林值。 如需詳細資訊，請參閱 [CMFCColorBar：： EnableOtherButton](#enableotherbutton)。|
|`m_ColorAutomatic`|儲存目前自動色彩的 [COLORREF](/windows/win32/gdi/colorref) 。 如需詳細資訊，請參閱 [CMFCColorBar：： EnableOtherButton](#enableotherbutton)。|
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md)物件，其會將一組 RGB 色彩與其名稱產生關聯。|
|`m_colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray](../../mfc/reference/carray-class.md) ，其中包含顏色列控制項中顯示的色彩。|
|`m_ColorSelected`|[COLORREF](/windows/win32/gdi/colorref)值，這個值是使用者目前從色彩列控制項選取的色彩。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList](../../mfc/reference/clist-class.md) ，其中包含檔中目前使用的色彩。|
|`m_nCommandID`|不帶正負號的整數，這是色彩按鈕的命令識別碼。|
|`m_nHorzMargin`|整數，這是色彩方格中色彩按鈕之間的水準邊界。|
|`m_nHorzOffset`|整數，這是色彩按鈕中間的水準位移。 如果按鈕除了色彩之外，還會顯示文字或影像，此值是很重要的。|
|`m_nNumColumns`|整數，這個整數是色彩列控制項格線中的資料行數目。|
|`m_nNumColumnsVert`|整數，這是色彩垂直方向方格中的資料行數目。|
|`m_nNumRowsHorz`|整數，這是水準方向格線中的資料行數目。|
|`m_nRowHeight`|整數，這是色彩格線中某一資料列的高度。|
|`m_nVertMargin`|整數，這是色彩方格中色彩按鈕之間的垂直邊界。|
|`m_nVertOffset`|整數，這是色彩按鈕中間的垂直位移。 如果按鈕除了色彩之外，還會顯示文字或影像，此值是很重要的。|
|`m_Palette`|色軸控制項中所使用之色彩的 [CPalette](../../mfc/reference/cpalette-class.md) 。|
|`m_pParentBtn`|[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)物件的指標，該物件為目前按鈕的父系。 如果 [色彩] 按鈕位於工具列控制項階層中，或位於 [色彩] 屬性方格控制項中，則這個值是很重要的。|
|`m_pParentRibbonBtn`|位於功能區上之 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) 物件的指標，也是目前按鈕的父按鈕。 如果 [色彩] 按鈕位於工具列控制項階層中，或位於 [色彩] 屬性方格控制項中，則這個值是很重要的。|
|`m_pWndPropList`|[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)物件的指標。|
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，這是顯示在 [**自動**] 按鈕上的文字。 如需詳細資訊，請參閱 [CMFCColorBar：： EnableAutomaticButton](#enableautomaticbutton)。|
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，這是顯示在 [檔色彩] 按鈕上的文字。 如需詳細資訊，請參閱 [CMFCColorBar：： SetDocumentColors](#setdocumentcolors)。|
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，也就是顯示在*另*一個按鈕上的文字。 如需詳細資訊，請參閱 [CMFCColorBar：： EnableOtherButton](#enableotherbutton)。|

## <a name="remarks"></a>備註

通常，您不會直接建立 `CMFCColorBar` 物件。 相反地， [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md) (用於功能表和工具列) 或 [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md) 會建立 `CMFCColorBar` 物件。

`CMFCColorBar`類別提供下列功能：

- 自動調整檔色彩的清單。

- 儲存和還原其狀態，以及檔狀態。

- 管理 [自動] 按鈕。

- 使用 [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md) 控制項來選取自訂色彩。

- 支援「卸載」狀態 (如果是使用 [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)) 建立的狀態。

若要將 `CMFCColorBar` 功能併入您的應用程式：

1. 建立一般的功能表按鈕，並為其指派識別碼，例如 ID_CHAR_COLOR。

1. 在您的框架視窗類別中，覆寫[CFrameWndEx：： OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法，並透過呼叫[CMFCToolBar：： ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)) ，將一般功能表按鈕取代為[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)物件 (。

1. 設定所有樣式，並 `CMFCColorBar` 在建立 [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md) 期間啟用或停用物件的功能。 物件會在 `CMFCColorMenuButton` `CMFCColorBar` 架構呼叫方法之後動態建立物件 `CreatePopupMenu` 。

當使用者按一下色軸控制項按鈕時，架構會使用 `ON_COMMAND` 宏來通知色 bar 控制項的父系。 在宏中，[命令 ID] 參數是您在步驟1中指派給 [色階] 控制項按鈕的值 (在此範例) 中 ID_CHAR_COLOR。 如需詳細資訊，請參閱 [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)、 [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)、 [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)、 [CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)和 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md) 類別。

## <a name="example"></a>範例

下列範例示範如何使用類別中的各種方法來設定色軸 `CMFCColorBar` 。 這些方法會設定水準和垂直邊界、啟用 [其他] 按鈕、建立色軸控制項視窗，以及設定目前選取的色彩。 這個範例是 [新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxcolorbar。h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a> CMFCColorBar：： AdjustLocations

調整色軸控制項上色彩按鈕的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>備註

在 WM_SIZE 訊息處理期間，架構會呼叫這個方法。

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a> CMFCColorBar：： AllowChangeTextLabels

指出色彩按鈕的文字標籤是否可以變更。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>傳回值

一律為 FALSE。

### <a name="remarks"></a>備註

根據預設，這個方法一律會傳回 FALSE，表示無法修改文字標籤。 覆寫此方法以啟用修改文字標籤。

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a> CMFCColorBar：： AllowShowOnList

指出在自訂程式中，是否可以在工具列清單中顯示色軸控制項物件。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>傳回值

一律為 TRUE。

### <a name="remarks"></a>備註

根據預設，這個方法一律會傳回 TRUE，這表示在自訂程式中，架構可以顯示色軸控制項。 覆寫這個方法以執行不同的行為。

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a> CMFCColorBar：： CalcSize

由架構在版面配置計算過程中呼叫。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>參數

*bVertDock*<br/>
在TRUE 表示要垂直停駐色軸控制項;FALSE 指定水準停駐色軸控制項。

### <a name="return-value"></a>傳回值

色軸控制項中色彩按鈕的陣列大小。

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a> CMFCColorBar：： CMFCColorBar

建構 `CMFCColorBar` 物件。

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>參數

*顏色*<br/>
在架構在色軸控制項上顯示的色彩陣列。

*color*<br/>
在初始選取的色彩。

*lpszAutoColor*<br/>
在 *自動* (預設) 色彩按鈕的文字標籤，或 Null。

[自動] 按鈕的標準標籤是 [ **自動**]。

*lpszOtherColor*<br/>
在 *另* 一個按鈕的文字標籤，其會顯示更多色彩選擇或 Null。

另一個按鈕的標準標籤是 [其他 **色彩**] .。。

*lpszDocColors*<br/>
在檔色彩按鈕的文字標籤。 檔色彩調色板會列出檔目前使用的所有色彩。

*lstDocColors*<br/>
在檔目前使用的色彩清單。

*nColumns*<br/>
在色彩陣列的資料行數目。

*nRowsDockHorz*<br/>
在當色軸水準停駐時，此資料列的數目。

*nColDockVert*<br/>
在當色軸垂直停駐時，所擁有的資料行數目。

*colorAutomatic*<br/>
在當您按一下 [自動] 按鈕時，架構所套用的預設色彩。

*nCommandID*<br/>
在色 bar 控制項命令識別碼。

*pParentBtn*<br/>
在父按鈕的指標。

*src*<br/>
在 `CMFCColorBar` 要複製到新物件中的現有物件 `CMFCColorBar` 。

*uiCommandID*<br/>
在命令識別碼。

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a> CMFCColorBar：： CoNtextToSize

計算在色軸控制項上包含按鈕所需的垂直和水準邊界，並調整這些按鈕的位置。

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>參數

*bSquareButtons*\
在TRUE 表示在色軸控制項上的按鈕形狀為正方形;否則為 FALSE。 預設值為 TRUE。

*bCenterButtons*\
在TRUE 表示要指定彩色橫條圖控制項按鈕的臉部內容是在中央;否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfccolorbarcreate"></a><a name="create"></a> CMFCColorBar：： Create

建立色軸控制項視窗，並將其附加至 `CMFCColorBar` 物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
在父視窗的指標。

*dwStyle*<br/>
在 (或 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)) 的位元組合。

*nID*<br/>
在命令識別碼。

*pPalette*<br/>
在色彩調色板的指標。 預設值是 NULL。

*nColumns*<br/>
在色軸控制項中的資料行數目。 預設值是 0。

*nRowsDockHorz*<br/>
在水準停駐時，色軸控制項中的資料列數目。 預設值是 0。

*nColDockVert*<br/>
在當垂直停駐時，色軸控制項中的資料行數目。 預設值是 0。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

若要建立 `CMFCColorBar` 物件，請呼叫類別的函式，然後再呼叫這個方法。 `Create`方法會建立 Windows 控制項並初始化色彩清單。

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a> CMFCColorBar：： CreateControl

建立色軸控制項視窗、將它附加至 `CMFCColorBar` 物件，然後調整控制項視窗的大小，以包含指定的色彩調色板。

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
在父視窗的指標。 不能是 NULL。

*矩形*<br/>
在指定要繪製色軸控制項之位置的周框。

*nID*<br/>
在控制項識別碼。

*nColumns*<br/>
在色軸控制項中的理想資料行數目。 這個方法會將該數位修改為符合指定的色彩調色板。 預設值為-1，表示未指定此參數。

*pPalette*<br/>
在色彩之調色板的指標，或為 Null。 如果這個參數是 Null，這個方法會計算色軸控制項的大小，就像指定了20個色彩一樣。 預設值是 NULL。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用 *rect*、 *nColumns*和 *pPalette* 參數來計算色軸控制項中適當的數目或資料列和資料行，然後呼叫 [CMFCColorBar：： Create](#create) 方法。

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a> CMFCColorBar：： CreatePalette

使用指定之色彩陣列中的色彩，初始化調色板。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>參數

*arColors*\
在色彩的陣列。

*調色板*\
在色彩的調色板。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorBar：： EnableAutomaticButton

顯示或隱藏 [自動] 按鈕。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在 *自動* (預設) 色彩按鈕的文字標籤，或 Null。

[自動] 按鈕的標準標籤是 [ **自動**]。

*colorAutomatic*<br/>
在當您按一下 [自動] 按鈕時，架構所套用的預設色彩。

*bEnable*<br/>
在TRUE 表示啟用 [自動] 按鈕;FALSE 表示停用 [自動] 按鈕。 預設值為 TRUE。

### <a name="remarks"></a>備註

如果 *lpszLabel* 參數為 Null 或 *BENABLE* 參數為 FALSE，則會刪除 [自動] 按鈕的文字標籤。

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorBar：： EnableOtherButton

啟用或停用對話方塊的顯示，讓使用者選取更多色彩。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在 *另* 一個按鈕的文字標籤，其會顯示更多色彩選擇或 Null。

此按鈕的標準標籤是**更多的色彩 ...**

*bAltColorDlg*<br/>
在TRUE 表示顯示 [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ] 對話方塊;FALSE 表示顯示 [標準 [CColorDialog](../../mfc/reference/ccolordialog-class.md) ] 對話方塊。 預設值為 TRUE。

*bEnable*<br/>
在TRUE 表示啟用按鈕;FALSE 表示停用按鈕。 預設值為 TRUE。

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a> CMFCColorBar：： GetColor

抓取目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

目前選取的色彩。

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a> CMFCColorBar：： GetColorGridSize

計算色軸控制項方格中的資料列和資料行數目。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>參數

*bVertDock*\
在TRUE 表示執行垂直停駐色軸控制項的計算;否則，請針對水準停駐的控制項執行計算。

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其 `cx` 元件包含資料行數目，以及其 `cy` 元件包含資料列數目的資料行數目。

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a> CMFCColorBar：： GetCommandID

抓取目前的色軸控制項的命令 ID。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>傳回值

命令識別碼。

### <a name="remarks"></a>備註

當使用者選取新的色彩時，架構會傳送 WM_COMMAND 訊息中的命令識別碼，以通知物件的父系 `CMFCColorBar` 。

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a> CMFCColorBar：： GetExtraHeight

計算目前的色軸需要的額外高度，以顯示其他使用者介面元素，例如 **其他** 按鈕或檔色彩。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>參數

*nNumColumns*\
在如果色軸控制項包含檔色彩，則顯示在檔色彩方格中的資料行數目。 否則，就不會使用這個值。

### <a name="return-value"></a>傳回值

需要的計算額外高度。

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a> CMFCColorBar：： GetHighlightedColor

抓取表示色彩按鈕具有焦點的色彩;也就是，按鈕是 *熱*的。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a> CMFCColorBar：： GetHorzMargin

抓取水準邊界，也就是左右色儲存格與用戶端區域界限之間的空間。

```
int GetHorzMargin();
```

### <a name="return-value"></a>傳回值

水準邊界。

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a> CMFCColorBar：： GetVertMargin

抓取垂直邊界，也就是頂端或底部色彩儲存格與用戶端區域界限之間的間距。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>傳回值

垂直邊界。

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a> CMFCColorBar：： InitColors

使用指定之調色板中的色彩，或使用系統預設的調色板，初始化色彩的陣列。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>參數

*pPalette*\
在調色板物件的指標，或為 Null。 如果這個參數是 Null，這個方法會使用作業系統的預設調色板。

*arColors*\
在色彩的陣列。

### <a name="return-value"></a>傳回值

色彩陣列中的元素數目。

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a> CMFCColorBar：： IsTearOff

指出目前的色軸是否為可停駐。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>傳回值

如果目前的色軸控制項是可停駐的，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果色軸控制項是可停駐的，則可能會從控制列中損毀，並停駐在另一個位置。

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a> CMFCColorBar：： OnKey

當使用者按下鍵盤按鈕時，由架構呼叫。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>參數

*nChar*<br/>
在使用者所按下之金鑰的虛擬金鑰碼。

### <a name="return-value"></a>傳回值

如果這個方法會處理指定的索引鍵，則為 TRUE;否則為 FALSE。

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a> CMFCColorBar：： OnSendCommand

由架構呼叫以關閉彈出控制項的階層。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

*pButton*\
在位於工具列上之控制項的指標。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCColorBar：： OnUpdateCmdUI

由架構呼叫，以在顯示專案之前啟用或停用色軸控制項的使用者介面專案。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

*pTarget*<br/>
在視窗的指標，其中包含要更新的使用者介面專案。

*bDisableIfNoHndler*<br/>
在TRUE 表示如果訊息對應中未定義任何處理程式，則停用使用者介面專案。否則為 FALSE。

### <a name="remarks"></a>備註

當應用程式的使用者按一下使用者介面專案時，專案必須知道它應該顯示為 [已啟用] 或 [已停用]。 命令訊息的目標是藉由執行 ON_UPDATE_COMMAND_UI 的命令處理常式來提供這項資訊。 您可以使用這個方法來協助處理命令。 如需詳細資訊，請參閱 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a> CMFCColorBar：： OpenColorDialog

開啟 [色彩] 對話方塊。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>參數

*colorDefault*<br/>
在開啟 [色彩] 對話方塊時，預設選取的色彩。

*colorRes*<br/>
擴展使用者選取的色彩。

### <a name="return-value"></a>傳回值

如果使用者選取了色彩，則為 TRUE;如果使用者取消 [色彩] 對話方塊，則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a> CMFCColorBar：： Rebuild

完全重繪色軸控制項。

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a> CMFCColorBar：： SelectPalette

將指定之裝置內容的邏輯調色板，設定為目前色軸控制項之父按鈕的選擇區。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>參數

*Pdc*\
在目前色軸控制項之父按鈕的裝置內容指標。

### <a name="return-value"></a>傳回值

由目前的色軸控制項之父按鈕的調色板所取代之調色板的指標。

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a> CMFCColorBar：： SetColor

設定目前選取的色彩。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在RGB 色彩值。

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a> CMFCColorBar：： SetColorName

為指定的色彩設定新的名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*color*<br/>
在色彩的 RGB 值。

*strName*<br/>
在指定之色彩的新名稱。

### <a name="remarks"></a>備註

這個方法會變更應用程式中所有物件的指定色彩名稱 `CMFCColorBar` 。

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a> CMFCColorBar：： SetCommandID

為色軸控制項設定新的命令識別碼。

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>參數

*nCommandID*<br/>
在命令識別碼。

### <a name="remarks"></a>備註

呼叫這個方法來修改色軸控制項的命令識別碼，並通知控制項的父視窗該識別碼已變更。

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorBar：： SetDocumentColors

設定目前檔中使用的色彩清單。

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>參數

*lpszCaption*<br/>
在當色軸控制項未停駐時所顯示的標題。

*lstDocColors*<br/>
在用來取代目前檔色彩的色彩清單。

*bShowWhenDocked*<br/>
在TRUE 表示在停駐色軸控制項時顯示檔色彩;否則為 FALSE。 預設值為 FALSE。

### <a name="remarks"></a>備註

*檔色彩* 是檔中目前使用的色彩。 架構會自動維護檔色彩的清單，但是您可以使用這個方法來修改清單。

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a> CMFCColorBar：： SetHorzMargin

設定水準邊界，也就是左邊或右邊的色彩儲存格與用戶端區域界限之間的空間。

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>參數

*nHorzMargin*<br/>
在水準邊界（以圖元為單位）。

### <a name="remarks"></a>備註

根據預設， [CMFCColorBar：： CMFCColorBar](#cmfccolorbar) 函式會將水準邊界設定為4圖元。

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a> CMFCColorBar：： SetPropList

將 `m_pWndPropList` 受保護的資料成員設定為屬性方格控制項的指定指標。

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>參數

*pWndList*\
在屬性方格控制項物件的指標。

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a> CMFCColorBar：： SetVertMargin

設定垂直邊界，也就是頂端或底部色彩儲存格與用戶端區域界限之間的間距。

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>參數

*nVertMargin*<br/>
在垂直邊界（以圖元為單位）。

### <a name="remarks"></a>備註

根據預設， [CMFCColorBar：： CMFCColorBar](#cmfccolorbar) 函式會將垂直邊界設定為4圖元。

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a> CMFCColorBar：： ShowCommandMessageString

要求擁有色軸控制項的框架視窗，以更新狀態列中的訊息行。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>參數

*uiCmdId*<br/>
在命令識別碼。  (忽略此參數。 ) 

### <a name="remarks"></a>備註

這個方法會將 WM_SETMESSAGESTRING 訊息傳送給 color bar 控制項的擁有者。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
