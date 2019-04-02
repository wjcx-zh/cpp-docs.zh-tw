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
ms.openlocfilehash: b23aa9e30c130cea8c84290b62cc19794376d4c1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773433"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 類別

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

控制項衍生自[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)，可插入 Outlook 功能區 ( [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 功能區窗格包含一欄大型按鈕。 如果按鈕清單比窗格還要大，使用者可以上下捲動清單。 當使用者將 Outlook 功能區窗格從 Outlook 功能區卸離時，這個窗格可以在主框架視窗中停駐或浮動。

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
|[CMFCOutlookBarPane::AddButton](#addbutton)|將按鈕加入至 Outlook 功能區窗格中。|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|判斷窗格是否可以停駐到另一個窗格或框架視窗。 (覆寫[CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|
|`CMFCOutlookBarPane::CanBeRestored`|判斷是否系統可以還原工具列為其原始狀態後自訂。 (覆寫[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|釋出 Outlook 功能區窗格中的映像所使用的資源。|
|[CMFCOutlookBarPane::Create](#create)|建立 Outlook 功能區窗格。|
|`CMFCOutlookBarPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCOutlookBarPane::Dock`|由架構呼叫以將 Outlook 功能區窗格停駐。 (覆寫 `CPane::Dock`。)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定是否在 Outlook 功能區窗格上的捲動箭號前進按鈕清單頁面上，或按鈕。|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|傳回 Outlook 功能區窗格的一般 （非選取） 的文字色彩。|
|`CMFCOutlookBarPane::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|判斷是否載入 Outlook 功能區窗格的背景影像。|
|`CMFCOutlookBarPane::IsChangeState`|判斷是否可以停駐浮動窗格。 (覆寫 `CPane::IsChangeState`。)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|判斷當按鈕已反白顯示，並顯示背景影像時，是否有陰影按鈕框線。|
|`CMFCOutlookBarPane::OnBeforeFloat`|當窗格即將浮點數時，由架構呼叫。 (覆寫[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|移除 [] 按鈕具有指定的命令 id。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。 (覆寫[CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|設定背景色彩。|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|設定背景影像。|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|將 Outlook 功能區窗格重設原始的按鈕集合中。|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|設定 Outlook 功能區窗格中的按鈕周圍使用邊框距離的像素數。|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|在 Outlook 功能區窗格中設定規則和反白顯示的文字的色彩。|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|設定 Outlook 功能區窗格的透明色彩。|
|`CMFCOutlookBarPane::SmartUpdate`|內部用來更新 Outlook 功能區。 (覆寫 `CMFCToolBar::SmartUpdate`。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定的快顯功能表項目會顯示在自訂模式。|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|從 Outlook 功能區窗格移除所有的按鈕。 (覆寫[CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|

## <a name="remarks"></a>備註

如需如何實作 Outlook 功能區的資訊，請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

如需 Outlook 功能區的範例，請參閱 OutlookDemo 範例專案。

## <a name="example"></a>範例

下列範例示範如何使用各種方法`CMFCOutlookBarPane`類別。 此範例示範如何建立 Outlook 功能區窗格，啟用頁面捲軸模式，啟用停駐，並設定 Outlook 功能區的背景色彩。 此程式碼片段是一部分[Outlook 多重檢視範例](../../overview/visual-cpp-samples.md)。

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

**標頭：** afxoutlookbarpane.h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

將按鈕加入至 Outlook 功能區窗格中。

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
[in]指定點陣圖的資源識別碼。

*lpszLabel*<br/>
[in]指定按鈕的文字。

*iIdCommand*<br/>
[in]指定按鈕控制項的識別碼。

*iInsertAt*<br/>
[in]要插入的按鈕的 outlook 功能區的頁面上指定的以零為起始的索引。

*uiLabel*<br/>
[in]字串資源 id。

*szBmpFileName*<br/>
[in]指定要載入之磁碟映像檔案名稱。

*szLabel*<br/>
[in]指定按鈕的文字。

*hBmp*<br/>
[in]按鈕的點陣圖控制代碼。

*hIcon*<br/>
[in]按鈕的圖示控制代碼。

### <a name="return-value"></a>傳回值

如果已成功; 新增按鈕，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

使用這個方法將新的按鈕插入 Outlook 功能區的頁面。 從應用程式資源，或是從磁碟檔案，就可以載入按鈕的影像。

如果所指定的頁面識別碼*uiPageID*為-1，按鈕會插入第一頁。

如果指定的索引*iInsertAt*為-1，按鈕就會加入結尾的頁面。

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

釋出 Outlook 功能區窗格上的映像所使用的資源。

```
void ClearAll();
```

### <a name="remarks"></a>備註

這個方法會直接呼叫[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，稱為映像所使用的 Outlook 功能區窗格上。

##  <a name="create"></a>  CMFCOutlookBarPane::Create

建立 Outlook 功能區窗格。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
[in]指定 Outlook 功能區窗格控制項的父視窗。 必須不是 NULL。

*dwStyle*<br/>
[in]視窗樣式。  如需視窗樣式的清單，請參閱 <<c0> [ 的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
[in]控制項 id。 必須是唯一以啟用儲存控制項的狀態。

*dwControlBarStyle*<br/>
[in]指定特殊從 Outlook 功能區中卸離時，定義行為的 Outlook 功能區窗格控制項的樣式。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

若要建構`CMFCOutlookBarPane`物件，第一次呼叫建構函式，然後再呼叫`Create`，這會建立列窗格控制項的 Outlook，並將它附加至`CMFCOutlookBarPane`物件。

如需詳細資訊`dwControlBarStyle`請參閱 < [cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

指定的快顯功能表項目會顯示在自訂模式。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[in]指標，使用者按下的工具列按鈕。

*pPopup*<br/>
[in]在捷徑功能表的指標。

### <a name="return-value"></a>傳回值

如果應該顯示的捷徑功能表，為 true，則傳回否則為 FALSE。

### <a name="remarks"></a>備註

覆寫此方法來修改架構會顯示在自訂模式中的 framework 標準的捷徑功能表。

預設實作會檢查自訂模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))，以及是否可以設定為 TRUE，會停用所有快顯功能表項目除外**刪除**。 然後，它只會傳遞的輸入的參數`CMFCToolBar::EnableContextMenuItems`。

> [!NOTE]
> *操作功能表*是快顯功能表的同義字。

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

指定捲動箭號，在 Outlook 功能區窗格是否前進的頁面或按鈕的按鈕的按鈕清單。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>參數

*bPageScroll*<br/>
[in]如果為 TRUE，讓頁面捲動模式。 如果為 FALSE，停用頁面捲動模式。

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

傳回一般 (亦即，未選取) 的 Outlook 功能區窗格的文字色彩。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>傳回值

目前的文字色彩為 RGB 色彩值。

### <a name="remarks"></a>備註

使用[CMFCOutlookBarPane::SetTextColor](#settextcolor)設定 Outlook 功能區的目前 （一般和已選取） 的文字色彩。 您可以藉由呼叫取得的預設文字色彩[GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) COLOR_WINDOW 索引的函式。

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

判斷是否載入 Outlook 功能區窗格的背景影像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>傳回值

如果沒有要顯示; 的背景影像，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

您可以藉由呼叫加入背景影像[CMFCOutlookBarPane::SetBackImage](#setbackimage)函式。

如果沒有任何背景影像，以使用指定的色彩繪製背景[CMFCOutlookBarPane::SetBackColor](#setbackcolor)。

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

判斷當按鈕已反白顯示，並顯示背景影像時，是否有陰影按鈕框線。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>傳回值

如果按鈕的框線會呈現灰色，則為 TRUE否則為 FALSE。

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

從 Outlook 功能區窗格移除所有的按鈕。

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

移除 [] 按鈕具有指定的命令 id。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>參數

*iIdCommand*<br/>
[in]指定要移除按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

如果成功移除 [] 按鈕;，則為 TRUE。如果指定的命令識別碼無效，則為 FALSE。

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

設定 Outlook 功能區的背景色彩。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
[in]指定新的背景色彩。

### <a name="remarks"></a>備註

呼叫此函式來設定 Outlook 功能區的目前背景色彩。 只有在沒有任何背景影像，會使用背景色彩。

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

設定背景影像。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>參數

*uiImageID*<br/>
[in]指定映像資源識別碼。

### <a name="remarks"></a>備註

呼叫這個方法來設定 Outlook 列的背景影像。 受管理的背景影像清單的內嵌[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件。

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

將 Outlook 功能區窗格重設原始的按鈕集合中。

```
void SetDefaultState();
```

### <a name="remarks"></a>備註

這個方法會將 [Outlook] 列按鈕還原到原始的集合。 這個方法就像`CMFCOutlookBarPane::RestoreOriginalstate`，不同之處在於它不會觸發的 Outlook 功能區窗格重繪。

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

設定 Outlook 功能區窗格中的按鈕周圍使用邊框距離的像素數。

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

在 Outlook 功能區窗格中設定規則和反白顯示的文字的色彩。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>參數

*clrRegText*<br/>
[in]指定新的非選取的文字色彩。

*clrSelText*<br/>
[in]指定選定文字的新色彩。

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

設定 Outlook 功能區窗格的透明色彩。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
指定新的透明色彩。

### <a name="remarks"></a>備註

顯示透明的映像所需的透明色彩。 是改為使用的背景色彩繪製任一發生事件，此映像中的色彩。  沒有任何透明混色的背景和前景的映像。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
