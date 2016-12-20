---
title: "CMFCVisualManagerWindows Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerWindows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows class"
ms.assetid: 568b6e9e-8e67-4477-9a3d-2981cbd09861
caps.latest.revision: 46
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerWindows Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在使用者選取 Windows XP 或 Windows Vista 佈景主題時，`CMFCVisualManagerWindows` 模仿 Microsoft Windows XP 或 Microsoft Vista 隨即出現。  
  
## 語法  
  
```  
class CMFCVisualManagerWindows : public CMFCVisualManagerOfficeXP  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCVisualManagerWindows::CMFCVisualManagerWindows`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCVisualManagerWindows::AlwaysHighlight3DTabs](../Topic/CMFCVisualManagerWindows::AlwaysHighlight3DTabs.md)|架構會呼叫這個方法會決定是否在應用程式應該一律 3D 反白顯示索引標籤。  \(覆寫 [CMFCVisualManager::AlwaysHighlight3DTabs](../Topic/CMFCVisualManager::AlwaysHighlight3DTabs.md)\)。|  
|[CMFCVisualManagerWindows::DrawComboBorderWinXP](../Topic/CMFCVisualManagerWindows::DrawComboBorderWinXP.md)|\(覆寫 `CMFCVisualManager::DrawComboBorderWinXP`\)。|  
|[CMFCVisualManagerWindows::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawComboDropButtonWinXP.md)|\(覆寫 [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md)\)。|  
|[CMFCVisualManagerWindows::DrawPushButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawPushButtonWinXP.md)|\(覆寫 [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md)\)。|  
|[CMFCVisualManagerWindows::GetButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetButtonExtraBorder.md)|在繪製工具列按鈕時，架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::GetButtonExtraBorder](../Topic/CMFCVisualManager::GetButtonExtraBorder.md)\)。|  
|[CMFCVisualManagerWindows::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetCaptionButtonExtraBorder.md)|\(覆寫 [CMFCVisualManager::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManager::GetCaptionButtonExtraBorder.md)\)。|  
|[CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight](../Topic/CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight.md)|\(覆寫 `CMFCVisualManager::GetDockingPaneCaptionExtraHeight`\)。|  
|[CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor](../Topic/CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor.md)|\(覆寫 `CMFCVisualManagerOfficeXP::GetHighlightedMenuItemTextColor`\)。|  
|[CMFCVisualManagerWindows::GetPopupMenuGap](../Topic/CMFCVisualManagerWindows::GetPopupMenuGap.md)|\(覆寫 `CMFCVisualManagerOfficeXP::GetPopupMenuGap`\)。|  
|[CMFCVisualManagerWindows::GetToolbarButtonTextColor](../Topic/CMFCVisualManagerWindows::GetToolbarButtonTextColor.md)|\(覆寫 `CMFCVisualManagerOfficeXP::GetToolbarButtonTextColor`\)。|  
|[CMFCVisualManagerWindows::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManagerWindows::IsDefaultWinXPPopupButton.md)|\(覆寫 [CMFCVisualManager::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManager::IsDefaultWinXPPopupButton.md)\)。|  
|[CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md)|\(覆寫 `CMFCVisualManagerOfficeXP::IsHighlightWholeMenuItem`\)。|  
|[CMFCVisualManagerWindows::IsOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeStyleMenus.md)||  
|[CMFCVisualManagerWindows::IsOfficeXPStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeXPStyleMenus.md)|表示視覺管理員是否實作 Office XP 樣式功能表。  \(覆寫 [CMFCVisualManager::IsOfficeXPStyleMenus](../Topic/CMFCVisualManager::IsOfficeXPStyleMenus.md)\)。|  
|[CMFCVisualManagerWindows::IsWindowsThemingSupported](../Topic/CMFCVisualManagerWindows::IsWindowsThemingSupported.md)|\(覆寫 `CMFCVisualManager::IsWindowsThemingSupported`\)。|  
|[CMFCVisualManagerWindows::IsWinXPThemeAvailable](../Topic/CMFCVisualManagerWindows::IsWinXPThemeAvailable.md)|表示 Windows 佈景主題是否可用。  主題可以是 Windows XP 主題或 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 佈景主題。|  
|[CMFCVisualManagerWindows::OnDrawBarGripper](../Topic/CMFCVisualManagerWindows::OnDrawBarGripper.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawBarGripper`\)。|  
|[CMFCVisualManagerWindows::OnDrawBrowseButton](../Topic/CMFCVisualManagerWindows::OnDrawBrowseButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`\)。|  
|[CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawButtonSeparator](../Topic/CMFCVisualManagerWindows::OnDrawButtonSeparator.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawButtonSeparator`\)。|  
|[CMFCVisualManagerWindows::OnDrawCaptionButton](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`\)。|  
|[CMFCVisualManagerWindows::OnDrawCaptionButtonIcon](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButtonIcon.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawCaptionButtonIcon`\)。|  
|[CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md)|\(覆寫 [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawComboBorder](../Topic/CMFCVisualManagerWindows::OnDrawComboBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawComboBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`\)。|  
|[CMFCVisualManagerWindows::OnDrawControlBorder](../Topic/CMFCVisualManagerWindows::OnDrawControlBorder.md)|\(覆寫 [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawEditBorder](../Topic/CMFCVisualManagerWindows::OnDrawEditBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawEditBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawExpandingBox](../Topic/CMFCVisualManagerWindows::OnDrawExpandingBox.md)|\(覆寫 [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder](../Topic/CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawFloatingToolbarBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder.md)|表示處於 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)執行個體時，周圍繪製框線架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow.md)|則繪製標題控制項的排序箭號時，架構會呼叫這個函式。  \(覆寫 [CMFCVisualManager::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManager::OnDrawHeaderCtrlSortArrow.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawMenuSystemButton](../Topic/CMFCVisualManagerWindows::OnDrawMenuSystemButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawMenuSystemButton`\)。|  
|[CMFCVisualManagerWindows::OnDrawMiniFrameBorder](../Topic/CMFCVisualManagerWindows::OnDrawMiniFrameBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawMiniFrameBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder.md)|呼叫框架時，它會將 Outlook 頁面按鈕的框線。  \(覆寫 [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawPaneBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawPaneCaption](../Topic/CMFCVisualManagerWindows::OnDrawPaneCaption.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`\)。|  
|[CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawScrollButtons](../Topic/CMFCVisualManagerWindows::OnDrawScrollButtons.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`\)。|  
|[CMFCVisualManagerWindows::OnDrawSeparator](../Topic/CMFCVisualManagerWindows::OnDrawSeparator.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawSeparator`\)。|  
|[CMFCVisualManagerWindows::OnDrawSpinButtons](../Topic/CMFCVisualManagerWindows::OnDrawSpinButtons.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawSpinButtons`\)。|  
|[CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarProgress.md)|則繪製在 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) 物件時，的進度指示器架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md)|在繪製 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)的大小時，控制項方塊架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md)\)。|  
|[CMFCVisualManagerWindows::OnDrawTab](../Topic/CMFCVisualManagerWindows::OnDrawTab.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTab`\)。|  
|[CMFCVisualManagerWindows::OnDrawTabCloseButton](../Topic/CMFCVisualManagerWindows::OnDrawTabCloseButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTabCloseButton`\)。|  
|[CMFCVisualManagerWindows::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawTabsButtonBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawTask](../Topic/CMFCVisualManagerWindows::OnDrawTask.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTask`\)。|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`\)。|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupCaption.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`\)。|  
|[CMFCVisualManagerWindows::OnDrawTearOffCaption](../Topic/CMFCVisualManagerWindows::OnDrawTearOffCaption.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`\)。|  
|[CMFCVisualManagerWindows::OnErasePopupWindowButton](../Topic/CMFCVisualManagerWindows::OnErasePopupWindowButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`\)。|  
|[CMFCVisualManagerWindows::OnEraseTabsArea](../Topic/CMFCVisualManagerWindows::OnEraseTabsArea.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnEraseTabsArea`\)。|  
|[CMFCVisualManagerWindows::OnEraseTabsButton](../Topic/CMFCVisualManagerWindows::OnEraseTabsButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnEraseTabsButton`\)。|  
|[CMFCVisualManagerWindows::OnEraseTabsFrame](../Topic/CMFCVisualManagerWindows::OnEraseTabsFrame.md)|會清除在 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)時，框架的架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md)\)。|  
|[CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillBarBackground`\)。|  
|[CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillButtonInterior`\)。|  
|[CMFCVisualManagerWindows::OnFillCommandsListBackground](../Topic/CMFCVisualManagerWindows::OnFillCommandsListBackground.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`\)。|  
|[CMFCVisualManagerWindows::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerWindows::OnFillMiniFrameCaption.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`\)。|  
|[CMFCVisualManagerWindows::OnFillOutlookPageButton](../Topic/CMFCVisualManagerWindows::OnFillOutlookPageButton.md)|會填入 Outlook 頁面按鈕的內部時，架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md)\)。|  
|[CMFCVisualManagerWindows::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerWindows::OnFillTasksGroupInterior.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`\)。|  
|[CMFCVisualManagerWindows::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerWindows::OnFillTasksPaneBackground.md)|會填滿控制項的背景 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 時，架構會呼叫這個方法。  \(覆寫 [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md)\)。|  
|[CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnHighlightMenuItem`\)。|  
|[CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`\)。|  
|[CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`\)。|  
|[CMFCVisualManagerWindows::SetOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::SetOfficeStyleMenus.md)||  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCVisualManagerWindows::m\_b3DTabsXPTheme](../Topic/CMFCVisualManagerWindows::m_b3DTabsXPTheme.md)|指定 Windows XP 主題是否顯示 3D 索引標籤。|  
  
## 備註  
 使用 `CMFCVisualManagerWindows` 類別變更應用程式外觀與目前 Windows XP 或 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 佈景主題會在應用程式執行的電腦上。  
  
 不過， Windows 佈景主題可能無法使用，如果應用程式是在 Windows 版本早於 Windows XP 上執行，或者停用主題，因為使用者使用 \[**傳統**\] 檢視。  如果主題不可用，則會使用預設視覺管理員所定義的應用程式在 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
## 範例  
 下列範例示範如何使用 `CMFCVisualManagerWindows`。  這個程式碼片段是 [桌面警示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#10](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagerwindows-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
## 需求  
 **標題:** afxvisualmanagerwindows.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)