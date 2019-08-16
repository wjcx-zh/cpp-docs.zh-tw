---
title: CMFCOutlookBarPane 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505156"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 類別

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

衍生自[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)的控制項, 可以插入 Outlook Bar ( [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 功能區窗格包含一欄大型按鈕。 如果按鈕清單比窗格還要大，使用者可以上下捲動清單。 當使用者將 Outlook 功能區窗格從 Outlook 功能區卸離時，這個窗格可以在主框架視窗中停駐或浮動。

## <a name="syntax"></a>語法

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|預設建構函式。|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|將按鈕新增至 [Outlook 工作列] 窗格。|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|決定窗格是否可以停駐于另一個窗格或框架視窗。 (覆寫[CBasePane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|
|`CMFCOutlookBarPane::CanBeRestored`|判斷系統是否可以在自訂之後, 將工具列還原成其原始狀態。 (覆寫[CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|釋放 [Outlook 工具列] 窗格中的影像所使用的資源。|
|[CMFCOutlookBarPane::Create](#create)|建立 Outlook 橫條圖窗格。|
|`CMFCOutlookBarPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCOutlookBarPane::Dock`|由架構呼叫以停駐 Outlook 橫條窗格。 (覆寫 `CPane::Dock`。)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定 Outlook 工具列窗格上的捲動箭號是否要依頁面或按下按鈕來前移按鈕清單。|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|傳回 Outlook 橫條圖窗格的一般 (非選取) 文字色彩。|
|`CMFCOutlookBarPane::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|決定是否有針對 Outlook 工作列窗格載入的背景影像。|
|`CMFCOutlookBarPane::IsChangeState`|決定浮動窗格是否可以停駐。 (覆寫 `CPane::IsChangeState`。)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|決定當按鈕反白顯示並顯示背景影像時, 按鈕框線是否會加上陰影。|
|`CMFCOutlookBarPane::OnBeforeFloat`|當窗格即將浮動時, 由架構呼叫。 (覆寫[CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|移除具有指定命令識別碼的按鈕。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。 (覆寫[CMFCToolBar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|設定背景色彩。|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|設定背景影像。|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|將 Outlook [工具列] 窗格重設為原始的按鈕集。|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|設定 [Outlook 橫條圖] 窗格中按鈕周圍使用的填補圖元數。|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|設定 Outlook 橫條圖窗格中一般和反白顯示文字的色彩。|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|設定 Outlook 工具列窗格的透明色彩。|
|`CMFCOutlookBarPane::SmartUpdate`|在內部用來更新 Outlook 橫條。 (覆寫 `CMFCToolBar::SmartUpdate`。)|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定在自訂模式中顯示的快捷方式功能表項目。|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|移除 Outlook 工具列窗格中的所有按鈕。 (覆寫[CMFCToolBar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|

## <a name="remarks"></a>備註

如需如何執行 Outlook bar 的詳細資訊, 請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

如需 Outlook 橫條的範例, 請參閱 OutlookDemo 範例專案。

## <a name="example"></a>範例

下列範例示範如何使用`CMFCOutlookBarPane`類別的各種方法。 此範例示範如何建立 Outlook 工作列窗格、啟用頁面捲軸模式、啟用停駐, 以及設定 Outlook 橫條的背景色彩。 此程式碼片段是[Outlook 多路流覽範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>需求

**標頭:** afxoutlookbarpane。h

##  <a name="addbutton"></a>CMFCOutlookBarPane:: AddButton

將按鈕新增至 [Outlook 工作列] 窗格。

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>參數

*uiImage*<br/>
在指定點陣圖的資源識別碼。

*lpszLabel*<br/>
在指定按鈕的文字。

*iIdCommand*<br/>
在指定按鈕控制項的識別碼。

*iInsertAt*<br/>
在在要插入按鈕的 outlook 工具列頁面上, 指定以零為起始的索引。

*uiLabel*<br/>
在字串資源識別碼。

*szBmpFileName*<br/>
在指定要載入之磁片影像檔的名稱。

*szLabel*<br/>
在指定按鈕的文字。

*hBmp*<br/>
在按鈕點陣圖的控制碼。

*hIcon*<br/>
在按鈕圖示的控制碼。

### <a name="return-value"></a>傳回值

如果已成功新增按鈕, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用此方法可將新按鈕插入 Outlook 工具列的頁面中。 您可以從應用程式資源或從磁片檔案載入按鈕的影像。

如果*uiPageID*所指定的頁面識別碼為-1, 則按鈕會插入至第一頁。

如果*iInsertAt*所指定的索引為-1, 則會在頁面的結尾加入按鈕。

##  <a name="canbeattached"></a>CMFCOutlookBarPane:: CanBeAttached

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

釋放 [Outlook 工具列] 窗格上的影像所使用的資源。

```
void ClearAll();
```

### <a name="remarks"></a>備註

這個方法會直接呼叫[CMFCToolBarImages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), 這會在 Outlook 橫條窗格所使用的影像上呼叫。

##  <a name="create"></a>CMFCOutlookBarPane:: Create

建立 Outlook 橫條圖窗格。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
在指定 Outlook 橫條窗格控制項的父視窗。 不得為 Null。

*dwStyle*<br/>
在視窗樣式。  如需視窗樣式的清單, 請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
在控制項識別碼。 必須是唯一的, 才能夠儲存控制項的狀態。

*dwControlBarStyle*<br/>
在指定特殊樣式, 以定義 Outlook 工具列窗格控制項從 Outlook 橫條中斷連結時的行為。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

若要建立`CMFCOutlookBarPane`物件, 請先呼叫此函式, 然後`Create`呼叫, 它會建立 Outlook 橫條窗格控制項, `CMFCOutlookBarPane`並將其附加至物件。

如需有關`dwControlBarStyle`的詳細資訊, 請參閱[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。

##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane:: EnableCoNtextMenuItems

指定在自訂模式中顯示的快捷方式功能表項目。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>參數

*pButton*<br/>
在使用者按一下的工具列按鈕指標。

*pPopup*<br/>
在快捷方式功能表的指標。

### <a name="return-value"></a>傳回值

如果應該顯示快捷方式功能表, 則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

覆寫此方法, 以修改架構在自訂模式中顯示的架構標準快捷方式功能表。

預設的執行會檢查自訂模式 ( [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)), 如果設定為 TRUE, 則會停用所有的快捷方式功能表項目 ( **Delete**除外)。 然後, 它只會將輸入參數傳遞`CMFCToolBar::EnableContextMenuItems`至。

> [!NOTE]
> *內容功能表*是快捷方式功能表的同義字。

##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane:: EnablePageScrollMode

指定 Outlook 工具列窗格上的箭號是否要依頁面或按鈕按下按鈕來前移按鈕的清單。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>參數

*bPageScroll*<br/>
在若為 TRUE, 則啟用頁面捲軸模式。 如果為 FALSE, 則停用頁面捲軸模式。

##  <a name="getregularcolor"></a>CMFCOutlookBarPane:: GetRegularColor

傳回 Outlook 工具列窗格的一般 (也就是非選取的) 文字色彩。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>傳回值

以 RGB 色彩值為目前的文字色彩。

### <a name="remarks"></a>備註

使用[CMFCOutlookBarPane:: SetTextColor](#settextcolor)來設定 Outlook 橫條的目前 (一般和選取) 文字色彩。 您可以藉由呼叫[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)函數與 COLOR_WINDOW 索引來取得預設的文字色彩。

##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane:: IsBackgroundTexture

決定是否有針對 Outlook 工作列窗格載入的背景影像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>傳回值

如果要顯示背景影像, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您可以藉由呼叫[CMFCOutlookBarPane:: SetBackImage](#setbackimage)函數來新增背景影像。

如果沒有背景影像, 則會使用[CMFCOutlookBarPane:: SetBackColor](#setbackcolor)所指定的色彩來繪製背景。

##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane:: IsDrawShadedHighlight

決定當按鈕反白顯示並顯示背景影像時, 按鈕框線是否會加上陰影。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>傳回值

如果按鈕的框線呈陰影, 則為 TRUE;否則為 FALSE。

##  <a name="removeallbuttons"></a>CMFCOutlookBarPane:: RemoveAllButtons

移除 Outlook 工具列窗格中的所有按鈕。

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>CMFCOutlookBarPane:: RemoveButton

移除具有指定命令識別碼的按鈕。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>參數

*iIdCommand*<br/>
在指定要移除之按鈕的命令 ID。

### <a name="return-value"></a>傳回值

如果已成功移除按鈕, 則為 TRUE;如果指定的命令識別碼無效, 則為 FALSE。

##  <a name="setbackcolor"></a>CMFCOutlookBarPane:: SetBackColor

設定 Outlook 橫條的背景色彩。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在指定新的背景色彩。

### <a name="remarks"></a>備註

呼叫此函式可設定 Outlook 橫條的目前背景色彩。 只有在沒有背景影像時, 才會使用背景色彩。

##  <a name="setbackimage"></a>CMFCOutlookBarPane:: SetBackImage

設定背景影像。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>參數

*uiImageID*<br/>
在指定映射資源識別碼。

### <a name="remarks"></a>備註

呼叫這個方法以設定 Outlook 橫條的背景影像。 背景影像的清單是由內嵌的[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件所管理。

##  <a name="setdefaultstate"></a>CMFCOutlookBarPane:: SetDefaultState

將 Outlook [工具列] 窗格重設為原始的按鈕集。

```
void SetDefaultState();
```

### <a name="remarks"></a>備註

這個方法會將 Outlook 工作列按鈕還原成原始的集合。 這個方法類似`CMFCOutlookBarPane::RestoreOriginalstate`, 但它不會觸發 Outlook 橫條窗格的重繪。

##  <a name="setextraspace"></a>CMFCOutlookBarPane:: SetExtraSpace

設定 [Outlook 橫條圖] 窗格中按鈕周圍使用的填補圖元數。

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>CMFCOutlookBarPane:: SetTextColor

設定 Outlook 橫條圖窗格中一般和反白顯示文字的色彩。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>參數

*clrRegText*<br/>
在指定非選取文字的新色彩。

*clrSelText*<br/>
在指定所選取文字的新色彩。

##  <a name="settransparentcolor"></a>CMFCOutlookBarPane:: SetTransparentColor

設定 Outlook 工具列窗格的透明色彩。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
指定新的透明色彩。

### <a name="remarks"></a>備註

若要顯示透明影像, 必須要有透明色彩。 影像中任何出現的此色彩都會改為使用背景色彩來繪製。  不會混合背景和前景影像。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
