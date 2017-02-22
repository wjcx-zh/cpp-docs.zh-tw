---
title: "CMFCVisualManagerOffice2003 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerOffice2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerOffice2003 class"
ms.assetid: 115482cd-e349-450a-8dc4-c6023d092aab
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCVisualManagerOffice2003 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerOffice2003` 給應用程式的 Microsoft Office 2003 的外觀。  
  
## 語法  
  
```  
class CMFCVisualManagerOffice2003 : public CMFCVisualManagerOfficeXP  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCVisualManagerOffice2003::DrawComboBorderWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboBorderWinXP.md)|使用目前的 Windows XP 主題，分割下拉式方塊框線。  覆寫 \( [CMFCVisualManager::DrawComboBorderWinXP](../Topic/CMFCVisualManager::DrawComboBorderWinXP.md)\)。|  
|[CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP.md)|使用目前的 Windows XP 主題，繪製下拉式方塊下拉式按鈕。  覆寫 \( [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md)\)。|  
|[CMFCVisualManagerOffice2003::DrawCustomizeButton](../Topic/CMFCVisualManagerOffice2003::DrawCustomizeButton.md)|繪製自訂按鈕。|  
|[CMFCVisualManagerOffice2003::DrawPushButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawPushButtonWinXP.md)|使用目前的 Windows XP 主題，繪製按鈕。  覆寫 \( [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md)\)。|  
|[CMFCVisualManagerOffice2003::GetBaseThemeColor](../Topic/CMFCVisualManagerOffice2003::GetBaseThemeColor.md)|取得基礎佈景主題色彩。|  
|[CMFCVisualManagerOffice2003::GetHighlightMenuItemColor](../Topic/CMFCVisualManagerOffice2003::GetHighlightMenuItemColor.md)|取得色彩用於反白顯示功能表項目。|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md)|架構會呼叫這個方法會取得屬性清單的背景色彩。  覆寫 \( `CMFCVisualManagerOfficeXP::GetPropertyGridGroupColor`\)。|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor.md)|架構會呼叫這個方法會擷取屬性清單的文字色彩。  覆寫 \( `CMFCVisualManagerOfficeXP::GetPropertyGridGroupTextColor`\)。|  
|[CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight.md)|傳回以表示功能表項目。  覆寫 \( [CMFCVisualManager::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManager::GetShowAllMenuItemsHeight.md)\)。|  
|[CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors.md)|設定指定的基底群組背景色彩、框線色彩。  覆寫 \( `CMFCVisualManagerOfficeXP::GetSmartDockingBaseGuideColors`\)。|  
|[CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor.md)|取得反白顯示音色。  覆寫 \( [CMFCVisualManager::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManager::GetSmartDockingHighlightToneColor.md)\)。|  
|[CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md)|在必須擷取一組繪製索引標籤視窗時，色彩架構呼叫此函式。  覆寫 \( [CMFCVisualManager::GetTabFrameColors](../Topic/CMFCVisualManager::GetTabFrameColors.md)\)。|  
|[CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin](../Topic/CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin.md)|取得工具列自訂按鈕的框線。  覆寫 \( `CMFCVisualManager::GetToolBarCustomizeButtonMargin`\)。|  
|[CMFCVisualManagerOffice2003::GetToolbarDisabledColor](../Topic/CMFCVisualManagerOffice2003::GetToolbarDisabledColor.md)|取得工具列的停用的色彩。  覆寫 \( `CMFCVisualManager::GetToolbarDisabledColor`\)。|  
|[CMFCVisualManagerOffice2003::GetToolTipInfo](../Topic/CMFCVisualManagerOffice2003::GetToolTipInfo.md)|由架構呼叫以取得工具提示資訊。  覆寫 \( [CMFCVisualManager::GetToolTipInfo](../Topic/CMFCVisualManager::GetToolTipInfo.md)\)。|  
|[CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled](../Topic/CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled.md)|表示視覺管理員是否使用原生 Windows XP 佈景主題色彩。|  
|[CMFCVisualManagerOffice2003::IsDockingTabHasBorder](../Topic/CMFCVisualManagerOffice2003::IsDockingTabHasBorder.md)|傳回目前視覺化管理員是否已內建和的索引窗格的框線。  覆寫 \( [CMFCVisualManager::IsDockingTabHasBorder](../Topic/CMFCVisualManager::IsDockingTabHasBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs](../Topic/CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs.md)|指示是否應該反白顯示 OneNote 選項。  覆寫 \( `CMFCVisualManager::IsHighlightOneNoteTabs`\)。|  
|[CMFCVisualManagerOffice2003::IsOffsetPressedButton](../Topic/CMFCVisualManagerOffice2003::IsOffsetPressedButton.md)|由架構呼叫時，繪製工具列按鈕時。  覆寫 \( `CMFCVisualManager::IsOffsetPressedButton`\)。|  
|[CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook.md)|指示是否有與 Office XP 外觀的狀態列。|  
|[CMFCVisualManagerOffice2003::IsToolbarRoundShape](../Topic/CMFCVisualManagerOffice2003::IsToolbarRoundShape.md)|指示指定的工具列是否有圓形。  覆寫 \( [CMFCVisualManager::IsToolbarRoundShape](../Topic/CMFCVisualManager::IsToolbarRoundShape.md)\)。|  
|[CMFCVisualManagerOffice2003::IsUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::IsUseGlobalTheme.md)|表示是否使用全域 Windows XP 主題。|  
|[CMFCVisualManagerOffice2003::IsWindowsThemingSupported](../Topic/CMFCVisualManagerOffice2003::IsWindowsThemingSupported.md)|指示佈景主題的視窗是否支援。  覆寫 \( [CMFCVisualManager::IsWindowsThemingSupported](../Topic/CMFCVisualManager::IsWindowsThemingSupported.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md)|會將自動隱藏按鈕的框線時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManager::OnDrawAutoHideButtonBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawBarGripper](../Topic/CMFCVisualManagerOffice2003::OnDrawBarGripper.md)|由架構呼叫時，繪製控制列的移駐夾。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawBarGripper`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawBrowseButton](../Topic/CMFCVisualManagerOffice2003::OnDrawBrowseButton.md)|則繪製編輯控制項時，瀏覽按鈕架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawButtonBorder.md)|則繪製工具列按鈕的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder.md)|當它除以 [CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md) 物件的框線時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawCaptionBarBorder](../Topic/CMFCVisualManager::OnDrawCaptionBarBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerOffice2003::OnDrawCheckBoxEx.md)|則繪製核取方塊時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawComboBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawComboBorder.md)|包含在 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) 物件附近時，繪製框線架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawComboBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawComboDropButton](../Topic/CMFCVisualManagerOffice2003::OnDrawComboDropButton.md)|則繪製 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)的下拉按鈕時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawControlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawControlBorder.md)|會將控制項的框線時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawExpandingBox](../Topic/CMFCVisualManagerOffice2003::OnDrawExpandingBox.md)|則繪製展開的方塊時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder.md)|包含在 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)的執行個體時，周圍繪製框線架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawMenuBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawMenuBorder.md)|當它除以 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter.md)|則繪製 Outlook 時，分隔器架構呼叫這個方法。  覆寫 \([CMFCVisualManager::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManager::OnDrawOutlookBarSplitter.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder.md)|由架構呼叫，以便區分 Outlook 頁面按鈕的框線。  覆寫 \( [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneBorder.md)|當它除以 [CPane Class](../../mfc/reference/cpane-class.md) 物件的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md)|則繪製 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 物件時，標題架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder.md)|則繪製快顯視窗的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawPopupWindowBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder.md)|則繪製一個按鈕的框線在快顯視窗時，這個架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption.md)|則繪製快顯視窗的標題時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawPopupWindowCaption`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup.md)|則繪製按鈕群組在功能區上的時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManager::OnDrawRibbonButtonsGroup.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption.md)|則繪製功能區類別中的時，標題列架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManager::OnDrawRibbonCategoryCaption.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab.md)|則繪製功能區類別的選項時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar.md)|則繪製 [CMFCRibbonProgressBar Class](../../mfc/reference/cmfcribbonprogressbar-class.md)時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator.md)|則繪製功能區快速存取工具列時，分隔符號架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawRibbonQuickAccessToolBarSeparator`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel.md)|則繪製 [CMFCRibbonSlider Class](../../mfc/reference/cmfcribbonslider-class.md)的通道時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb.md)|則繪製 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) 物件的指標時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton.md)|則繪製 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) 物件時，縮放按鈕架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane.md)|則繪製在狀態列時，執行窗格架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawRibbonStatusBarPane`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawScrollButtons](../Topic/CMFCVisualManagerOffice2003::OnDrawScrollButtons.md)|則繪製按鈕時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md)|則繪製分隔符號時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawSeparator`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems](../Topic/CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems.md)|則繪製功能表時，中的所有項目架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawShowAllMenuItems](../Topic/CMFCVisualManager::OnDrawShowAllMenuItems.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder.md)|當它除以 [CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md) 物件的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarProgress.md)|會以 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) 物件時，的進度指示器架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox.md)|則繪製 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)的大小時，控制項的架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md)\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md)|則繪製 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 物件的選項時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTab`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder.md)|則繪製選項按鈕的框線時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTask](../Topic/CMFCVisualManagerOffice2003::OnDrawTask.md)|則繪製 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md) 物件時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTask`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder.md)|包含在 [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md) 物件時，一組框線架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption.md)|則繪製 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md) 物件的標頭時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`\)。|  
|[CMFCVisualManagerOffice2003::OnDrawTearOffCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTearOffCaption.md)|則繪製 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 物件的標頭時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`\)。|  
|[CMFCVisualManagerOffice2003::OnErasePopupWindowButton](../Topic/CMFCVisualManagerOffice2003::OnErasePopupWindowButton.md)|會清除在快顯視窗時，中的按鈕時由架構呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`\)。|  
|[CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md)|會清除選項視窗的索引標籤區域時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnEraseTabsArea`\)。|  
|[CMFCVisualManagerOffice2003::OnEraseTabsButton](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsButton.md)|會清除選項按鈕的文字和圖示時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnEraseTabsButton`\)。|  
|[CMFCVisualManagerOffice2003::OnEraseTabsFrame](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsFrame.md)|會清除在 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)時，的框架架構呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md)\)。|  
|[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md)|會填入自動隱藏按鈕的背景時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManager::OnFillAutoHideButtonBackground.md)\)。|  
|[CMFCVisualManagerOffice2003::OnFillBarBackground](../Topic/CMFCVisualManagerOffice2003::OnFillBarBackground.md)|會填入 [CBasePane Class](../../mfc/reference/cbasepane-class.md) 物件背景時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillBarBackground`\)。|  
|[CMFCVisualManagerOffice2003::OnFillButtonInterior](../Topic/CMFCVisualManagerOffice2003::OnFillButtonInterior.md)|會填入工具列按鈕的背景時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillButtonInterior`\)。|  
|[CMFCVisualManagerOffice2003::OnFillCommandsListBackground](../Topic/CMFCVisualManagerOffice2003::OnFillCommandsListBackground.md)|架構會呼叫這個方法，以填入屬於命令工具列按鈕的背景時。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`\)。|  
|[CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground.md)|會填入標題控制項的背景時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManager::OnFillHeaderCtrlBackground.md)\)。|  
|[CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md)|會填入工具列按鈕的反白區域時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillHighlightedArea`\)。|  
|[CMFCVisualManagerOffice2003::OnFillOutlookBarCaption](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookBarCaption.md)|會填入 Outlook 視窗標題列的背景色彩時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnFillOutlookBarCaption](../Topic/CMFCVisualManager::OnFillOutlookBarCaption.md)\)。|  
|[CMFCVisualManagerOffice2003::OnFillOutlookPageButton](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookPageButton.md)|會填入 Outlook 頁面按鈕的內部時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md)\)。|  
|[CMFCVisualManagerOffice2003::OnFillPopupWindowBackground](../Topic/CMFCVisualManagerOffice2003::OnFillPopupWindowBackground.md)|會填入快顯視窗的背景時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillPopupWindowBackground`\)。|  
|[CMFCVisualManagerOffice2003::OnFillTab](../Topic/CMFCVisualManagerOffice2003::OnFillTab.md)|會填入索引標籤視窗的背景時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillTab`\)。|  
|[CMFCVisualManagerOffice2003::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerOffice2003::OnFillTasksGroupInterior.md)|會填入 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md) 物件內時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`\)。|  
|[CMFCVisualManagerOffice2003::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerOffice2003::OnFillTasksPaneBackground.md)|會填入 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 控制項背景時，架構會呼叫這個方法。  覆寫 \( [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md)\)。|  
|[CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton](../Topic/CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton.md)|則繪製反白顯示的自訂功能表按鈕時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnHighlightQuickCustomizeMenuButton`\)。|  
|[CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems.md)|則繪製一個反白顯示的功能表命令時，架構會呼叫這個方法。  覆寫 \( `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`\)。|  
|[CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md)|當系統色彩變更時，架構會呼叫這個函式。  覆寫 \( `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`\)。|  
|[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](../Topic/CMFCVisualManagerOffice2003::SetDefaultWinXPColors.md)|指定視覺化管理員是否應該使用 [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)或色彩衍生的原生 Windows XP 佈景主題色彩。|  
|[CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook.md)|指定應該使用 Windows XP 主題。|  
|[CMFCVisualManagerOffice2003::SetUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::SetUseGlobalTheme.md)|指定視覺化管理員是否使用全域主題。|  
  
## 備註  
 您可以使用 `CMFCVisualManagerOffice2003` 類別變更應用程式的視覺外觀類似 Microsoft Office 2003。  
  
## 範例  
 下列範例示範如何設定 Office 2003 視覺化管理員。  這個程式碼片段是 [桌面警示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#6](../../mfc/reference/codesnippet/CPP/cmfcvisualmanageroffice2003-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
## 需求  
 **標題:** afxvisualmanageroffice2003.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)