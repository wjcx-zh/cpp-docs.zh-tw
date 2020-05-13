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
ms.openlocfilehash: 97c7edde26bdf13e899d823dcf88d143068d86a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749603"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 類別

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

從[CMFCToolBar 類](../../mfc/reference/cmfctoolbar-class.md)派生的控制項,可以插入到 Outlook 欄[(CMFCOutlookBar 類](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 功能區窗格包含一欄大型按鈕。 如果按鈕清單比窗格還要大，使用者可以上下捲動清單。 當使用者將 Outlook 功能區窗格從 Outlook 功能區卸離時，這個窗格可以在主框架視窗中停駐或浮動。

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
|[CMFCOutlookBarPane::添加按鈕](#addbutton)|向 Outlook 欄窗格添加一個按鈕。|
|[CMFCOutlookbarPane::可以附加](#canbeattached)|確定窗格是否可以停靠到另一個窗格或框架視窗。 (覆蓋[CBasePane::可以附加](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|確定系統在自定義后是否可以將工具列還原到其原始狀態。 (覆蓋[CMFCTool 欄:可以還原](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane:清除所有](#clearall)|釋放Outlook欄窗格中圖像使用的資源。|
|[CMFCOutlookBarPane:創建](#create)|創建 Outlook 欄窗格。|
|`CMFCOutlookBarPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCOutlookBarPane::Dock`|由框架調用以停靠 Outlook 欄窗格。 (覆寫 `CPane::Dock`。)|
|[CMFCOutlookbarPane::啟用頁面滾動模式](#enablepagescrollmode)|指定「Outlook」欄窗格上的滾動箭頭是按頁面或按按鈕前進按鈕清單的。|
|[CMFCOutlookBarPane:獲取常規顏色](#getregularcolor)|返回 Outlook 欄窗格的常規(未選中)文字顏色。|
|`CMFCOutlookBarPane::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCOutlookBarPane:是背景紋理](#isbackgroundtexture)|確定是否為 Outlook 欄窗格載入了背景影像。|
|`CMFCOutlookBarPane::IsChangeState`|確定是否可以停靠浮動窗格。 (覆寫 `CPane::IsChangeState`。)|
|[CMFCOutlookBarPane::繪製高光](#isdrawshadedhighlight)|確定在突出顯示按鈕和顯示背景圖像時,按鈕邊框是否已呈現。|
|`CMFCOutlookBarPane::OnBeforeFloat`|當窗格即將浮動時,由框架調用。 (覆蓋[CPane::在浮動之前](../../mfc/reference/cpane-class.md#onbeforefloat)開啟 。|
|[CMFCOutlook 列::刪除按鈕](#removebutton)|刪除具有指定命令 ID 的按鈕。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。 (覆寫[CMFCTool 列:回復原始狀態](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|
|[CMFCOutlookbarPane::設置回彩](#setbackcolor)|設置背景顏色。|
|[CMFCOutlookBarPane::設置返回圖像](#setbackimage)|設置背景圖像。|
|[CMFCOutlook 欄::設定預設狀態](#setdefaultstate)|將 Outlook 欄窗格重置為原始按鈕集。|
|[CMFCOutlookbarPane:設置額外空間](#setextraspace)|設置 Outlook 欄窗格中按鈕周圍使用的填充圖元數。|
|[CMFCOutlookbarPane::設置文字顏色](#settextcolor)|在 Outlook 欄窗格中設定常規文字和突出顯示文本的顏色。|
|[CMFCOutlook 欄::設定透明色](#settransparentcolor)|設定 Outlook 欄窗格的透明顏色。|
|`CMFCOutlookBarPane::SmartUpdate`|在內部用於更新 Outlook 欄。 (覆寫 `CMFCToolBar::SmartUpdate`。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCOutlook 欄::啟用上下文選單專案](#enablecontextmenuitems)|指定在自定義模式下顯示的快捷選單項。|
|[CMFCOutlookBarPane::刪除所有按鈕](#removeallbuttons)|從 Outlook 欄窗格中刪除所有按鈕。 (覆寫[CMFCTool 列:刪除所有按鈕](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>備註

有關如何實現 Outlook 欄的資訊,請參閱[CMFCOutlookBar 類](../../mfc/reference/cmfcoutlookbar-class.md)。

有關 Outlook 欄的範例,請參閱 OutlookDemo 範例專案。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCOutlookBarPane`類的各種方法。 該範例展示如何建立Outlook欄窗格、啟用頁面滾動模式、啟用停靠以及設置Outlook欄的背景顏色。 此代碼段是 Outlook[多視圖示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>需求

**標題:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::添加按鈕

向 Outlook 欄窗格添加一個按鈕。

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
[在]指定點陣圖的資源識別碼。

*lpszLabel*<br/>
[在]指定按鈕的文字。

*iIdCommand*<br/>
[在]指定按鈕控制項的識別碼。

*iInsertAt*<br/>
[在]指定要插入按鈕的 Outlook 欄頁面上的零索引。

*烏伊標籤*<br/>
[在]字串資源識別碼。

*szBmpFile名稱*<br/>
[在]指定要載入的磁碟映像檔的名稱。

*szLabel*<br/>
[在]指定按鈕的文字。

*hBmp*<br/>
[在]按鈕點陣圖的句柄。

*hIcon*<br/>
[在]按鈕圖示的句柄。

### <a name="return-value"></a>傳回值

如果已成功添加按鈕,則為 TRUE;如果已成功添加按鈕,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

使用此方法將新按鈕插入到 Outlook 欄的頁面。 可以從應用程式資源或磁碟檔載入按鈕的圖像。

如果*uiPageID*指定的頁面 ID 為 -1,則該按鈕將插入到第一頁。

如果*iInsertAt*指定的索引為 -1,則按鈕將添加到頁面末尾。

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookbarPane::可以附加

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane:清除所有

釋放Outlook欄窗格上圖像使用的資源。

```cpp
void ClearAll();
```

### <a name="remarks"></a>備註

此方法直接調用[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear),它調用 Outlook 欄窗格使用的圖像。

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane:創建

創建 Outlook 欄窗格。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
[在]指定 Outlook 欄窗格控件的父視窗。 不能為 NULL。

*dwStyle*<br/>
[在]視窗樣式。  關於視窗樣式的清單,請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
[在]控件識別碼。 必須是唯一的才能保存控件的狀態。

*dwControlBar 樣式*<br/>
[在]指定定義 Outlook 欄窗格控件與 Outlook 欄分離時的行為的特殊樣式。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

要建構物件`CMFCOutlookBarPane`,請先調用建構函數,然後調`Create`用 ,這將創建 Outlook 欄窗格控件`CMFCOutlookBarPane`並將其附加到 物件。

有關有關的詳細資訊`dwControlBarStyle`,請參閱[CBasePane::創建 Ex](../../mfc/reference/cbasepane-class.md#createex)。

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlook 欄::啟用上下文選單專案

指定在自定義模式下顯示的快捷選單項。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[在]指向用戶按下的工具列按鈕的指標。

*pPopup*<br/>
[在]指向快捷功能表的指標。

### <a name="return-value"></a>傳回值

如果應顯示快捷功能表,則返回 TRUE;如果應顯示快捷方式功能表,則返回 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

重寫此方法以修改框架在自定義模式下顯示的框架標準快捷功能表。

預設實現檢查自定義模式[(CMFCToolBar::是自訂模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)),如果設置為 TRUE,則禁用**除刪除**之外的所有快捷功能表項。 然後,它只是將輸入參數傳遞給`CMFCToolBar::EnableContextMenuItems`。

> [!NOTE]
> *上下文菜單*是快捷功能表的同義詞。

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookbarPane::啟用頁面滾動模式

指定 Outlook 欄窗格上的滾動箭頭是逐頁前進按鈕清單,還是按按鈕前進。

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>參數

*bPageScroll*<br/>
[在]如果為 TRUE,則啟用頁面滾動模式。 如果 FALSE,則禁用頁面滾動模式。

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane:獲取常規顏色

返回 Outlook 欄窗格的常規(即未選中)文字顏色。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>傳回值

當前文字顏色作為 RGB 顏色值。

### <a name="remarks"></a>備註

使用[CMFCOutlookBarPane:SetTextColor](#settextcolor)設置 Outlook 欄的當前(常規和選定)文本顏色。 您可以透過使用COLOR_WINDOW索引呼叫[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)函數來取得預設文本顏色。

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane:是背景紋理

確定是否為 Outlook 欄窗格載入了背景影像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>傳回值

如果有要顯示的背景圖像,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

您可以通過調用[CMFCOutlookBarPane::設置返回圖像](#setbackimage)功能來添加背景圖像。

如果沒有背景影像,則使用[CMFCOutlookBarPane 指定的顏色繪製背景::設定返回顏色](#setbackcolor)。

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::繪製高光

確定在突出顯示按鈕和顯示背景圖像時,按鈕邊框是否已呈現。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>傳回值

如果按鈕的邊框被帶過,則為 TRUE;否則 FALSE。

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::刪除所有按鈕

從 Outlook 欄窗格中刪除所有按鈕。

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlook 列::刪除按鈕

刪除具有指定命令 ID 的按鈕。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>參數

*iIdCommand*<br/>
[在]指定要刪除的按鈕的命令 ID。

### <a name="return-value"></a>傳回值

如果按鈕已成功刪除,則為 TRUE;如果指定的命令 ID 無效,則 FALSE。

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookbarPane::設置回彩

設置 Outlook 欄的背景顏色。

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]指定新的背景顏色。

### <a name="remarks"></a>備註

呼叫此函數以設置 Outlook 欄的當前背景顏色。 僅當沒有背景圖像時,才使用背景顏色。

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::設置返回圖像

設置背景圖像。

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>參數

*uiImageID*<br/>
[在]指定影像資源識別碼。

### <a name="remarks"></a>備註

調用此方法以設置Outlook欄的背景圖像。 背景圖像清單由嵌入的[CMFCToolBarImages 類](../../mfc/reference/cmfctoolbarimages-class.md)物件管理。

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlook 欄::設定預設狀態

將 Outlook 欄窗格重置為原始按鈕集。

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>備註

此方法將 Outlook 欄按鈕還原到原始集。 此方法類似於`CMFCOutlookBarPane::RestoreOriginalstate`,只不過它不會觸發 Outlook 欄窗格的重繪。

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookbarPane:設置額外空間

設置 Outlook 欄窗格中按鈕周圍使用的填充圖元數。

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookbarPane::設置文字顏色

在 Outlook 欄窗格中設定常規文字和突出顯示文本的顏色。

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>參數

*clrRegText*<br/>
[在]指定非選定文字的新顏色。

*clrSelText*<br/>
[在]指定選取的文字的新顏色。

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlook 欄::設定透明色

設定 Outlook 欄窗格的透明顏色。

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
指定新的透明顏色。

### <a name="remarks"></a>備註

顯示透明圖像需要透明顏色。 圖像中此顏色的任何出現都用背景顏色繪製。  背景圖像和前景圖像沒有混合。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
