---
title: "CMFCVisualManagerOffice2003 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCVisualManagerOffice2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCVisualManagerOffice2003 class
ms.assetid: 115482cd-e349-450a-8dc4-c6023d092aab
caps.latest.revision: 31
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: db48c053de741ff37aacf377f338ea4af4d3bec1
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcvisualmanageroffice2003-class"></a>CMFCVisualManagerOffice2003 類別
`CMFCVisualManagerOffice2003`為應用程式提供 Microsoft Office 2003 的外觀。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCVisualManagerOffice2003 : public CMFCVisualManagerOfficeXP  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCVisualManagerOffice2003::DrawComboBorderWinXP](#drawcomboborderwinxp)|繪製使用目前的 Windows XP 主題的下拉式方塊框線。 (覆寫[CMFCVisualManager::DrawComboBorderWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawcomboborderwinxp)。)|  
|[CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP](#drawcombodropbuttonwinxp)|繪製使用目前的 Windows XP 主題的下拉式方塊下拉式按鈕。 (覆寫[CMFCVisualManager::DrawComboDropButtonWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawcombodropbuttonwinxp)。)|  
|[CMFCVisualManagerOffice2003::DrawCustomizeButton](#drawcustomizebutton)|繪製自訂按鈕。|  
|[CMFCVisualManagerOffice2003::DrawPushButtonWinXP](#drawpushbuttonwinxp)|繪製使用目前的 Windows XP 主題的按鈕。 (覆寫[CMFCVisualManager::DrawPushButtonWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawpushbuttonwinxp)。)|  
|[CMFCVisualManagerOffice2003::GetBaseThemeColor](#getbasethemecolor)|取得基底的佈景主題色彩。|  
|[CMFCVisualManagerOffice2003::GetHighlightMenuItemColor](#gethighlightmenuitemcolor)|取得用於反白顯示的功能表項目的色彩。|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|架構會呼叫這個方法，取得屬性清單的背景色彩。 (覆寫 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupColor`。)|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor](#getpropertygridgrouptextcolor)|架構會呼叫這個方法，以擷取的屬性清單的文字色彩。 (覆寫 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupTextColor`。)|  
|[CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight](#getshowallmenuitemsheight)|傳回所有功能表項目高度。 (覆寫[CMFCVisualManager::GetShowAllMenuItemsHeight](../../mfc/reference/cmfcvisualmanager-class.md#getshowallmenuitemsheight)。)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors](#getsmartdockingbaseguidecolors)|設定指定的基底群組的背景色彩和框線色彩。 (覆寫 `CMFCVisualManagerOfficeXP::GetSmartDockingBaseGuideColors`。)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor](#getsmartdockinghighlighttonecolor)|取得反白顯示的色調色彩。 (覆寫[CMFCVisualManager::GetSmartDockingHighlightToneColor](../../mfc/reference/cmfcvisualmanager-class.md#getsmartdockinghighlighttonecolor)。)|  
|[CMFCVisualManagerOffice2003::GetTabFrameColors](#gettabframecolors)|必須擷取一組色彩繪製 索引標籤視窗時，架構會呼叫此函式。 (覆寫[CMFCVisualManager::GetTabFrameColors](../../mfc/reference/cmfcvisualmanager-class.md#gettabframecolors)。)|  
|[CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin](#gettoolbarcustomizebuttonmargin)|取得自訂工具列按鈕的邊界。 (覆寫 `CMFCVisualManager::GetToolBarCustomizeButtonMargin`。)|  
|[CMFCVisualManagerOffice2003::GetToolbarDisabledColor](#gettoolbardisabledcolor)|取得工具列已停用的色彩。 (覆寫 `CMFCVisualManager::GetToolbarDisabledColor`。)|  
|[CMFCVisualManagerOffice2003::GetToolTipInfo](#gettooltipinfo)|若要取得工具提示資訊架構呼叫。 (覆寫[CMFCVisualManager::GetToolTipInfo](../../mfc/reference/cmfcvisualmanager-class.md#gettooltipinfo)。)|  
|[CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled](#isdefaultwinxpcolorsenabled)|表示視覺管理員是否使用原生的 Windows XP 佈景主題色彩。|  
|[CMFCVisualManagerOffice2003::IsDockingTabHasBorder](#isdockingtabhasborder)|傳回目前的視覺管理員是否會繪製停駐和索引標籤式窗格周圍的框線。 (覆寫[CMFCVisualManager::IsDockingTabHasBorder](../../mfc/reference/cmfcvisualmanager-class.md#isdockingtabhasborder)。)|  
|[CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs](#ishighlightonenotetabs)|指出是否應該醒目提示 OneNote 索引標籤。 (覆寫 `CMFCVisualManager::IsHighlightOneNoteTabs`。)|  
|[CMFCVisualManagerOffice2003::IsOffsetPressedButton](#isoffsetpressedbutton)|繪製工具列按鈕時，由架構呼叫。 (覆寫 `CMFCVisualManager::IsOffsetPressedButton`。)|  
|[CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook](#isstatusbarofficexplook)|指出是否有狀態列，以 Office XP 外觀。|  
|[CMFCVisualManagerOffice2003::IsToolbarRoundShape](#istoolbarroundshape)|指出指定的工具列是否具有圓角圖案。 (覆寫[CMFCVisualManager::IsToolbarRoundShape](../../mfc/reference/cmfcvisualmanager-class.md#istoolbarroundshape)。)|  
|[CMFCVisualManagerOffice2003::IsUseGlobalTheme](#isuseglobaltheme)|指出是否要使用全域 Windows XP 主題。|  
|[CMFCVisualManagerOffice2003::IsWindowsThemingSupported](#iswindowsthemingsupported)|指出是否支援 Windows 佈景主題。 (覆寫[CMFCVisualManager::IsWindowsThemingSupported](../../mfc/reference/cmfcvisualmanager-class.md#iswindowsthemingsupported)。)|  
|[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|當它繪製自動隱藏按鈕的邊框時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawautohidebuttonborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawBarGripper](#ondrawbargripper)|當它繪製控制項 bar 移駐夾，由架構呼叫。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawBarGripper`。)|  
|[CMFCVisualManagerOffice2003::OnDrawBrowseButton](#ondrawbrowsebutton)|當它繪製編輯控制項的瀏覽 按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`。)|  
|[CMFCVisualManagerOffice2003::OnDrawButtonBorder](#ondrawbuttonborder)|當它繪製工具列按鈕的框線，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder](#ondrawcaptionbarborder)|架構會呼叫這個方法時它繪製的框線[CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)物件。 (覆寫[CMFCVisualManager::OnDrawCaptionBarBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcaptionbarborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawCheckBoxEx](#ondrawcheckboxex)|它會繪製一個核取方塊時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcheckboxex)。)|  
|[CMFCVisualManagerOffice2003::OnDrawComboBorder](#ondrawcomboborder)|架構會呼叫這個方法時它繪製周圍的框線[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawComboBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawComboDropButton](#ondrawcombodropbutton)|它會繪製的下拉式按鈕時，架構會呼叫這個方法[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`。)|  
|[CMFCVisualManagerOffice2003::OnDrawControlBorder](#ondrawcontrolborder)|當它繪製控制項的框線，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawControlBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcontrolborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawExpandingBox](#ondrawexpandingbox)|當它繪製展開的方塊時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawExpandingBox](../../mfc/reference/cmfcvisualmanager-class.md#ondrawexpandingbox)。)|  
|[CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder](#ondrawheaderctrlborder)|它繪製的框線的執行個體時，架構會呼叫這個方法[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)。 (覆寫[CMFCVisualManager::OnDrawHeaderCtrlBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawheaderctrlborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawMenuBorder](#ondrawmenuborder)|架構會呼叫這個方法時它繪製的框線[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter](#ondrawoutlookbarsplitter)|它繪製為 outlook 功能區分割時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawOutlookBarSplitter](../../mfc/reference/cmfcvisualmanager-class.md#ondrawoutlookbarsplitter)。)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder](#ondrawoutlookpagebuttonborder)|當它繪製框線的 Outlook 頁 按鈕時，由架構呼叫。 (覆寫[CMFCVisualManager::OnDrawOutlookPageButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawoutlookpagebuttonborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneBorder](#ondrawpaneborder)|架構會呼叫這個方法時它繪製的框線[CPane 類別](../../mfc/reference/cpane-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneCaption](#ondrawpanecaption)|架構會呼叫這個方法時它繪製的標題[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`。)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder](#ondrawpopupwindowborder)|當它繪製框線的快顯視窗時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder](#ondrawpopupwindowbuttonborder)|它會在快顯視窗中繪製按鈕的框線時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption](#ondrawpopupwindowcaption)|當它繪製標題的快顯視窗時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowCaption`。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup](#ondrawribbonbuttonsgroup)|當它在功能區上繪製一組按鈕時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawRibbonButtonsGroup](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonsgroup)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption](#ondrawribboncategorycaption)|當它繪製功能區分類的標題列，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawRibbonCategoryCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorycaption)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab](#ondrawribboncategorytab)|當它繪製為功能區類別目錄 索引標籤時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar](#ondrawribbonprogressbar)|架構會呼叫這個方法時，它會繪製[CMFCRibbonProgressBar 類別](../../mfc/reference/cmfcribbonprogressbar-class.md)。 (覆寫[CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator](#ondrawribbonquickaccesstoolbarseparator)|它會快速存取工具列功能區上繪製分隔符號時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawRibbonQuickAccessToolBarSeparator`。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel](#ondrawribbonsliderchannel)|架構會呼叫這個方法時它繪製的色板[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)。 (覆寫[CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb](#ondrawribbonsliderthumb)|它繪製的捲動方塊時，架構會呼叫這個方法[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)物件。 (覆寫[CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton](#ondrawribbonsliderzoombutton)|當它繪製 [縮放] 按鈕時，架構會呼叫這個方法[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)物件。 (覆寫[CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane](#ondrawribbonstatusbarpane)|當它在狀態列上繪製一個窗格，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawRibbonStatusBarPane`。)|  
|[CMFCVisualManagerOffice2003::OnDrawScrollButtons](#ondrawscrollbuttons)|當它繪製捲動按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`。)|  
|[CMFCVisualManagerOffice2003::OnDrawSeparator](#ondrawseparator)|當它繪製分隔符號時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawSeparator`。)|  
|[CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems](#ondrawshowallmenuitems)|當它繪製功能表中的所有項目時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnDrawShowAllMenuItems](../../mfc/reference/cmfcvisualmanager-class.md#ondrawshowallmenuitems)。)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder](#ondrawstatusbarpaneborder)|架構會呼叫這個方法時它繪製的框線[CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarProgress](#ondrawstatusbarprogress)|架構會呼叫這個方法時，它會在上繪製進度列指示器[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)物件。 (覆寫[CMFCVisualManager::OnDrawStatusBarProgress](../../mfc/reference/cmfcvisualmanager-class.md#ondrawstatusbarprogress)。)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox](#ondrawstatusbarsizebox)|架構會呼叫這個方法時它繪製大小方塊[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)。 (覆寫[CMFCVisualManager::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanager-class.md#ondrawstatusbarsizebox)。)|  
|[CMFCVisualManagerOffice2003::OnDrawTab](#ondrawtab)|它會繪製的索引標籤時，架構會呼叫這個方法[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTab`。)|  
|[CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder](#ondrawtabsbuttonborder)|當它繪製框線的索引標籤 按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawTask](#ondrawtask)|架構會呼叫這個方法時，它會繪製[CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTask`。)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder](#ondrawtasksgroupareaborder)|架構會呼叫這個方法時，它會在上繪製一組周圍的框線[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`。)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption](#ondrawtasksgroupcaption)|架構會呼叫這個方法時它繪製的標題[CMFCTasksPaneTaskGroup 類別](../../mfc/reference/cmfctaskspanetaskgroup-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`。)|  
|[CMFCVisualManagerOffice2003::OnDrawTearOffCaption](#ondrawtearoffcaption)|架構會呼叫這個方法時它繪製的標題[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`。)|  
|[CMFCVisualManagerOffice2003::OnErasePopupWindowButton](#onerasepopupwindowbutton)|它會清除快顯視窗中的按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`。)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsArea](#onerasetabsarea)|它會清除 索引標籤的區域 索引標籤視窗時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnEraseTabsArea`。)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsButton](#onerasetabsbutton)|它會清除文字和圖示的索引標籤 按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnEraseTabsButton`。)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsFrame](#onerasetabsframe)|它會清除上的框架上時，架構會呼叫這個方法[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)。 (覆寫[CMFCVisualManager::OnEraseTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#onerasetabsframe)。)|  
|[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|當它填入自動隱藏按鈕的背景時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillautohidebuttonbackground)。)|  
|[CMFCVisualManagerOffice2003::OnFillBarBackground](#onfillbarbackground)|架構會呼叫這個方法時的背景填滿[CBasePane 類別](../../mfc/reference/cbasepane-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillBarBackground`。)|  
|[CMFCVisualManagerOffice2003::OnFillButtonInterior](#onfillbuttoninterior)|工具列按鈕的背景填滿時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillButtonInterior`。)|  
|[CMFCVisualManagerOffice2003::OnFillCommandsListBackground](#onfillcommandslistbackground)|屬於命令清單的工具列按鈕的背景填滿時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`。)|  
|[CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground](#onfillheaderctrlbackground)|標頭控制項的背景填滿時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnFillHeaderCtrlBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillheaderctrlbackground)。)|  
|[CMFCVisualManagerOffice2003::OnFillHighlightedArea](#onfillhighlightedarea)|它填滿反白顯示的區域的工具列按鈕時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillHighlightedArea`。)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookBarCaption](#onfilloutlookbarcaption)|當 Outlook 標題列的背景填滿時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnFillOutlookBarCaption](../../mfc/reference/cmfcvisualmanager-class.md#onfilloutlookbarcaption)。)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookPageButton](#onfilloutlookpagebutton)|它填滿內部 Outlook 頁 按鈕時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::OnFillOutlookPageButton](../../mfc/reference/cmfcvisualmanager-class.md#onfilloutlookpagebutton)。)|  
|[CMFCVisualManagerOffice2003::OnFillPopupWindowBackground](#onfillpopupwindowbackground)|快顯視窗的背景填滿時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillPopupWindowBackground`。)|  
|[CMFCVisualManagerOffice2003::OnFillTab](#onfilltab)|填滿 索引標籤視窗的背景時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillTab`。)|  
|[CMFCVisualManagerOffice2003::OnFillTasksGroupInterior](#onfilltasksgroupinterior)|架構會呼叫這個方法時它填滿內部[CMFCTasksPaneTaskGroup 類別](../../mfc/reference/cmfctaskspanetaskgroup-class.md)物件。 (覆寫 `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`。)|  
|[CMFCVisualManagerOffice2003::OnFillTasksPaneBackground](#onfilltaskspanebackground)|架構會呼叫這個方法時的背景填滿[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控制項。 (覆寫[CMFCVisualManager::OnFillTasksPaneBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfilltaskspanebackground)。)|  
|[CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton](#onhighlightquickcustomizemenubutton)|這個架構會呼叫這個方法，它會繪製反白顯示時快速自訂功能表按鈕。 (覆寫 `CMFCVisualManagerOfficeXP::OnHighlightQuickCustomizeMenuButton`。)|  
|[CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems](#onhighlightrarelyusedmenuitems)|當它繪製反白顯示的功能表命令時，架構會呼叫這個方法。 (覆寫 `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`。)|  
|[CMFCVisualManagerOffice2003::OnUpdateSystemColors](#onupdatesystemcolors)|當系統色彩變更時，架構會呼叫此函式。 (覆寫 `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`。)|  
|[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](#setdefaultwinxpcolors)|指定視覺管理員應該使用原生的 Windows XP 佈景主題色彩或色彩取自[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。|  
|[CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook](#setstatusbarofficexplook)|指定應該使用 Windows XP 全域主題。|  
|[CMFCVisualManagerOffice2003::SetUseGlobalTheme](#setuseglobaltheme)|指定視覺管理員是否使用全域主題。|  
  
## <a name="remarks"></a>備註  
 您使用`CMFCVisualManagerOffice2003`類別來變更您的應用程式類似 Microsoft Office 2003 的視覺外觀。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定 office 2003 視覺管理員。 此程式碼片段是一部分[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfcvisualmanageroffice2003-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxvisualmanageroffice2003.h  
  
##  <a name="a-namedrawcomboborderwinxpa--cmfcvisualmanageroffice2003drawcomboborderwinxp"></a><a name="drawcomboborderwinxp"></a>CMFCVisualManagerOffice2003::DrawComboBorderWinXP  
 繪製使用目前的 Windows XP 主題的下拉式方塊框線。  
  
```  
virtual BOOL DrawComboBorderWinXP(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 下拉式方塊框的週框。  
  
 [in] `bDisabled`  
 指定是否要停用下拉式方塊框線。  
  
 [in] `bIsDropped`  
 指定是否要卸除的下拉式方塊的框線。  
  
 [in] `bIsHighlighted`  
 指定下拉式方塊框線會反白顯示。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果已啟用佈景主題的 API 或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedrawcombodropbuttonwinxpa--cmfcvisualmanageroffice2003drawcombodropbuttonwinxp"></a><a name="drawcombodropbuttonwinxp"></a>CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP  
 繪製使用目前的 Windows XP 主題的下拉式方塊下拉式按鈕。  
  
```  
virtual BOOL DrawComboDropButtonWinXP(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 下拉式方塊下拉式按鈕，這個周框。  
  
 [in] `bDisabled`  
 指定是否要停用下拉式方塊下拉式按鈕。  
  
 [in] `bIsDropped`  
 指定是否要卸除下拉式方塊下拉式按鈕。  
  
 [in] `bIsHighlighted`  
 指定下拉式方塊下拉式按鈕會反白顯示。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果已啟用佈景主題的 API 或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedrawcustomizebuttona--cmfcvisualmanageroffice2003drawcustomizebutton"></a><a name="drawcustomizebutton"></a>CMFCVisualManagerOffice2003::DrawCustomizeButton  
 繪製自訂按鈕。  
  
```  
virtual void DrawCustomizeButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsHorz,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    BOOL bIsCustomize,  
    BOOL bIsMoreButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 顯示內容的指標。  
  
 [in] `rect`  
 週框的按鈕  
  
 [in] `bIsHorz`  
 `TRUE`如果按鈕是水平、 或`FALSE`如果垂直。  
  
 [in] `state`  
 要繪製 （一般、 按下或反白顯示） 是與按鈕的狀態。  
  
 [in] `bIsCustomize`  
 `TRUE`如果自訂下拉式箭號或左箭號影像應該繪製按鈕在矩形中，或`FALSE`如果不是。  
  
 [in] `bIsMoreButtons`  
 `TRUE`如果水平或垂直自訂多按鈕應該在按鈕的矩形中繪製影像或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedrawpushbuttonwinxpa--cmfcvisualmanageroffice2003drawpushbuttonwinxp"></a><a name="drawpushbuttonwinxp"></a>CMFCVisualManagerOffice2003::DrawPushButtonWinXP  
 繪製使用目前的 Windows XP 主題的按鈕。  
  
```  
virtual BOOL DrawPushButtonWinXP(
    CDC* pDC,  
    CRect rect,  
    CMFCButton* pButton,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 [推送] 按鈕，這個周框。  
  
 [in] `pButton`  
 指標[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)物件來繪製。  
  
 [in] `uiState`  
 忽略。 狀態取自`pButton`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetbasethemecolora--cmfcvisualmanageroffice2003getbasethemecolor"></a><a name="getbasethemecolor"></a>CMFCVisualManagerOffice2003::GetBaseThemeColor  
 取得基底的佈景主題色彩。  
  
```  
virtual COLORREF GetBaseThemeColor();
```  
  
### <a name="return-value"></a>傳回值  
 傳回基底的主題，如果其中一個設定，佈景主題色彩列表面的色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethighlightmenuitemcolora--cmfcvisualmanageroffice2003gethighlightmenuitemcolor"></a><a name="gethighlightmenuitemcolor"></a>CMFCVisualManagerOffice2003::GetHighlightMenuItemColor  
 取得用於反白顯示的功能表項目的色彩。  
  
```  
virtual COLORREF GetHighlightMenuItemColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回反白顯示的功能表項目所使用的色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpropertygridgroupcolora--cmfcvisualmanageroffice2003getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManagerOffice2003::GetPropertyGridGroupColor  
 架構會呼叫這個方法，取得屬性清單的背景色彩。  
  
```  
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPropList`  
 繪製架構屬性清單的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回的背景色彩`pPropList`。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來自訂您的應用程式中的屬性清單的背景色彩。  
  
##  <a name="a-namegetpropertygridgrouptextcolora--cmfcvisualmanageroffice2003getpropertygridgrouptextcolor"></a><a name="getpropertygridgrouptextcolor"></a>CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor  
 架構會呼叫這個方法，以擷取的屬性清單的文字色彩。  
  
```  
virtual COLORREF GetPropertyGridGroupTextColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPropList`  
 屬性清單的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回指定的屬性清單的文字色彩。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來自訂您的應用程式中的屬性清單的文字色彩。  
  
##  <a name="a-namegetshowallmenuitemsheighta--cmfcvisualmanageroffice2003getshowallmenuitemsheight"></a><a name="getshowallmenuitemsheight"></a>CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight  
 傳回所有功能表項目高度。  
  
```  
virtual int GetShowAllMenuItemsHeight(
    CDC* pDC,  
    const CSize& sizeDefault);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `sizeDefault`  
 預設功能表大小。  
  
### <a name="return-value"></a>傳回值  
 根據預設，會傳回所有的功能表影像再加上邊界的高度。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetsmartdockingbaseguidecolorsa--cmfcvisualmanageroffice2003getsmartdockingbaseguidecolors"></a><a name="getsmartdockingbaseguidecolors"></a>CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors  
 設定指定的基底群組的背景色彩和框線色彩。  
  
```  
virtual void GetSmartDockingBaseGuideColors(
    COLORREF& clrBaseGroupBackground,  
    COLORREF& clrBaseGroupBorder);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrBaseGroupBackground`  
 若要參考[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)設定背景色彩。  
  
 [in] `clrBaseGroupBorder`  
 若要參考[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)設定框線色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetsmartdockinghighlighttonecolora--cmfcvisualmanageroffice2003getsmartdockinghighlighttonecolor"></a><a name="getsmartdockinghighlighttonecolor"></a>CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor  
 傳回反白顯示的色調色彩。  
  
```  
virtual COLORREF GetSmartDockingHighlightToneColor();
```  
  
### <a name="return-value"></a>傳回值  
 傳回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，其中包含醒目提示的色調色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabframecolorsa--cmfcvisualmanageroffice2003gettabframecolors"></a><a name="gettabframecolors"></a>CMFCVisualManagerOffice2003::GetTabFrameColors  
 必須擷取一組色彩繪製 索引標籤視窗時，架構會呼叫此函式。  
  
```  
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,  
    COLORREF& clrDark,  
    COLORREF& clrBlack,  
    COLORREF& clrHighlight,  
    COLORREF& clrFace,  
    COLORREF& clrDarkShadow,  
    COLORREF& clrLight,  
    CBrush*& pbrFace,  
    CBrush*& pbrBlack);
```  
  
### <a name="parameters"></a>參數  
 [in] `pTabWnd`  
 索引標籤式的視窗框架繪製索引標籤的指標。  
  
 [輸出] `clrDark`  
 參考[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，這個方法會儲存深色 索引標籤的框線色彩。  
  
 [輸出] `clrBlack`  
 參考`COLORREF`參數，此方法將儲存的索引標籤視窗的框線色彩。 框線的預設色彩是黑色。  
  
 [輸出] `clrHighlight`  
 參考`COLORREF`參數，這個方法會儲存反白顯示視窗的狀態 索引標籤的色彩。  
  
 [輸出] `clrFace`  
 參考`COLORREF`參數，這個方法會儲存的索引標籤 視窗的色彩。  
  
 [輸出] `clrDarkShadow`  
 參考`COLORREF`參數，這個方法會儲存索引標籤視窗的陰影的色彩。  
  
 [輸出] `clrLight`  
 參考`COLORREF`參數，此方法將儲存的淺色 索引標籤視窗邊緣的色彩。  
  
 [輸出] `pbrFace`  
 筆刷的參考指標。 此方法將儲存的筆刷，用來填滿 索引標籤 視窗中，此參數中的圖示。  
  
 [輸出] `pbrBlack`  
 筆刷的參考指標。 這個方法會儲存它使用來填滿 索引標籤 視窗中，此參數中的黑色邊緣的筆刷。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettoolbarcustomizebuttonmargina--cmfcvisualmanageroffice2003gettoolbarcustomizebuttonmargin"></a><a name="gettoolbarcustomizebuttonmargin"></a>CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin  
 取得邊界工具列的 [自訂] 按鈕。  
  
```  
virtual int GetToolBarCustomizeButtonMargin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回自訂工具列按鈕的邊界。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettoolbardisabledcolora--cmfcvisualmanageroffice2003gettoolbardisabledcolor"></a><a name="gettoolbardisabledcolor"></a>CMFCVisualManagerOffice2003::GetToolbarDisabledColor  
 取得工具列已停用的色彩。  
  
```  
virtual COLORREF GetToolbarDisabledColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，其中包含已停用的色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettooltipinfoa--cmfcvisualmanageroffice2003gettooltipinfo"></a><a name="gettooltipinfo"></a>CMFCVisualManagerOffice2003::GetToolTipInfo  
 若要取得工具提示資訊架構呼叫。  
  
```  
virtual BOOL GetToolTipInfo(
    CMFCToolTipInfo& params,  
    UINT nType = (UINT)(-1));
```  
  
### <a name="parameters"></a>參數  
 [輸出] `params`  
 參考[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)，這個方法會傳回工具提示資訊的物件。  
  
 [in] `nType`  
 輸入要傳回的工具提示資訊的資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果傳回工具提示資訊，以及`FALSE`否則。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdefaultwinxpcolorsenableda--cmfcvisualmanageroffice2003isdefaultwinxpcolorsenabled"></a><a name="isdefaultwinxpcolorsenabled"></a>CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled  
 表示視覺管理員是否使用原生 Windows XP 的佈景主題色彩。  
  
```  
static BOOL IsDefaultWinXPColorsEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果視覺管理員會使用原生的顏色。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如需有關原生色彩的詳細資訊，請參閱[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](#setdefaultwinxpcolors)。  
  
##  <a name="a-nameisdockingtabhasbordera--cmfcvisualmanageroffice2003isdockingtabhasborder"></a><a name="isdockingtabhasborder"></a>CMFCVisualManagerOffice2003::IsDockingTabHasBorder  
 傳回目前的視覺管理員是否會繪製停駐和索引標籤式窗格周圍的框線。  
  
```  
virtual BOOL IsDockingTabHasBorder();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 visual manager 繪製框線窗格停駐和索引標籤。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameishighlightonenotetabsa--cmfcvisualmanageroffice2003ishighlightonenotetabs"></a><a name="ishighlightonenotetabs"></a>CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs  
 指出是否應該醒目提示 OneNote 索引標籤。  
  
```  
virtual BOOL IsHighlightOneNoteTabs() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisoffsetpressedbuttona--cmfcvisualmanageroffice2003isoffsetpressedbutton"></a><a name="isoffsetpressedbutton"></a>CMFCVisualManagerOffice2003::IsOffsetPressedButton  
 繪製工具列按鈕時，由框架呼叫。  
  
```  
virtual BOOL IsOffsetPressedButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 預設實作會傳回 `FALSE`。  
  
##  <a name="a-nameisstatusbarofficexplooka--cmfcvisualmanageroffice2003isstatusbarofficexplook"></a><a name="isstatusbarofficexplook"></a>CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook  
 指出是否有狀態列，以 Office XP 外觀。  
  
```  
static BOOL __stdcall IsStatusBarOfficeXPLook();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 傳回`TRUE`如果狀態列，以 Office XP 的外觀，或`FALSE`如果不是。  
  
##  <a name="a-nameistoolbarroundshapea--cmfcvisualmanageroffice2003istoolbarroundshape"></a><a name="istoolbarroundshape"></a>CMFCVisualManagerOffice2003::IsToolbarRoundShape  
 指出指定的工具列是否為圓形。  
  
```  
virtual BOOL IsToolbarRoundShape(CMFCToolBar* pToolBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pToolBar`  
 工具列有問題的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果工具列為圓形，或`FALSE`是否功能表列。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisuseglobalthemea--cmfcvisualmanageroffice2003isuseglobaltheme"></a><a name="isuseglobaltheme"></a>CMFCVisualManagerOffice2003::IsUseGlobalTheme  
 表示您的應用程式是否使用 Windows XP 主題。  
  
```  
static BOOL IsUseGlobalTheme();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果視覺管理員會使用 Windows XP 主題。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用方法[CMFCVisualManagerOffice2003::SetUseGlobalTheme](#setuseglobaltheme)變更是否您視覺管理員會使用 Windows XP 主題。  
  
##  <a name="a-nameiswindowsthemingsupporteda--cmfcvisualmanageroffice2003iswindowsthemingsupported"></a><a name="iswindowsthemingsupported"></a>CMFCVisualManagerOffice2003::IsWindowsThemingSupported  
 指出是否支援 Windows 佈景主題。  
  
```  
virtual BOOL IsWindowsThemingSupported() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`支援 Windows 佈景主題，則為或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawautohidebuttonbordera--cmfcvisualmanageroffice2003ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder  
 當它繪製自動隱藏按鈕的邊框時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectBounds`  
 大小和位置的 [自動隱藏] 按鈕。  
  
 [in] `rectBorderSize`  
 框線的大小。  
  
 [in] `pButton`  
 指標 [自動隱藏] 按鈕。 架構會繪製此按鈕的框線。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，如果您想要自訂的自動隱藏 按鈕的框線外觀。 根據預設，這個方法會填入您的應用程式的預設陰影色彩的一般框線。  
  
 `rectBorderSize`參數不包含外框的座標。 它包含的框線大小`top`， `bottom`， `left`，和`right`資料成員。 值小於或等於 0 表示沒有 [自動隱藏] 按鈕的那一端上的框線。  
  
##  <a name="a-nameondrawbargrippera--cmfcvisualmanageroffice2003ondrawbargripper"></a><a name="ondrawbargripper"></a>CMFCVisualManagerOffice2003::OnDrawBarGripper  
 當它繪製控制項 bar 移駐夾，由架構呼叫。  
  
```  
virtual void OnDrawBarGripper(
    CDC* pDC,  
    CRect rectGripper,  
    BOOL bHorz,  
    CBasePane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 控制列的裝置內容指標。  
  
 [in] `rectGripper`  
 控制列，這個周框。  
  
 [in] `bHorz`  
 布林值的參數，指定是否以水平或垂直方式將停駐控制列。  
  
 [in] `pBar`  
 控制列指標。 視覺化管理員繪製此控制項列的移駐夾。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會顯示標準的移駐夾。 若要自訂的移駐夾外觀，覆寫這個方法中的自訂類別衍生自[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)類別。  
  
##  <a name="a-nameondrawbrowsebuttona--cmfcvisualmanageroffice2003ondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCVisualManagerOffice2003::OnDrawBrowseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    CMFCEditBrowseCtrl* pEdit,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `rect`  
 [in] `pEdit`  
 [in] `state`  
 [in] `clrText`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawbuttonbordera--cmfcvisualmanageroffice2003ondrawbuttonborder"></a><a name="ondrawbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawButtonBorder  
 當它繪製工具列按鈕的框線，架構會呼叫這個方法。  
  
```  
virtual void OnDrawButtonBorder(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 工具列按鈕的裝置內容的指標。  
  
 [in] `pButton`  
 指標，工具列按鈕。 架構會繪製這個按鈕的框線。  
  
 [in] `rect`  
 指定的工具列按鈕的界限的矩形。  
  
 [in] `state`  
 列舉的資料型別指定的工具列按鈕的目前狀態。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會顯示標準的框線。 覆寫這個方法在衍生的視覺管理員，以自訂的工具列按鈕的框線外觀。  
  
 可能的工具列按鈕的狀態為`ButtonsIsRegular`， `ButtonsIsPressed`，或`ButtonsIsHighlighted`。  
  
##  <a name="a-nameondrawcaptionbarbordera--cmfcvisualmanageroffice2003ondrawcaptionbarborder"></a><a name="ondrawcaptionbarborder"></a>CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder  
 架構會呼叫這個方法時它繪製的框線[CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)物件。  
  
```  
virtual void OnDrawCaptionBarBorder(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect,  
    COLORREF clrBarBorder,  
    BOOL bFlatBorder);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pBar`  
 指標[CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)物件。 架構會繪製此標題列。  
  
 [in] `rect`  
 指定的標題列界限的矩形。  
  
 [in] `clrBarBorder`  
 框線的色彩。  
  
 [in] `bFlatBorder`  
 `TRUE`如果框線應該具有一般、 2D 外觀，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 自訂標題列的框線外觀的衍生類別中，這個方法會覆寫。  
  
##  <a name="a-nameondrawcheckboxexa--cmfcvisualmanageroffice2003ondrawcheckboxex"></a><a name="ondrawcheckboxex"></a>CMFCVisualManagerOffice2003::OnDrawCheckBoxEx  
 繪製核取方塊時，由架構呼叫。  
  
```  
virtual void OnDrawCheckBoxEx(
    CDC* pDC,  
    CRect rect,  
    int nState,  
    BOOL bHighlighted,  
    BOOL bPressed,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 核取方塊，這個周框。  
  
 [in] `nState`  
 核取方塊的狀態︰ 0，如果未選取，1，表示核取狀態，2 如果已核取 混合。  
  
 [in] `bHighlighted`  
 `TRUE`如果核取方塊，會反白顯示，或`FALSE`如果不是。  
  
 [in] `bPressed`  
 `TRUE`如果按下核取方塊時，或`FALSE`如果不是。  
  
 [in] `bEnabled`  
 `TRUE`如果已啟用 核取方塊，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawcombobordera--cmfcvisualmanageroffice2003ondrawcomboborder"></a><a name="ondrawcomboborder"></a>CMFCVisualManagerOffice2003::OnDrawComboBorder  
 它繪製的框線的執行個體時，架構會呼叫這個方法[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
```  
virtual void OnDrawComboBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 下拉式方塊按鈕的裝置內容指標。  
  
 [in] `rect`  
 指定下拉式方塊按鈕的界限的矩形。  
  
 [in] `bDisabled`  
 布林值的參數，指出下拉式方塊按鈕是否為無法使用。  
  
 [in] `bIsDropped`  
 布林值的參數，指出下拉式方塊是否落下。  
  
 [in] `bIsHighlighted`  
 布林值的參數，指出下拉式方塊按鈕會反白顯示。  
  
 [in] `pButton`  
 指標`CMFCToolBarComboBoxButton`物件。 架構會繪製此下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，在您衍生的視覺管理員，以自訂下拉式方塊的框線外觀。  
  
##  <a name="a-nameondrawcombodropbuttona--cmfcvisualmanageroffice2003ondrawcombodropbutton"></a><a name="ondrawcombodropbutton"></a>CMFCVisualManagerOffice2003::OnDrawComboDropButton  
 它會繪製的下拉式按鈕時，架構會呼叫這個方法[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
```  
virtual void OnDrawComboDropButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定下拉式按鈕的界限的矩形。  
  
 [in] `bDisabled`  
 布林值的參數，指出下拉式按鈕是否為無法使用。  
  
 [in] `bIsDropped`  
 布林值的參數，指出下拉式方塊是否落下。  
  
 [in] `bIsHighlighted`  
 布林值的參數，表示下拉式按鈕會反白顯示。  
  
 [in] `pButton`  
 指標`CMFCToolBarComboBoxButton`物件。 架構繪製此下拉式方塊按鈕的下拉式按鈕  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在您衍生的視覺管理員自訂下拉式按鈕的下拉式方塊按鈕的外觀。  
  
##  <a name="a-nameondrawcontrolbordera--cmfcvisualmanageroffice2003ondrawcontrolborder"></a><a name="ondrawcontrolborder"></a>CMFCVisualManagerOffice2003::OnDrawControlBorder  
 當它繪製控制項的框線，架構會呼叫這個方法。  
  
```  
virtual void OnDrawControlBorder(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndCtrl`  
 指標[CWnd 類別](../../mfc/reference/cwnd-class.md)物件，表示要繪製框線的控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawexpandingboxa--cmfcvisualmanageroffice2003ondrawexpandingbox"></a><a name="ondrawexpandingbox"></a>CMFCVisualManagerOffice2003::OnDrawExpandingBox  
 繪製展開的方塊時，由框架呼叫。  
  
```  
virtual void OnDrawExpandingBox(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsOpened,  
    COLORREF colorBox);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 要繪製展開的方塊顯示內容的指標。  
  
 [in] `rect`  
 要繪製展開的方塊，這個周框。  
  
 [in] `bIsOpened`  
 `TRUE`若要繪製方塊開啟時，或`FALSE`如果不是。  
  
 [in] `colorBox`  
 要繪製方塊的外框色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawheaderctrlbordera--cmfcvisualmanageroffice2003ondrawheaderctrlborder"></a><a name="ondrawheaderctrlborder"></a>CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder  
 它繪製的框線的執行個體時，架構會呼叫這個方法[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)。  
  
```  
virtual void OnDrawHeaderCtrlBorder(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect& rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCtrl`  
 指標[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)物件。 架構會繪製此標頭控制項的框線。  
  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定標頭控制項的界限的矩形。  
  
 [in] `bIsPressed`  
 [in] `bIsHighlighted`  
 布林值的參數，指出是否已按下標題控制項。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂標頭控制項的框線。  
  
##  <a name="a-nameondrawmenubordera--cmfcvisualmanageroffice2003ondrawmenuborder"></a><a name="ondrawmenuborder"></a>CMFCVisualManagerOffice2003::OnDrawMenuBorder  
 架構會呼叫這個方法時它繪製的框線[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)。  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCPopu* pMenu,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件。  
  
 [in] `pMenu`  
 指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件。 架構會繪製框線這個快顯功能表。  
  
 [in] `rect`  
 指定的快顯功能表界限的矩形。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會顯示標準功能表的邊框。 覆寫這個方法在衍生的視覺管理員，以自訂功能表框線的外觀。  
  
##  <a name="a-nameondrawoutlookbarsplittera--cmfcvisualmanageroffice2003ondrawoutlookbarsplitter"></a><a name="ondrawoutlookbarsplitter"></a>CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter  
 它繪製為 outlook 功能區分割時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawOutlookBarSplitter(
    CDC* pDC,  
    CRect rectSplitter);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectSplitter`  
 指定的分隔器界限的矩形。  
  
### <a name="remarks"></a>備註  
 自訂 outlook 功能區上的分隔器外觀的衍生視覺管理員中，這個方法會覆寫。  
  
##  <a name="a-nameondrawoutlookpagebuttonbordera--cmfcvisualmanageroffice2003ondrawoutlookpagebuttonborder"></a><a name="ondrawoutlookpagebuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder  
 當它繪製框線的 Outlook 頁 按鈕時，由架構呼叫。  
  
```  
virtual void OnDrawOutlookPageButtonBorder(
    CDC* pDC,  
    CRect& rectBtn,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectBtn`  
 指定的界限 Outlook 頁 按鈕的矩形。  
  
 [in] `bIsHighlighted`  
 布林值，指定 [] 按鈕會反白顯示。  
  
 [in] `bIsPressed`  
 布林值，指定是否按下按鍵時。  
  
### <a name="remarks"></a>備註  
 若要變更的 Outlook 頁按鈕外觀的自訂視覺管理員中，這個方法會覆寫。  
  
##  <a name="a-nameondrawpanebordera--cmfcvisualmanageroffice2003ondrawpaneborder"></a><a name="ondrawpaneborder"></a>CMFCVisualManagerOffice2003::OnDrawPaneBorder  
 架構會呼叫這個方法時它繪製的框線[CPane 類別](../../mfc/reference/cpane-class.md)物件。  
  
```  
virtual void OnDrawPaneBorder(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的控制列的指標。  
  
 [in] `pBar`  
 窗格的指標。 視覺化管理員繪製此窗格框線。  
  
 [in] `rect`  
 指出窗格的界限的矩形。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會顯示標準的框線。 覆寫這個方法在衍生的類別，即可自訂框線的外觀。  
  
##  <a name="a-nameondrawpanecaptiona--cmfcvisualmanageroffice2003ondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManagerOffice2003::OnDrawPaneCaption  
 架構會呼叫這個方法時它繪製的標題[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)物件。  
  
```  
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,  
    CDockablePane* pBar,  
    BOOL bActive,  
    CRect rectCaption,  
    CRect rectButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pBar`  
 指標[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)物件。 架構會繪製此窗格的標題。  
  
 [in] `bActive`  
 布林值的參數，指示控制列是否為作用中。  
  
 [in] `rectCaption`  
 指定標題的界限的矩形。  
  
 [in] `rectButtons`  
 指定標題按鈕的界限的矩形。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，指出標題的文字色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawpopupwindowbordera--cmfcvisualmanageroffice2003ondrawpopupwindowborder"></a><a name="ondrawpopupwindowborder"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder  
 當它繪製框線的快顯視窗時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawPopupWindowBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的快顯視窗的指標。  
  
 [in] `rect`  
 快顯視窗，這個周框。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawpopupwindowbuttonbordera--cmfcvisualmanageroffice2003ondrawpopupwindowbuttonborder"></a><a name="ondrawpopupwindowbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder  
 它會在快顯視窗中繪製按鈕的框線時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawPopupWindowButtonBorder(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 按鈕的裝置內容的指標。  
  
 [in] `rectClient`  
 週框的按鈕。  
  
 [in] `pButton`  
 按鈕的指標 ( [CMFCDesktopAlertWndButton 類別](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)物件)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawpopupwindowcaptiona--cmfcvisualmanageroffice2003ondrawpopupwindowcaption"></a><a name="ondrawpopupwindowcaption"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption  
 當它繪製標題的快顯視窗時，架構會呼叫這個方法。  
  
```  
virtual COLORREF OnDrawPopupWindowCaption(
    CDC* pDC,  
    CRect rectCaption,  
    CMFCDesktopAlertWnd* pPopupWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 標題的裝置內容的指標。  
  
 [in] `rectCaption`  
 週框的標題。  
  
 [in] `pPopupWnd`  
 要繪製的標題為快顯視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 標題的文字色彩。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂快顯視窗標題的外觀。  
  
##  <a name="a-nameondrawribbonbuttonsgroupa--cmfcvisualmanageroffice2003ondrawribbonbuttonsgroup"></a><a name="ondrawribbonbuttonsgroup"></a>CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup  
 當它在功能區上繪製一組按鈕時，架構會呼叫這個方法。  
  
```  
virtual COLORREF OnDrawRibbonButtonsGroup(
    CDC* pDC,  
    CMFCRibbonButtonsGroup* pGroup,  
    CRect rectGroup);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pGroup`  
 功能區上的按鈕群組指標。 架構會繪製按鈕的此群組。  
  
 [in] `rectGroup`  
 指定的界限群組的矩形。  
  
### <a name="return-value"></a>傳回值  
 保留的值。 預設的實作會傳回 -1。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂一組功能區上的按鈕外觀。  
  
##  <a name="a-nameondrawribboncategorycaptiona--cmfcvisualmanageroffice2003ondrawribboncategorycaption"></a><a name="ondrawribboncategorycaption"></a>CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption  
 當它繪製功能區分類的標題列，架構會呼叫這個方法。  
  
```  
virtual COLORREF OnDrawRibbonCategoryCaption(
    CDC* pDC,  
    CMFCRibbonContextCaption* pContextCaption);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區類別的裝置內容指標。  
  
 [in] `pContextCaption`  
 標題列指標。 視覺化管理員繪製這[CMFCRibbonContextCaption 類別](../../mfc/reference/cmfcribboncontextcaption-class.md)。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，指出在標題列文字的色彩。  
  
### <a name="remarks"></a>備註  
 覆寫此方法來自訂功能區分類的標題列的外觀的衍生類別中。  
  
##  <a name="a-nameondrawribboncategorytaba--cmfcvisualmanageroffice2003ondrawribboncategorytab"></a><a name="ondrawribboncategorytab"></a>CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab  
 當它繪製為功能區類別目錄 索引標籤時，架構會呼叫這個方法。  
  
```  
virtual COLORREF OnDrawRibbonCategoryTab(
    CDC* pDC,  
    CMFCRibbonTab* pTab,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pTab`  
 功能區索引標籤上物件的指標。 架構會繪製此索引標籤。  
  
 [in] `bIsActive`  
 `TRUE`如果作用中 索引標籤或`FALSE`如果不是。  
  
### <a name="return-value"></a>傳回值  
 用於功能區類別目錄 索引標籤上的文字色彩。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂功能區類別目錄 索引標籤的外觀。  
  
##  <a name="a-nameondrawribbonprogressbara--cmfcvisualmanageroffice2003ondrawribbonprogressbar"></a><a name="ondrawribbonprogressbar"></a>CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar  
 架構會呼叫這個方法時，它會繪製[CMFCRibbonProgressBar 類別](../../mfc/reference/cmfcribbonprogressbar-class.md)物件。  
  
```  
virtual void OnDrawRibbonProgressBar(
    CDC* pDC,  
    CMFCRibbonProgressBar* pProgress,  
    CRect rectProgress,  
    CRect rectChunk,  
    BOOL bInfiniteMode);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pProgress`  
 指標[CMFCRibbonProgressBar 類別](../../mfc/reference/cmfcribbonprogressbar-class.md)物件。 架構會繪製這個進度列。  
  
 [in] `rectProgress`  
 指定進度列的界限的矩形。  
  
 [in] `rectChunk`  
 指定區域周圍的進度列的界限的矩形。  
  
 [in] `bInfiniteMode`  
 `TRUE`如果列在無限模式中，或`FALSE`如果不是。 預設實作不會使用這個參數。  
  
### <a name="remarks"></a>備註  
 這個方法來自訂外觀的進度列在衍生類別中覆寫  
  
##  <a name="a-nameondrawribbonquickaccesstoolbarseparatora--cmfcvisualmanageroffice2003ondrawribbonquickaccesstoolbarseparator"></a><a name="ondrawribbonquickaccesstoolbarseparator"></a>CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator  
 它會快速存取工具列功能區上繪製分隔符號時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawRibbonQuickAccessToolBarSeparator(
    CDC* pDC,  
    CMFCRibbonSeparator* pSeparator,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pSeparator`  
 指標[CMFCRibbonSeparator 類別](../../mfc/reference/cmfcribbonseparator-class.md)物件。 架構會繪製此功能區分隔符號。  
  
 [in] `rect`  
 指定的分隔符號界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫此方法來自訂功能區快速存取工具列上的分隔符號外觀的衍生類別中。  
  
##  <a name="a-nameondrawribbonsliderchannela--cmfcvisualmanageroffice2003ondrawribbonsliderchannel"></a><a name="ondrawribbonsliderchannel"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel  
 架構會呼叫這個方法時它繪製的色板[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)。  
  
```  
virtual void OnDrawRibbonSliderChannel(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pSlider`  
 指標[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)物件。 架構會繪製這個功能區滑桿的通道。  
  
 [in] `rect`  
 指定通道的功能區滑桿界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫此方法來自訂功能區滑桿的通道外觀的衍生類別中。  
  
##  <a name="a-nameondrawribbonsliderthumba--cmfcvisualmanageroffice2003ondrawribbonsliderthumb"></a><a name="ondrawribbonsliderthumb"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb  
 它繪製的捲動方塊時，架構會呼叫這個方法[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)物件  
  
```  
virtual void OnDrawRibbonSliderThumb(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pSlider`  
 指標[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)。 架構會繪製這個功能區滑桿的縮圖。  
  
 [in] `rect`  
 指定捲動方塊的功能區滑桿的界限的矩形。  
  
 [in] `bIsHighlighted`  
 布林值的參數，指出捲動方塊會反白顯示。  
  
 [in] `bIsPressed`  
 布林值的參數，指出是否按下縮圖。  
  
 [in] `bIsDisabled`  
 布林值的參數，指出是否無法使用捲動方塊。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂功能區滑桿的捲動方塊的外觀。  
  
##  <a name="a-nameondrawribbonsliderzoombuttona--cmfcvisualmanageroffice2003ondrawribbonsliderzoombutton"></a><a name="ondrawribbonsliderzoombutton"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton  
 當它繪製 [縮放] 按鈕時，架構會呼叫這個方法[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)物件。  
  
```  
virtual void OnDrawRibbonSliderZoomButton(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsZoomOut,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pSlider`  
 指標[CMFCRibbonSlider 類別](../../mfc/reference/cmfcribbonslider-class.md)物件。 架構會繪製此功能區滑桿。  
  
 [in] `rect`  
 指定在功能區滑桿的 [縮放] 按鈕的界限的矩形。  
  
 [in] `bIsZoomOut`  
 `TRUE`如果架構應繪製的左的按鈕 」 ** - **」 的縮小、 或`FALSE`如果架構應繪製與向右按鈕 」 ** + **"zoom 中。  
  
 [in] `bIsHighlighted`  
 布林值的參數，指出按鈕會反白顯示。  
  
 [in] `bIsPressed`  
 布林值的參數，指出是否按下按鍵時。  
  
 [in] `bIsDisabled`  
 布林值的參數，指出是否無法使用 按鈕。  
  
### <a name="remarks"></a>備註  
 根據預設，在功能區滑桿上的顯示比例按鈕都使用圓形** + **或** - **登入中央。 若要自訂顯示比例按鈕的外觀，覆寫這個方法在衍生的視覺管理員。  
  
##  <a name="a-nameondrawribbonstatusbarpanea--cmfcvisualmanageroffice2003ondrawribbonstatusbarpane"></a><a name="ondrawribbonstatusbarpane"></a>CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane  
 當它在狀態列上繪製一個窗格，架構會呼叫這個方法。  
  
```  
virtual COLORREF OnDrawRibbonStatusBarPane(
    CDC* pDC,  
    CMFCRibbonStatusBar* pBar,  
    CMFCRibbonStatusBarPane* pPane);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pBar`  
 包含窗格的 [狀態] 列指標。  
  
 [in] `pPane`  
 狀態列窗格的指標。 架構繪製這[CMFCRibbonStatusBarPane 類別](../../mfc/reference/cmfcribbonstatusbarpane-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 保留的值。 預設的實作會傳回 -1。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂狀態列窗格的外觀。  
  
##  <a name="a-nameondrawscrollbuttonsa--cmfcvisualmanageroffice2003ondrawscrollbuttons"></a><a name="ondrawscrollbuttons"></a>CMFCVisualManagerOffice2003::OnDrawScrollButtons  
 當它繪製捲動按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawScrollButtons(
    CDC* pDC,  
    const CRect& rect,  
    const int nBorderSize,  
    int iImage,  
    BOOL bHilited);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 捲軸按鈕，這個周框。  
  
 [in] `nBorderSize`  
 若要捲動按鈕周圍繪製框線的大小。  
  
 [in] `iImage`  
 若要在捲動按鈕中繪製影像的識別項。  
  
 [in] `bHilited`  
 `TRUE`如果捲動按鈕會反白顯示，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawseparatora--cmfcvisualmanageroffice2003ondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManagerOffice2003::OnDrawSeparator  
 當它繪製分隔符號時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rect,  
    BOOL bIsHoriz);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 控制列的裝置內容指標。  
  
 [in] `pBar`  
 包含分隔符號的窗格指標。  
  
 [in] `rect`  
 指定的分隔符號界限的矩形。  
  
 [in] `bIsHoriz`  
 `TRUE`如果水平停駐窗格或`FALSE`如果垂直停駐窗格。  
  
### <a name="remarks"></a>備註  
 控制列上使用分隔符號來分隔群組的相關圖示。 這個方法的預設實作會顯示標準的分隔符號。 覆寫這個方法在衍生的視覺管理員，以自訂分隔符號的外觀。  
  
##  <a name="a-nameondrawshowallmenuitemsa--cmfcvisualmanageroffice2003ondrawshowallmenuitems"></a><a name="ondrawshowallmenuitems"></a>CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems  
 它會繪製在功能表中的所有項目時，架構會呼叫這個方法  
  
```  
virtual void OnDrawShowAllMenuItems(
    CDC* pDC,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 要繪製功能表上，這個周框。  
  
 [in] `state`  
 按鈕的狀態。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawstatusbarpanebordera--cmfcvisualmanageroffice2003ondrawstatusbarpaneborder"></a><a name="ondrawstatusbarpaneborder"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder  
 架構會呼叫這個方法時它繪製的框線[CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)物件。  
  
```  
virtual void OnDrawStatusBarPaneBorder(
    CDC* pDC,  
    CMFCStatusBar* pBar,  
    CRect rectPane,  
    UINT uiID,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pBar`  
 指標[CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)物件。 架構會繪製此狀態列物件。  
  
 [in] `rectPane`  
 指定狀態列的界限的矩形。  
  
 [in] `uiID`  
 [狀態] 列的識別碼。  
  
 [in] `nStyle`  
 [狀態] 列的樣式。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂的框線外觀`CMFCStatusBar`物件。  
  
##  <a name="a-nameondrawstatusbarprogressa--cmfcvisualmanageroffice2003ondrawstatusbarprogress"></a><a name="ondrawstatusbarprogress"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarProgress  
 架構會呼叫這個方法時，它會在上繪製進度列指示器[CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)物件  
  
```  
virtual void OnDrawStatusBarProgress(
    CDC* pDC,  
    CMFCStatusBar* pStatusBar,  
    CRect rectProgress,  
    int nProgressTotal,  
    int nProgressCurr,  
    COLORREF clrBar,  
    COLORREF clrProgressBarDest,  
    COLORREF clrProgressText,  
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容中，[狀態] 列的指標  
  
 [in] `pStatusBar`  
 [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)物件，其中包含進度列。  
  
 [in] `rectProgress`  
 指定進度列的界限的矩形。  
  
 [in] `nProgressTotal`  
 進度列的總數。  
  
 [in] `nProgressCurr`  
 進度列目前的進度。  
  
 [in] `clrBar`  
 進度列的初始色彩。 值為色彩漸層的開始或完成的進度列色彩。  
  
 [in] `clrProgressBarDest`  
 [in] `clrProgressText`  
 [in] `bProgressText`  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂狀態列上的進度列的外觀。  
  
##  <a name="a-nameondrawstatusbarsizeboxa--cmfcvisualmanageroffice2003ondrawstatusbarsizebox"></a><a name="ondrawstatusbarsizebox"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox  
 架構會呼叫這個方法時它繪製大小方塊[CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)。  
  
```  
virtual void OnDrawStatusBarSizeBox(
    CDC* pDC,  
    CMFCStatusBar* pStatBar,  
    CRect rectSizeBox);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pStatBar`  
 狀態列指標。 架構會繪製此狀態列上的 [大小] 方塊。  
  
 [in] `rectSizeBox`  
 指定 [大小] 中的界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂狀態列上的 [大小] 方塊的外觀。  
  
##  <a name="a-nameondrawtaba--cmfcvisualmanageroffice2003ondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManagerOffice2003::OnDrawTab  
 它會繪製的索引標籤時，架構會呼叫這個方法[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。  
  
```  
virtual void OnDrawTab(
    CDC* pDC,  
    CRect rectTab,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectTab`  
 指定的索引標籤控制項界限的矩形。  
  
 [in] `iTab`  
 繪製架構 索引標籤的索引。  
  
 [in] `bIsActive`  
 布林值的參數，指定是否為作用中 索引標籤。  
  
 [in] `pTabWnd`  
 指標[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 架構會繪製這個索引標籤控制項。  
  
### <a name="remarks"></a>備註  
 A`CMFCBaseTabCtrl`物件時呼叫這個方法會處理`WM_PAINT`訊息。在衍生類別來自訂查詢 索引標籤中的，這個方法會覆寫。  
  
##  <a name="a-nameondrawtabsbuttonbordera--cmfcvisualmanageroffice2003ondrawtabsbuttonborder"></a><a name="ondrawtabsbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder  
 當它繪製框線的索引標籤 按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawTabsButtonBorder(
    CDC* pDC,  
    CRect& rect,  
    CMFCButton* pButton,  
    UINT uiState,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定的索引標籤 按鈕的界限的矩形。  
  
 [in] `pButton`  
 指標[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)架構，會繪製框線。  
  
 [in] `uiState`  
 按鍵的狀態 (請參閱[CButton::GetState](../../mfc/reference/cbutton-class.md#getstate))。  
  
 [in] `pWndTab`  
 父索引標籤視窗的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂索引標籤 按鈕的框線外觀。  
  
##  <a name="a-nameondrawtaska--cmfcvisualmanageroffice2003ondrawtask"></a><a name="ondrawtask"></a>CMFCVisualManagerOffice2003::OnDrawTask  
 架構會呼叫這個方法時，它會繪製[CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)物件。  
  
```  
virtual void OnDrawTask(
    CDC* pDC,  
    CMFCTasksPaneTask* pTask,  
    CImageList* pIcons,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pTask`  
 指標[CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)物件。 架構會繪製這項工作。  
  
 [in] `pIcons`  
 工作窗格與相關聯的影像清單的指標。 每個工作包含此清單中的映像的索引。  
  
 [in] `bIsHighlighted`  
 布林值的參數，指定是否要反白顯示的工作。  
  
 [in] `bIsSelected`  
 布林值的參數，指定是否要選取顯示的工作。  
  
### <a name="remarks"></a>備註  
 架構會顯示為圖示和文字的工作列上的工作。 `pIcons`參數包含所指示的工作圖示`pTask`。 自訂外觀，請在工作列上的工作在衍生類別中，這個方法會覆寫。  
  
##  <a name="a-nameondrawtasksgroupareabordera--cmfcvisualmanageroffice2003ondrawtasksgroupareaborder"></a><a name="ondrawtasksgroupareaborder"></a>CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder  
 架構會呼叫這個方法時，它會在上繪製一組周圍的框線[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)物件。  
  
```  
virtual void OnDrawTasksGroupAreaBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE,  
    BOOL bNoTitle = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 在工作窗格中指定的界限群組區域的矩形。  
  
 [in] `bSpecial`  
 布林值的參數會指定框線會反白顯示。 值為`TRUE`指出框線會反白顯示。  
  
 [in] `bNoTitle`  
 布林值的參數，指定群組區域是否有標題。 值為`TRUE`表示群組區域沒有標題。  
  
### <a name="remarks"></a>備註  
 若要自訂工作窗格上的群組區域周圍的框線在衍生類別中的這個函式會覆寫。  
  
##  <a name="a-nameondrawtasksgroupcaptiona--cmfcvisualmanageroffice2003ondrawtasksgroupcaption"></a><a name="ondrawtasksgroupcaption"></a>CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption  
 架構會呼叫這個方法時它繪製的標題[CMFCTasksPaneTaskGroup 類別](../../mfc/reference/cmfctaskspanetaskgroup-class.md)物件。  
  
```  
virtual void OnDrawTasksGroupCaption(
    CDC* pDC,  
    CMFCTasksPaneTaskGroup* pGroup,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE,  
    BOOL bCanCollapse = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pGroup`  
 指標[CMFCTasksPaneTaskGroup 類別](../../mfc/reference/cmfctaskspanetaskgroup-class.md)物件。 架構會繪製此群組的標題。  
  
 [in] `bIsHighlighted`  
 表示群組會反白顯示的布林參數。  
  
 [in] `bIsSelected`  
 布林值的參數，指出目前是否已選取的群組。  
  
 [in] `bCanCollapse`  
 布林值的參數，指出是否可摺疊群組。  
  
### <a name="remarks"></a>備註  
 這個方法來自訂標題的衍生類別中覆寫`CMFCTasksPaneTaskGroup`。  
  
##  <a name="a-nameondrawtearoffcaptiona--cmfcvisualmanageroffice2003ondrawtearoffcaption"></a><a name="ondrawtearoffcaption"></a>CMFCVisualManagerOffice2003::OnDrawTearOffCaption  
 架構會呼叫這個方法時它繪製的標題[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件。  
  
```  
virtual void OnDrawTearOffCaption(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定標題的界限的矩形。  
  
 [in] `bIsActive`  
 `TRUE`如果標題為使用中。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式時[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件處理程序`WM_PAINT`訊息，並必須繪製撕標題。  
  
 覆寫這個方法在衍生的類別，即可自訂撕列標題的外觀。  
  
##  <a name="a-nameonerasepopupwindowbuttona--cmfcvisualmanageroffice2003onerasepopupwindowbutton"></a><a name="onerasepopupwindowbutton"></a>CMFCVisualManagerOffice2003::OnErasePopupWindowButton  
 它會清除快顯視窗中的按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnErasePopupWindowButton(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectClient`  
 所指定的快顯視窗的工作區的矩形。  
  
 [in] `pButton`  
 指標 [清除] 按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonerasetabsareaa--cmfcvisualmanageroffice2003onerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManagerOffice2003::OnEraseTabsArea  
 它會清除 索引標籤的區域 索引標籤視窗時，架構會呼叫這個方法。  
  
```  
virtual void OnEraseTabsArea(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定的索引標籤區域界限的矩形。  
  
 [in] `pTabWnd`  
 索引標籤視窗的指標。 架構會清除指定的索引標籤視窗的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式時[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件處理程序`WM_PAINT`訊息，並清除 索引標籤區域。  
  
 覆寫這個方法在衍生的視覺管理員，以自訂索引標籤的外觀。  
  
##  <a name="a-nameonerasetabsbuttona--cmfcvisualmanageroffice2003onerasetabsbutton"></a><a name="onerasetabsbutton"></a>CMFCVisualManagerOffice2003::OnEraseTabsButton  
 它會清除文字和圖示的索引標籤 按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnEraseTabsButton(
    CDC* pDC,  
    CRect rect,  
    CMFCButton* pButton,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定的索引標籤 按鈕的界限的矩形。  
  
 [in] `pButton`  
 指向的索引標籤 按鈕。 架構會清除文字與圖示，此按鈕。  
  
 [in] `pWndTab`  
 包含索引標籤按鈕 索引標籤控制項的指標。  
  
### <a name="remarks"></a>備註  
 架構會清除文字和圖示的按鈕時[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件處理程序`WM_ERASEBKGND`訊息  
  
 覆寫這個方法在衍生的視覺管理員，以自訂索引標籤按鈕的外觀。  
  
##  <a name="a-nameonerasetabsframea--cmfcvisualmanageroffice2003onerasetabsframe"></a><a name="onerasetabsframe"></a>CMFCVisualManagerOffice2003::OnEraseTabsFrame  
 它會清除上的框架上時，架構會呼叫這個方法[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。  
  
```  
virtual BOOL OnEraseTabsFrame(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定的索引標籤視窗界限的矩形。  
  
 [in] `pTabWnd`  
 索引標籤視窗的指標。 這個架構會清除的框架[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 這個方法會填入所指示的區域`rect`與作用中的索引標籤的背景色彩。 它時，會呼叫`CMFCBaseTabCtrl`物件處理程序`WM_PAINT`訊息，並清除 [框架] 索引標籤。  
  
##  <a name="a-nameonfillautohidebuttonbackgrounda--cmfcvisualmanageroffice2003onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground  
 當它填入自動隱藏按鈕的背景時，架構會呼叫這個方法。  
  
```  
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,  
    CRect rect,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定 [自動隱藏] 按鈕的界限的矩形。  
  
 [in] `pButton`  
 指標[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)物件。 架構會填滿此自動隱藏按鈕的背景。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂自動隱藏 按鈕的外觀。  
  
##  <a name="a-nameonfillbarbackgrounda--cmfcvisualmanageroffice2003onfillbarbackground"></a><a name="onfillbarbackground"></a>CMFCVisualManagerOffice2003::OnFillBarBackground  
 架構會呼叫這個方法時的背景填滿[CBasePane 類別](../../mfc/reference/cbasepane-class.md)物件。  
  
```  
virtual void OnFillBarBackground(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rectClient,  
    CRect rectClip,  
    BOOL bNCArea = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 控制列的裝置內容指標。  
  
 [in] `pBar`  
 指標[CBasePane 類別](../../mfc/reference/cbasepane-class.md)物件。 架構會填滿此窗格的背景。  
  
 [in] `rectClient`  
 指定窗格的界限的矩形。  
  
 [in] `rectClip`  
 指定在窗格的裁剪區域的矩形。  
  
 [in] `bNCArea`  
 保留的值。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會填滿與全域變數 3d 的背景色彩列的背景`afxGlobalData`。  
  
 覆寫這個方法在衍生的視覺管理員，以自訂窗格的背景。  
  
##  <a name="a-nameonfillbuttoninteriora--cmfcvisualmanageroffice2003onfillbuttoninterior"></a><a name="onfillbuttoninterior"></a>CMFCVisualManagerOffice2003::OnFillButtonInterior  
 工具列按鈕的背景填滿時，架構會呼叫這個方法。  
  
```  
virtual void OnFillButtonInterior(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 工具列按鈕的裝置內容的指標。  
  
 [in] `pButton`  
 指標的填滿架構背景的按鈕。  
  
 [in] `rect`  
 指定的工具列按鈕的界限的矩形。  
  
 [in] `state`  
 工具列按鈕的狀態 (可能的工具列按鈕的狀態為`ButtonsIsRegular`， `ButtonsIsPressed`，或`ButtonsIsHighlighted`)。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會使用預設色彩背景填滿。 覆寫這個方法在衍生的視覺管理員，以自訂工具列按鈕的背景。  
  
##  <a name="a-nameonfillcommandslistbackgrounda--cmfcvisualmanageroffice2003onfillcommandslistbackground"></a><a name="onfillcommandslistbackground"></a>CMFCVisualManagerOffice2003::OnFillCommandsListBackground  
 屬於命令清單的工具列按鈕的背景填滿時，架構會呼叫這個方法。 此命令的清單是自訂對話方塊的一部分。  
  
```  
virtual COLORREF OnFillCommandsListBackground(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定按鈕的界限的矩形。  
  
 [in] `bIsSelected`  
 布林值的參數，指出是否已選取 [] 按鈕。  
  
### <a name="return-value"></a>傳回值  
 工具列按鈕文字的色彩。  
  
### <a name="remarks"></a>備註  
 如需自訂清單的詳細資訊，請參閱[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。 這個方法的預設實作會填滿背景根據目前選取的面板的色彩配置。  
  
##  <a name="a-nameonfillheaderctrlbackgrounda--cmfcvisualmanageroffice2003onfillheaderctrlbackground"></a><a name="onfillheaderctrlbackground"></a>CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground  
 標頭控制項的背景填滿時，架構會呼叫這個方法。  
  
```  
virtual void OnFillHeaderCtrlBackground(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCtrl`  
 指標[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)物件。 架構會填滿此標頭控制項的背景。  
  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定標頭控制項的界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂標頭控制項的外觀。  
  
##  <a name="a-nameonfillhighlightedareaa--cmfcvisualmanageroffice2003onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a>CMFCVisualManagerOffice2003::OnFillHighlightedArea  
 它填滿反白顯示的區域的工具列按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnFillHighlightedArea(
    CDC* pDC,  
    CRect rect,  
    CBrush* pBrush,  
    CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 反白顯示要填滿區域的周框矩形。  
  
 [in] `pBrush`  
 用於反白顯示的區域的填滿筆刷。  
  
 [in] `pButton`  
 指標[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件用來填滿反白顯示的區域。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfilloutlookbarcaptiona--cmfcvisualmanageroffice2003onfilloutlookbarcaption"></a><a name="onfilloutlookbarcaption"></a>CMFCVisualManagerOffice2003::OnFillOutlookBarCaption  
 當 Outlook 標題列的背景填滿時，架構會呼叫這個方法。  
  
```  
virtual void OnFillOutlookBarCaption(
    CDC* pDC,  
    CRect rectCaption,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectCaption`  
 指定的標題列界限的矩形。  
  
 [輸出] `clrText`  
 參考`COLORREF`物件，這個方法會寫入文字的色彩在標題列。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會填滿的標題列，以根據目前的面板的陰影的色彩。  
  
 覆寫這個方法在衍生的視覺管理員，以自訂 Outlook 的標題列的色彩。  
  
##  <a name="a-nameonfilloutlookpagebuttona--cmfcvisualmanageroffice2003onfilloutlookpagebutton"></a><a name="onfilloutlookpagebutton"></a>CMFCVisualManagerOffice2003::OnFillOutlookPageButton  
 它填滿內部 Outlook 頁 按鈕時，架構會呼叫這個方法。  
  
```  
virtual void OnFillOutlookPageButton(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定 Outlook 頁 按鈕的界限的矩形。  
  
 [in] `bIsHighlighted`  
 布林值參數來指定按鈕會反白顯示。  
  
 [in] `bIsPressed`  
 布林值的參數，指定是否按下按鍵時。  
  
 [輸出] `clrText`  
 參考`COLORREF`物件，這個方法會儲存於 outlook 按鈕的文字色彩。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式中的衍生的視覺管理員，以自訂 Outlook 按鈕的外觀。  
  
##  <a name="a-nameonfillpopupwindowbackgrounda--cmfcvisualmanageroffice2003onfillpopupwindowbackground"></a><a name="onfillpopupwindowbackground"></a>CMFCVisualManagerOffice2003::OnFillPopupWindowBackground  
 快顯視窗的背景填滿時，架構會呼叫這個方法。  
  
```  
virtual void OnFillPopupWindowBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定的快顯視窗界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂快顯視窗的外觀。  
  
##  <a name="a-nameonfilltaba--cmfcvisualmanageroffice2003onfilltab"></a><a name="onfilltab"></a>CMFCVisualManagerOffice2003::OnFillTab  
 填滿 索引標籤視窗的背景時，架構會呼叫這個方法。  
  
```  
virtual void OnFillTab(
    CDC* pDC,  
    CRect rectFill,  
    CBrush* pbrFill,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectFill`  
 指定的索引標籤視窗界限的矩形。  
  
 [in] `pbrFill`  
 架構使用填滿 索引標籤視窗的筆刷指標。  
  
 [in] `iTab`  
 以零為起始的索引標籤索引架構填滿背景索引標籤。  
  
 [in] `bIsActive`  
 `TRUE`如果使用中 索引標籤或`FALSE`如果不是。  
  
 [in] `pTabWnd`  
 父索引標籤控制項的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂索引標籤的外觀。  
  
##  <a name="a-nameonfilltasksgroupinteriora--cmfcvisualmanageroffice2003onfilltasksgroupinterior"></a><a name="onfilltasksgroupinterior"></a>CMFCVisualManagerOffice2003::OnFillTasksGroupInterior  
 架構會呼叫這個方法時它填滿內部[CMFCTasksPaneTaskGroup 類別](../../mfc/reference/cmfctaskspanetaskgroup-class.md)物件。  
  
```  
virtual void OnFillTasksGroupInterior(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 指定工作群組界限的矩形。  
  
 [in] `bSpecial`  
 布林值，指出內部會填入一個特殊的色彩。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂工作群組的外觀。  
  
##  <a name="a-nameonfilltaskspanebackgrounda--cmfcvisualmanageroffice2003onfilltaskspanebackground"></a><a name="onfilltaskspanebackground"></a>CMFCVisualManagerOffice2003::OnFillTasksPaneBackground  
 架構會呼叫這個方法時的背景填滿[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)控制項。  
  
```  
virtual void OnFillTasksPaneBackground(
    CDC* pDC,  
    CRect rectWorkArea);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectWorkArea`  
 指定的工作窗格界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂的外觀[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)物件。  
  
##  <a name="a-nameonhighlightquickcustomizemenubuttona--cmfcvisualmanageroffice2003onhighlightquickcustomizemenubutton"></a><a name="onhighlightquickcustomizemenubutton"></a>CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton  
 這個架構會呼叫這個方法，它會繪製反白顯示時快速自訂功能表按鈕。  
  
```  
virtual void OnHighlightQuickCustomizeMenuButton(
    CDC* pDC,  
    CMFCToolBarMenuButton* pButton,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 按鈕的裝置內容指標。  
  
 [in] `pButton`  
 按鈕指標。  
  
 [in] `rect`  
 [] 按鈕，這個周框。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonhighlightrarelyusedmenuitemsa--cmfcvisualmanageroffice2003onhighlightrarelyusedmenuitems"></a><a name="onhighlightrarelyusedmenuitems"></a>CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems  
 當它繪製反白顯示的功能表命令時，架構會呼叫這個方法。  
  
```  
virtual void OnHighlightRarelyUsedMenuItems(
    CDC* pDC,  
    CRect rectRarelyUsed);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectRarelyUsed`  
 指定反白顯示命令的界限的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生的視覺管理員，以自訂外觀反白顯示的功能表命令。  
  
##  <a name="a-nameonupdatesystemcolorsa--cmfcvisualmanageroffice2003onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManagerOffice2003::OnUpdateSystemColors  
 當系統色彩變更時，架構會呼叫此函式。  
  
```  
virtual void OnUpdateSystemColors();
```  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法處理一部分`WM_SYSCOLORCHANGE`訊息。 如果您想要在應用程式中的色彩變更時執行自訂程式碼，請覆寫這個方法在衍生的視覺管理員。  
  
##  <a name="a-namesetdefaultwinxpcolorsa--cmfcvisualmanageroffice2003setdefaultwinxpcolors"></a><a name="setdefaultwinxpcolors"></a>CMFCVisualManagerOffice2003::SetDefaultWinXPColors  
 指定視覺管理員應該使用原生的 Windows XP 佈景主題色彩或色彩取自[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。  
  
```  
static void SetDefaultWinXPColors(BOOL bDefaultWinXPColors = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDefaultWinXPColors`  
 指定是否視覺管理員會使用原生 Windows XP 的色彩。  
  
### <a name="remarks"></a>備註  
 如果`bDefaultWinXPColors`是`TRUE`，視覺管理員將會使用原生的 Windows XP 色彩，例如藍色、 橄欖色或銀卡。 否則，視覺管理員會使用取自色彩`GetSysColor`。 使用視覺項目，例如視覺管理員`COLOR_3DFACE`， `COLOR_3DSHADOW`， `COLOR_3DHIGHLIGHT`， `COLOR_3DDKSHADOW`，和`COLOR_3DLIGHT`。  
  
 根據預設，`CMFCVisualManagerOffice2003`物件會使用原生的 Windows XP 佈景主題色彩。  
  
##  <a name="a-namesetstatusbarofficexplooka--cmfcvisualmanageroffice2003setstatusbarofficexplook"></a><a name="setstatusbarofficexplook"></a>CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook  
 指定應該使用 Windows XP 全域主題。  
  
```  
static void __stdcall SetStatusBarOfficeXPLook(BOOL bStatusBarOfficeXPLook = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStatusBarOfficeXPLook`  
 `TRUE`如果要將 Windows XP 全域主題 （預設值），或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetuseglobalthemea--cmfcvisualmanageroffice2003setuseglobaltheme"></a><a name="setuseglobaltheme"></a>CMFCVisualManagerOffice2003::SetUseGlobalTheme  
 指定視覺管理員是否使用全域主題。  
  
```  
static void SetUseGlobalTheme(BOOL bUseGlobalTheme = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bUseGlobalTheme`  
 `TRUE`如果您想要使用全域主題; 的視覺管理員`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 如果`CMFCVisualManagerOffice2003`物件會使用全域主題，它會藉由繪製 GUI 元素[CMFCVisualManagerWindows 類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)。  
  
 如果`CMFCVisualManagerOffice2003`物件不會使用全域主題，它會藉由繪製 GUI 元素[CMFCVisualManagerOfficeXP 類別](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP 類別](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows 類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

