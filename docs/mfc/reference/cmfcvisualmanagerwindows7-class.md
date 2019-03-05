---
title: CMFCVisualManagerWindows7 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 296ccc0accdf2937406d9965118c1807aeb2604c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269392"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 類別

`CMFCVisualManagerWindows7`讓應用程式的 Windows 7 應用程式的外觀。

## <a name="syntax"></a>語法

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|預設建構函式。|
|[CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7__~cmfcvisualmanagerwindows7)|預設解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|清除目前的視覺化樣式，並會重設預設視覺化樣式。|
|`CMFCVisualManagerWindows7::CleanUp`|清除所有的使用者介面中的物件，並會重設功能表。|
|`CMFCVisualManagerWindows7::DrawNcBtn`|在框架上，在非工作區中繪製的按鈕。 這個方法，以繪製降到最低，架構會使用最大化、 關閉並還原中的視窗框架的右上角的按鈕。 程式會使用非 Aero 佈景主題時，不會呼叫這個方法。|
|`CMFCVisualManagerWindows7::DrawNcText`|在框架上，在非工作區中繪製文字。 架構會使用這個方法，來繪製應用程式標題的框架視窗頂端的標題列中。|
|`CMFCVisualManagerWindows7::DrawSeparator`|上繪製分隔符號[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。|
|`CMFCVisualManagerWindows7::GetRibbonBar`|擷取[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)使用者介面相關聯。|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|取得功能區編輯方塊的背景色彩。|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|覆寫[CMFCVisualManager::GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|覆寫[CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|覆寫[CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|覆寫[CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|覆寫[CMFCVisualManager::IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|決定是否`CMFCRibbonBar`存在且可見。|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|覆寫[CMFCVisualManagerWindows::OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|覆寫[CMFCVisualManagerWindows::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|覆寫[CMFCVisualManagerWindows::OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|覆寫[CMFCVisualManager::OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|覆寫[CMFCVisualManagerWindows::OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|覆寫[CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|覆寫[CMFCVisualManager::OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|覆寫 `CMFCVisualManager::OnDrawRadioButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|覆寫[CMFCVisualManager::OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|覆寫[CMFCVisualManager::OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|覆寫[CMFCVisualManager::OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|覆寫[CMFCVisualManager::OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Overrides [CMFCVisualManager::OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Overrides [CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Overrides [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Overrides [CMFCVisualManager::OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|覆寫 `CMFCVisualManager::OnDrawRibbonLaunchButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Overrides [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Overrides [CMFCVisualManager::OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Overrides [CMFCVisualManager::OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Overrides [CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|覆寫[CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|覆寫[CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Overrides [CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|覆寫[CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|覆寫[CMFCVisualManager::OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|覆寫[CMFCVisualManager::OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|覆寫[CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|覆寫[CMFCVisualManagerWindows::OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|覆寫[CMFCVisualManagerWindows::OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|填入功能表項目影像的周圍區域時，架構會呼叫這個方法。|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|覆寫[CMFCVisualManager::OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Overrides [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|覆寫[CMFCVisualManagerWindows::OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|覆寫[CMFCVisualManager::OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|覆寫[CMFCVisualManager::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|覆寫[CMFCVisualManagerWindows::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|設定描述的視覺管理員屬性的資源控制代碼。|
|`CMFCVisualManagerWindows7::SetStyle`|設定的色彩配置`CMFCVisualManagerWindows7`GUI。|

## <a name="remarks"></a>備註

使用`CMFCVisualManagerWindows7`類別，以變更您的應用程式，來模擬預設的 Windows 7 應用程式的外觀。 這個類別可能不正確，如果您的應用程式的 Windows 版本早於 Windows 7 上執行。 在該案例中，應用程式使用中定義的預設視覺管理員[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)。

CMFCVisualManagerWindows7 多個方法同時繼承自[CMFCVisualManagerWindows 類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)而`CMFCVisualManager`類別。 上一節中所列的方法是方法的新手`CMFCVisualManagerWindows7`類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>需求

**標頭：** afxvisualmanagerwindows7.h

##  <a name="_dtorcmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7

預設解構函式。

```
virtual ~CMFCVisualManagerWindows7();
```

##  <a name="cmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

預設建構函式。

```
CMFCVisualManagerWindows7();
```

##  <a name="getribboneditbackgroundcolor"></a>  CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

取得功能區編輯方塊的背景色彩。

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>參數

*pEdit*<br/>
[in]編輯控制項指標。 此值不能是 NULL。

*bIsHighlighted*<br/>
[out]傳回功能區方塊是否反白顯示。

*bIsPaneHighlighted*<br/>
[out]傳回 TRUE，如果功能區面板，會包含*pEdit*會反白顯示。

*bIsDisabled*<br/>
[out]傳回是否*pEdit*已停用。

### <a name="return-value"></a>傳回值

在編輯方塊的背景色彩*pEdit*。

### <a name="remarks"></a>備註

##  <a name="onfillmenuimagerect"></a>  CMFCVisualManagerWindows7::OnFillMenuImageRect

當它填滿 功能表項目影像周圍的區域時，架構會呼叫這個方法。

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rect,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容功能表按鈕的指標。

*pButton*<br/>
[in]指標`CMFCToolBarButton`。 此架構會填滿此按鈕的背景。

*rect*<br/>
[in]指定的功能表按鈕的影像區域界限的矩形。

*state*<br/>
[in]按鈕的狀態。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows 類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
