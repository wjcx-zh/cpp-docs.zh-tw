---
title: CMFCVisualManagerWindows7 類別
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 6686afecc2b8ef97ea24ef45ff5225433677a954
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319840"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 類別

為`CMFCVisualManagerWindows7`應用程式提供 Windows 7 應用程式的外觀。

## <a name="syntax"></a>語法

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC視覺管理員視窗7::CMFC視覺管理器Windows7](#cmfcvisualmanagerwindows7)|預設建構函式。|
|[CMFC視覺管理員視窗7::~CMFC視覺管理器7](#_dtorcmfcvisualmanagerwindows7)|默認析構函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|清除當前視覺樣式並重置預設視覺樣式。|
|`CMFCVisualManagerWindows7::CleanUp`|清除用戶介面中的所有物件並重置功能表。|
|`CMFCVisualManagerWindows7::DrawNcBtn`|在框架的非工作區中繪製一個按鈕。 框架使用此方法在視窗框架的右上角繪製最小化、最大化、關閉和恢復按鈕。 僅當程式使用`Aero`主題時,才調用此方法。|
|`CMFCVisualManagerWindows7::DrawNcText`|在框架的非工作區中繪製文本。 框架使用此方法在框架視窗頂部的標題列中繪製應用程式標題。|
|`CMFCVisualManagerWindows7::DrawSeparator`|在[CMFCToolBar 類](../../mfc/reference/cmfctoolbar-class.md)上繪製分隔符。|
|`CMFCVisualManagerWindows7::GetRibbonBar`|檢索與使用者介面關聯的[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)。|
|[CMFC 視覺管理員視窗7::取得功能編輯背景顏色](#getribboneditbackgroundcolor)|取得功能區編輯框背景顏色。|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|覆[寫 CMFC 視覺化管理員::取得放大縮小字型功能 放大縮小字型功能](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|覆[寫 CMFC 視覺管理員::取得功能快速存取工具BarVveV偏移](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|覆[寫 CMFC 視覺管理員::取得功能快速存取工具列邊緣](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|覆[寫 CMFC 視覺化管理員視窗::是突顯完整選單專案](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|覆[寫 CMFC 視覺化管理員::擁有者DrawMenu檢查](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|確定是否存在`CMFCRibbonBar`和可見。|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|覆[寫 CMFC 視覺化管理員視窗::在繪製按鈕邊框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|覆[寫 CMFC 視覺化管理員視窗::在DrawCheckBoxEx上](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|覆[寫 CMFC 視覺化管理員視窗::OnDrawComDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|覆[寫 CMFC 視覺化管理員::在繪製預設功能圖片](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|覆[寫 CMFC 視覺化管理員視窗::在繪製選單邊框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|覆[寫 CMFC 視覺管理員::在繪製選單檢查](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|覆[寫 CMFC 視覺管理員::在DrawMenu標籤上](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|覆寫 `CMFCVisualManager::OnDrawRadioButton`。|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|覆[寫 CMFC 視覺化管理員::在繪製功能應用程式按鈕](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|覆[寫 CMFC 視覺管理員::在繪製功能按鈕邊框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|覆[寫 CMFC 視覺管理員::繪製功能標題](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|覆[寫 CMFC 視覺管理員::在繪製功能字幕按鈕](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|覆[寫 CMFC 視覺化管理員::OnDraw 功能區類別](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|覆[寫 CMFC 視覺化管理員::在繪製功能符類別選項卡](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|覆[寫 CMFC 視覺化管理員::在繪製功能區預設窗格按鈕](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|覆[寫 CMFC 視覺化管理員::在Draw功能區畫廊按鈕](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|覆寫 `CMFCVisualManager::OnDrawRibbonLaunchButton`。|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|覆[寫 CMFC 視覺化管理員::繪製功能選單檢查框架](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|覆[寫 CMFC 視覺管理員::在繪製功能面板](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|覆[寫 CMFC 視覺管理員::在DrawRibbon面板標題](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|覆[寫 CMFC 視覺化管理員::在繪製功能進度列](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|覆[寫 CMFC 視覺化管理員::繪製功能最近檔案框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|覆[寫 CMFC 視覺化管理員::在繪製功能滑塊通道](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|覆[寫 CMFC 視覺化管理員::在繪製功能滑動](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|覆[寫 CMFC 視覺化管理員::在繪製功能滑動點縮放按鈕](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|覆[寫 CMFC 視覺化管理員::在繪製功能狀態列窗格](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|覆[寫 CMFC 視覺化管理員::在繪製功能符選項卡框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|覆[寫 CMFC 視覺化管理員視窗::在繪製狀態列大小框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|覆[寫 CMFC 視覺化管理員視窗::開啟填充列背景](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|覆[寫 CMFC 視覺化管理員視窗::開啟填充按鈕內部](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::在填充功能表圖像重新ct](#onfillmenuimagerect)|當框架填充功能表項圖像周圍的區域時,它將調用此方法。|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|覆[寫 CMFC 視覺化管理員:開啟填充功能按鈕](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|覆[寫 CMFC 視覺管理員::在填充功能快速存取工具列彈出](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|覆[寫 CMFC 視覺化管理員視窗::在突顯選單項目](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|覆[寫 CMFC 視覺化管理員::開啟 NcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|覆[寫 CMFC 視覺化管理員::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|覆[寫 CMFC 視覺化管理員視窗::更新系統顏色](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|設置描述視覺化管理員屬性的資源句柄。|
|`CMFCVisualManagerWindows7::SetStyle`|設置 GUI`CMFCVisualManagerWindows7`的色彩配置。|

## <a name="remarks"></a>備註

使用`CMFCVisualManagerWindows7`類更改應用程式的外觀以類比預設的 Windows 7 應用程式。 如果應用程式在 Windows 7 之前的版本上運行,則此類可能無效。 在這種情況下,應用程式使用[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)中定義的預設可視化管理器。

CMFCVisualManagerWindows7 從[CMFCVisualManagerWindows 類](../../mfc/reference/cmfcvisualmanagerwindows-class.md)和`CMFCVisualManager`類繼承多種方法。 上一節中列出的方法是類`CMFCVisualManagerWindows7`的新方法。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase 視覺化管理員](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFC可視化經理辦公室XP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>需求

**標題:** afxvisualmanagerwindows7.h

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a>CMFC視覺管理員視窗7::~CMFC視覺管理器7

默認析構函數。

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a>CMFC視覺管理員視窗7::CMFC視覺管理器Windows7

預設建構函式。

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a>CMFC 視覺管理員視窗7::取得功能編輯背景顏色

取得功能區編輯框的背景顏色。

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>參數

*pEdit*<br/>
[在]指向編輯控制件的指標。 此值不能為 NULL。

*bIs 突顯*<br/>
[出]返回功能區框是否突出顯示。

*bIsPane 突顯*<br/>
[出]如果突出顯示包含*pEdit*的功能區面板,則返回 TRUE。

*bIs 已關閉*<br/>
[出]返回是否禁用*pEdit。*

### <a name="return-value"></a>傳回值

編輯框*pEdit*的背景顏色。

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a>CMFCVisualManagerWindows7::在填充功能表圖像重新ct

當框架填充功能表項圖像周圍的區域時,它將調用此方法。

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向功能表按鈕的設備上下文的指標。

*pButton*<br/>
[在]指向的`CMFCToolBarButton`指標。 框架填充此按鈕的背景。

*矩形*<br/>
[在]指定功能表按鈕影像區域邊界的矩形。

*state*<br/>
[在]按鈕狀態。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFC 視覺化管理員類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
