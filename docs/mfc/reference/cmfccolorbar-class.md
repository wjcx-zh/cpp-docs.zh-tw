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
ms.openlocfilehash: 58fddeef9cb0afe930af84b05e6a87871f729da4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752567"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 類別

類`CMFCColorBar`表示可選擇文檔或應用程式中的顏色的停靠控制欄。

## <a name="syntax"></a>語法

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorBar:CMFCColorBar](#cmfccolorbar)|建構 `CMFCColorBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorbar:上下文大小](#contexttosize)|計算包含顏色條控制元件上的按鈕所需的垂直和水平邊距,然後調整這些按鈕的位置。|
|[CMFCColorBar:建立控制](#createcontrol)|創建顏色列控制項視窗,將其附加到`CMFCColorBar`物件,並調整控制件的大小以包含指定的調色板。|
|[CMFCColorBar:建立](#create)|創建顏色條控制項視窗並將其附加到`CMFCColorBar`物件。|
|[CMFCColorBar:開啟自動按鈕](#enableautomaticbutton)|顯示或隱藏自動按鈕。|
|[CMFCColorBar:啟用其他按鈕](#enableotherbutton)|啟用或禁用允許使用者選擇更多顏色的對話框的顯示。|
|[CMFCColorBar:取得顏色](#getcolor)|檢索當前選擇的顏色。|
|[CMFCColorBar:取得命令ID](#getcommandid)|檢索目前顏色列控件的命令 ID。|
|[CMFCColorBar:取得突出顯示的顏色](#gethighlightedcolor)|檢索表示顏色按鈕具有焦點的顏色;也就是說,按鈕是*熱*的。|
|[CMFCColorBar:取得霍茲邊緣](#gethorzmargin)|檢索水平邊距,即左或右顏色單元格和工作區邊界之間的空間。|
|[CMFCColorBar:取得 VertMargin](#getvertmargin)|檢索垂直邊距,即頂部或底部顏色單元格和工作區邊界之間的空間。|
|[CMFCColorBar:IsTearoff](#istearoff)|指示當前顏色條是否可停靠。|
|[CMFCColor 列:設定顏色](#setcolor)|設置當前選擇的顏色。|
|[CMFC 顏色列:設定顏色名稱](#setcolorname)|為指定顏色設置新名稱。|
|[CMFCColorBar:setCommandID](#setcommandid)|為顏色條控制項設定新的命令 ID。|
|[CMFCColor 列:設定文件顏色](#setdocumentcolors)|設定目前文件中使用的顏色清單。|
|[CMFCColorBar:SetHorz邊緣](#sethorzmargin)|設置水平邊距,即左側或右側顏色單元格和工作區邊界之間的空間。|
|[CMFC 顏色列:設定Vert邊緣](#setvertmargin)|設置垂直邊距,即頂部或底部顏色單元格和工作區邊界之間的空間。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorBar:調整位置](#adjustlocations)|調整顏色條控制項上顏色按鈕的位置。|
|[CMFCColor 列:允許變更文字標籤](#allowchangetextlabels)|指示顏色按鈕的文本標籤是否可以更改。|
|[CMFCColorbar:允許顯示清單](#allowshowonlist)|指示在自定義過程中,顏色條控制件物件是否可以顯示在工具列清單中。|
|[CMFCColorBar:鈣化](#calcsize)|框架在布局計算過程中調用。|
|[CMFCColorBar:建立調色板](#createpalette)|使用指定顏色陣列中的顏色初始化調色板。|
|[CMFCColorBar:取得顏色格格大小](#getcolorgridsize)|計算顏色條控制元件網格中的行數和欄數。|
|[CMFCColorBar:取得額外高度](#getextraheight)|計算目前的顏色列顯示其他使用者介面元素(如 **'其他**'按鈕、文件顏色等)所需的額外高度。|
|[CMFCColorbar::以顏色](#initcolors)|使用指定調色板中的顏色或系統預設調色板中的顏色初始化顏色陣列。|
|[CMFCColorbar::打開鑰匙](#onkey)|當使用者按下鍵盤按鈕時,框架調用。|
|[CMFCColorbar:開啟傳送指令](#onsendcommand)|由框架調用以關閉彈出控制件的層次結構。|
|[CMFCColorBar:關於更新CmdUI](#onupdatecmdui)|框架呼叫以在顯示專案之前啟用或禁用顏色條控制項的使用者介面項。|
|[CMFCColorBar::打開顏色對話](#opencolordialog)|打開顏色對話方塊。|
|[CMFCColorBar:重建](#rebuild)|完全重繪色條控件。|
|[CMFCColor 列:選擇調色盤](#selectpalette)|將指定設備上下文的邏輯調色板設置為當前顏色欄控件的父按鈕的調色板。|
|[CMFCColor 列:設定Proplist](#setproplist)|將`m_pWndPropList`受保護的資料成員設置到指向屬性網格控制項的指定指標。|
|[CMFCColorBar::顯示命令訊息字串](#showcommandmessagestring)|請求擁有顏色列控件的幀視窗更新狀態列中的消息行。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|`m_bInternal`|確定是否處理滑鼠事件的布林欄位。 通常,當此欄位為 TRUE 且自訂模式為 FALSE 時,將處理滑鼠事件。|
|`m_bIsEnabled`|指示控件是否已啟用的布爾。|
|`m_bIsTearOff`|指示顏色條控件是否支援停靠的布爾。|
|`m_BoxSize`|指定顏色列格中儲存格大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|
|`m_bShowDocColorsWhenDocked`|一個布林,指示在顏色條停靠時是否顯示文檔顏色。 有關詳細資訊,請參閱[CMFCColor 欄:設定文件顏色](#setdocumentcolors)。|
|`m_bStdColorDlg`|指示是顯示標準系統顏色對話框還是[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話方塊的布林。 有關詳細資訊,請參閱[CMFCColorBar:啟用其他按鈕](#enableotherbutton)。|
|`m_ColorAutomatic`|儲存目前自動顏色的[COLORREF。](/windows/win32/gdi/colorref) 有關詳細資訊,請參閱[CMFCColorBar:啟用其他按鈕](#enableotherbutton)。|
|`m_ColorNames`|將一組 RGB 顏色與其名稱關聯到的[CMap](../../mfc/reference/cmap-class.md)物件。|
|`m_colors`|包含顏色列控制元件中顯示的顏色的[COLORREF](/windows/win32/gdi/colorref)值的[CArray。](../../mfc/reference/carray-class.md)|
|`m_ColorSelected`|[COLORREF](/windows/win32/gdi/colorref)值,是使用者當前從色條控制項中選擇的顏色。|
|`m_lstDocColors`|包含文件中目前使用的顏色的[COLORREF](/windows/win32/gdi/colorref)值的[CList。](../../mfc/reference/clist-class.md)|
|`m_nCommandID`|一個未簽名的整數,它是顏色按鈕的命令 ID。|
|`m_nHorzMargin`|一個整數,它是顏色網格中顏色按鈕之間的水平邊距。|
|`m_nHorzOffset`|一個整數,它是顏色按鈕中心的水準偏移。 如果按鈕除了顯示顏色外,還顯示文本或圖像,則此值很重要。|
|`m_nNumColumns`|一個整數,它是顏色列中控制顏色網格中的列數。|
|`m_nNumColumnsVert`|一個整數,它是垂直方向的顏色網格中的列數。|
|`m_nNumRowsHorz`|一個整數,它是水準方向顏色網格中的列數。|
|`m_nRowHeight`|一個整數,它是顏色網格中一行顏色按鈕的高度。|
|`m_nVertMargin`|一個整數,它是顏色網格中顏色按鈕之間的垂直邊距。|
|`m_nVertOffset`|一個整數,它是顏色按鈕中心的垂直偏移。 如果按鈕除了顯示顏色外,還顯示文本或圖像,則此值很重要。|
|`m_Palette`|顏色列控制項中使用的顏色的[CPalette。](../../mfc/reference/cpalette-class.md)|
|`m_pParentBtn`|指向當前按鈕的父級[的 CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)物件的指標。 如果顏色按鈕位於工具列控制元件的層次結構中或位於顏色屬性網格控制項中,則此值非常重要。|
|`m_pParentRibbonBtn`|指向功能區上的[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)物件的指標,該物件是當前按鈕的父按鈕。 如果顏色按鈕位於工具列控制元件的層次結構中或位於顏色屬性網格控制項中,則此值非常重要。|
|`m_pWndPropList`|指向[CMFC 屬性網格Ctrl](../../mfc/reference/cmfcpropertygridctrl-class.md)物件的指標。|
|`m_strAutoColor`|["CString",](../../atl-mfc-shared/reference/cstringt-class.md)是 **"自動"** 按鈕上顯示的文字。 關於詳細資訊,請參閱[CMFCColorBar:開啟自動按鈕](#enableautomaticbutton)。|
|`m_strDocColors`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md)是顯示在文件顏色按鈕上的文字。 有關詳細資訊,請參閱[CMFCColor 欄:設定文件顏色](#setdocumentcolors)。|
|`m_strOtherColor`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md)是*顯示在另一個*按鈕上的文字。 有關詳細資訊,請參閱[CMFCColorBar:啟用其他按鈕](#enableotherbutton)。|

## <a name="remarks"></a>備註

通常,您不會直接創建`CMFCColorBar`物件。 相反[,CMFCColorMenuButton 類](../../mfc/reference/cmfccolormenubutton-class.md)(用於功能表和工具列)或[CMFCColorButton 類](../../mfc/reference/cmfccolorbutton-class.md)將創建`CMFCColorBar`該物件。

該`CMFCColorBar`類別提供以下功能:

- 自動調整文件顏色的清單。

- 保存和恢復其狀態以及文件狀態。

- 管理"自動"按鈕。

- 使用[CMFCColorPickerCtrl 類](../../mfc/reference/cmfccolorpickerctrl-class.md)控制項選擇自訂顏色。

- 支援"撕掉"狀態(如果使用[CMFCColorMenuButton 類](../../mfc/reference/cmfccolormenubutton-class.md)創建)。

要將`CMFCColorBar`功能合併到應用程式中,

1. 創建常規功能表按鈕並為其分配 ID,例如ID_CHAR_COLOR。

1. 在框架視窗類中,重寫[CFrameWndEx::onShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法,並將常規功能表按鈕取代為[CMFCColorMenuButton 類](../../mfc/reference/cmfccolormenubutton-class.md)物件(透過呼叫[CMFCToolBar::替換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。

1. 在[CMFCColorMenuButton 類](../../mfc/reference/cmfccolormenubutton-class.md)`CMFCColorBar`建立期間設定 所有樣式並啟用或禁用物件的功能。 對`CMFCColorMenuButton`象 在框架`CMFCColorBar``CreatePopupMenu`調用 方法後動態創建物件。

當用戶按一下顏色條控制件按鈕時,框架將`ON_COMMAND`使用宏通知顏色條控制的父級。 在巨集中,命令 ID 參數是分配給步驟 1 中 color 欄控制按鈕的值(ID_CHAR_COLOR在此範例中)。 有關詳細資訊,請參閱[CMFCColorMenuButton 類](../../mfc/reference/cmfccolormenubutton-class.md)[、CMFCColorButton 類](../../mfc/reference/cmfccolorbutton-class.md)[、CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)類別[、CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)和[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCColorBar`類中的各種方法配置顏色條。 這些方法設置水準和垂直邊距,啟用另一個按鈕,創建顏色條控制視窗,並設置當前選擇的顏色。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar:調整位置

調整顏色條控制項上顏色按鈕的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>備註

在消息處理期間,框架會調用此方法WM_SIZE消息處理。

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColor 列:允許變更文字標籤

指示顏色按鈕的文本標籤是否可以更改。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>傳回值

一律為 FALSE。

### <a name="remarks"></a>備註

默認情況下,此方法始終返回 FALSE,這意味著無法修改文本標籤。 重寫此方法以啟用修改文本標籤。

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorbar:允許顯示清單

指示在自定義過程中,顏色條控制件物件是否可以顯示在工具列清單中。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>傳回值

一律為 TRUE。

### <a name="remarks"></a>備註

預設情況下,此方法始終返回 TRUE,這意味著框架可以在自定義過程中顯示色條控件。 重寫此方法以實現其他行為。

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar:鈣化

框架在布局計算過程中調用。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>參數

*bVertDock*<br/>
[在]TRUE 指定顏色條控件垂直停靠;FALSE 以指定顏色條控制項水準停靠。

### <a name="return-value"></a>傳回值

顏色列控制項中顏色按鈕陣列大小。

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar:CMFCColorBar

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
[在]框架顯示在顏色列控制元件上的顏色陣列。

*顏色*<br/>
[在]最初選擇的顏色。

*lpsz自動顏色*<br/>
[在]*自動*(預設)顏色按鈕或 NULL 的文字標籤。

自動按鈕的標準標籤是 **「自動**」。。

*lpszOther顏色*<br/>
[在]*另*一個按鈕的文字標籤,顯示更多顏色選項,或 NULL。

另一個按鈕的標準標籤是 **"更多顏色..."**

*lpszDocColors*<br/>
[在]文件顏色按鈕的文字標籤。 文件顏色調色板列出文件目前使用的所有顏色。

*lstDocColors*<br/>
[在]文件目前使用的顏色清單。

*nColumns*<br/>
[在]顏色陣列的欄數。

*n 羅索多克霍爾茲*<br/>
[在]顏色欄水準停靠時的行數。

*n科爾多克弗特*<br/>
[在]顏色列垂直停靠時的列數。

*顏色 自動*<br/>
[在]按下自動按鈕時框架適用的預設顏色。

*nCommandID*<br/>
[在]顏色條控制命令 ID。

*p 家長Btn*<br/>
[在]指向父按鈕的指標。

*src*<br/>
[在]要複製到`CMFCColorBar`新`CMFCColorBar`物件的現有物件。

*uiCommandID*<br/>
[在]命令識別碼。

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorbar:上下文大小

計算包含顏色條控制元件上的按鈕所需的垂直和水平邊距,並調整這些按鈕的位置。

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*b 方形按鈕*|[在]TRUE 指定顏色條控制程式上的按鈕形狀為正方形;否則,FALSE。 預設值為 TRUE。|
|*b中心按鈕*|[在]TRUE 指定顏色條控制按鈕正面上的內容居中;否則,FALSE。 預設值為 TRUE。|

### <a name="remarks"></a>備註

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar:建立

創建顏色條控制項視窗並將其附加到`CMFCColorBar`物件。

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

*pparentwnd*<br/>
[在]指向父視窗的指標。

*dwStyle*<br/>
[在][視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的位組合 (OR)。

*nID*<br/>
[在]命令識別碼。

*pPalette*<br/>
[在]指向顏色調色板的指標。 預設值是 NULL。

*nColumns*<br/>
[在]顏色列控制項中的欄數。 預設值是 0。

*n 羅索多克霍爾茲*<br/>
[在]顏色列控件中水準停靠的行數。 預設值是 0。

*n科爾多克弗特*<br/>
[在]顏色條控制項中垂直停靠的欄數。 預設值是 0。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

要構造物件`CMFCColorBar`,請調用類構造函數,然後調用此方法。 該方法`Create`創建 Windows 控制件並初始化顏色清單。

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar:建立控制

建立顏色列控制元件視窗,將其附加到`CMFCColorBar`物件,並調整控制件視窗的大小以包含指定的調色板。

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
[在]指向父視窗的指標。 不能是 NULL。

*矩形*<br/>
[在]指定繪製顏色條控制件的位置的邊界矩形。

*nID*<br/>
[在]控件識別碼。

*nColumns*<br/>
[在]顏色條控件中理想的列數。 此方法修改該數位以適合指定的顏色調色板。 預設值為 -1,這意味著未指定此參數。

*pPalette*<br/>
[在]指向顏色調色板的指標,或 NULL。 如果此參數為 NULL,則此方法計算顏色條控制件的大小,就像指定了 20 種顏色一樣。 預設值是 NULL。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

此方法使用*rect、nColumns*和*pPalette*參數計算顏色列控制項中的適當數位或行和列,然後調用[CMFCColorBar::create](#create)方法。 *nColumns*

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar:建立調色板

使用指定顏色陣列中的顏色初始化調色板。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*阿爾顏色*|[在]顏色陣列。|
|*調色盤 (palette)*|[在]顏色的調色板。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar:開啟自動按鈕

顯示或隱藏自動按鈕。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]*自動*(預設)顏色按鈕或 NULL 的文字標籤。

自動按鈕的標準標籤是 **「自動**」。。

*顏色 自動*<br/>
[在]按下自動按鈕時框架適用的預設顏色。

*b 啟用*<br/>
[在]TRUE 啟用自動按鈕;FALSE 以關閉自動按鈕。 預設值為 TRUE。

### <a name="remarks"></a>備註

如果*lpszLabel*參數為 NULL 或*bEnable*參數為 FALSE,則自動按鈕的文本標籤將被刪除。

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar:啟用其他按鈕

啟用或禁用允許使用者選擇更多顏色的對話框的顯示。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]*另*一個按鈕的文字標籤,顯示更多顏色選項,或 NULL。

這個按鈕的標準標籤是**更多顏色...**

*巴爾特·博拉爾德格*<br/>
[在]TRUE 顯示[CMFCColor對話框](../../mfc/reference/cmfccolordialog-class.md);FALSE 以顯示標準[CColorDialog](../../mfc/reference/ccolordialog-class.md)對話框。 預設值為 TRUE。

*b 啟用*<br/>
[在]TRUE 啟用按鈕;FALSE 以禁用按鈕。 預設值為 TRUE。

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar:取得顏色

檢索當前選擇的顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

當前選擇的顏色。

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar:取得顏色格格大小

計算顏色條控制元件網格中的行數和欄數。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*bVertDock*|[在]TRUE 以執行垂直停靠的色條控制項的計算;否則,對水準停靠控件執行計算。|

### <a name="return-value"></a>傳回值

其`cx`元件包含列數及其`cy`元件包含列數的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar:取得命令ID

檢索目前顏色列控件的命令 ID。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>傳回值

命令識別碼。

### <a name="remarks"></a>備註

當使用者選擇新顏色時,框架將發送WM_COMMAND消息中的命令 ID`CMFCColorBar`以通知 物件的父級。

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar:取得額外高度

計算目前的顏色列顯示其他使用者介面元素(如 **'其他**'按鈕或文件顏色)所需的額外高度。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*nNumColumns*|[在]如果顏色條控制檔包含文件顏色,則要在文件顏色網格中顯示的欄數。 否則,不使用此值。|

### <a name="return-value"></a>傳回值

所需的計算額外高度。

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar:取得突出顯示的顏色

檢索表示顏色按鈕具有焦點的顏色;也就是說,按鈕是*熱*的。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar:取得霍茲邊緣

檢索水平邊距,即左或右顏色單元格和工作區邊界之間的空間。

```
int GetHorzMargin();
```

### <a name="return-value"></a>傳回值

水平邊距。

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar:取得 VertMargin

檢索垂直邊距,即頂部或底部顏色單元格和工作區邊界之間的空間。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>傳回值

垂直邊距。

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorbar::以顏色

使用指定調色板中的顏色或系統預設調色板初始化顏色陣列。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pPalette*|[在]指向調色板物件的指標,或 NULL。 如果此參數為 NULL,則此方法使用作業系統的預設調色板。|
|*阿爾顏色*|[在]顏色陣列。|

### <a name="return-value"></a>傳回值

顏色陣列中的元素數。

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar:IsTearoff

指示當前顏色條是否可停靠。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>傳回值

如果當前顏色條控件可停靠,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果顏色條控件可停靠,則可以將其從控制欄上撕下並停靠在另一個位置。

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorbar::打開鑰匙

當使用者按下鍵盤按鈕時,框架調用。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>參數

*n查爾*<br/>
[在]使用者按下的密鑰的虛擬金鑰代碼。

### <a name="return-value"></a>傳回值

如果此方法處理指定的密鑰,則為 TRUE;如果此方法處理指定的密鑰,則為 TRUE。否則,FALSE。

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorbar:開啟傳送指令

由框架調用以關閉彈出視窗控制件的層次結構。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pButton*|[在]指向駐留在工具列上的控件的指標。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar:關於更新CmdUI

框架呼叫以在顯示專案之前啟用或禁用顏色條控制項的使用者介面項。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

*p 目標*<br/>
[在]指向包含要更新的用戶介面項的視窗的指標。

*b 關閉IfNoHndler*<br/>
[在]如果消息映射中未定義處理程式,則為禁用使用者介面項;如果消息映射中未定義任何處理程式,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

當應用程式的用戶按一下使用者介面項時,該項必須知道該項應顯示為已啟用還是禁用。 命令消息的目標通過實現ON_UPDATE_COMMAND_UI命令處理程式來提供此資訊。 使用此方法可幫助處理該命令。 有關詳細資訊,請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::打開顏色對話

打開顏色對話方塊。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>參數

*顏色 預設*<br/>
[在]預設情況下,顏色對話框打開時選擇的顏色。

*顏色 Res*<br/>
[出]使用者選擇的顏色。

### <a name="return-value"></a>傳回值

如果用戶選擇了顏色,則為 TRUE;如果用戶選擇了顏色。如果使用者取消了顏色對話框,則FALSE。

### <a name="remarks"></a>備註

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar:重建

完全重繪色條控件。

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColor 列:選擇調色盤

將指定設備上下文的邏輯調色板設置為當前顏色欄控件的父按鈕的調色板。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pDC*|[在]指向當前顏色列控件的父按鈕的設備上下文。|

### <a name="return-value"></a>傳回值

指標指向由當前顏色條控制件的父按鈕的調色板替換的調色板。

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColor 列:設定顏色

設置當前選擇的顏色。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]RGB 顏色值。

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFC 顏色列:設定顏色名稱

為指定顏色設置新名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]顏色的 RGB 值。

*strName*<br/>
[在]指定顏色的新名稱。

### <a name="remarks"></a>備註

此方法更改應用程式中所有`CMFCColorBar`物件中指定顏色的名稱。

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar:setCommandID

為顏色條控制項設定新的命令 ID。

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>參數

*nCommandID*<br/>
[在]命令識別碼。

### <a name="remarks"></a>備註

呼叫此方法以修改顏色條控制項的命令 ID,並通知控制件的父視窗 ID 已更改。

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColor 列:設定文件顏色

設定目前文件中使用的顏色清單。

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>參數

*lpszCaption*<br/>
[在]顏色條控制項未停靠時顯示的標題。

*lstDocColors*<br/>
[在]取代目前的文件顏色的顏色清單。

*B 顯示已載*<br/>
[在]TRUE 顯示顏色條控件停靠時的文檔顏色;否則,FALSE。 預設值為 FALSE。

### <a name="remarks"></a>備註

*文件顏色*是文件中目前使用的顏色。 框架會自動維護文檔顏色的清單,但您可以使用此方法修改清單。

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar:SetHorz邊緣

設置水平邊距,即左側或右側顏色單元格與工作區邊界之間的空間。

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>參數

*nHorzMargin*<br/>
[在]水平邊距,以像素為單位。

### <a name="remarks"></a>備註

預設情況下[,CMFCColorBar:CMFCColorBar](#cmfccolorbar)建構函數將水平邊距設置為 4 圖元。

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColor 列:設定Proplist

將`m_pWndPropList`受保護的資料成員設置到指向屬性網格控制項的指定指標。

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pwndlist*|[在]指向屬性網格控制物件的指標。|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFC 顏色列:設定Vert邊緣

設置垂直邊距,即頂部或底部顏色單元格和工作區邊界之間的空間。

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>參數

*nVertMargin*<br/>
[在]垂直邊距,以像素為單位。

### <a name="remarks"></a>備註

預設情況下[,CMFCColorBar:CMFCColorBar](#cmfccolorbar)建構函數將垂直邊距設置為 4 圖元。

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::顯示命令訊息字串

請求擁有顏色列控件的幀視窗更新狀態列中的消息行。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>參數

*烏伊CmDId*<br/>
[在]命令識別碼。 (此參數將被忽略。

### <a name="remarks"></a>備註

此方法將WM_SETMESSAGESTRING消息發送到顏色欄控件的擁有者。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
