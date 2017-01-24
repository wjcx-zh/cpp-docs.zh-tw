---
title: "CMFCVisualManagerWindows7 Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxvisualmanagerwindows7/CMFCVisualManagerWindows7"
  - "CMFCVisualManagerWindows7"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows7 class"
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerWindows7 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerWindows7` 寫入應用程式 [!INCLUDE[win7](../../build/includes/win7_md.md)] 應用程式的外觀。  
  
## 語法  
  
```  
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7.md)|預設建構函式。|  
|[CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7.md)|預設的解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCVisualManagerWindows7::CleanStyle`|清除目前視覺化樣式並重設預設視覺化樣式。|  
|`CMFCVisualManagerWindows7::CleanUp`|清除所有的使用者介面 \(UI\) 中的物件並重設功能表。|  
|`CMFCVisualManagerWindows7::DrawNcBtn`|繪製在非用戶端區域中的按鈕在框架。  架構會使用此方法來繪製最小化，最大化，關閉並還原按鈕在框架右上角。  當程式使用非 Aero 佈景主題時，不會呼叫這個方法。|  
|`CMFCVisualManagerWindows7::DrawNcText`|繪製在非工作區的文字在框架。  架構會在標題列中使用這個方法會繪製應用程式標題在框架視窗上方。|  
|`CMFCVisualManagerWindows7::DrawSeparator`|繪製在 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)的分隔符號。|  
|`CMFCVisualManagerWindows7::GetRibbonBar`|擷取 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) 與使用者介面。|  
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](../Topic/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor.md)|取得一個功能區編輯方塊背景色彩。|  
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|覆寫 [CMFCVisualManager::GetRibbonPopupBorderSize](../Topic/CMFCVisualManager::GetRibbonPopupBorderSize.md)。|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|覆寫 [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset.md)。|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|覆寫 [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin.md)。|  
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|覆寫 [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md)。|  
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|覆寫 [CMFCVisualManager::IsOwnerDrawMenuCheck](../Topic/CMFCVisualManager::IsOwnerDrawMenuCheck.md)。|  
|`CMFCVisualManagerWindows7::IsRibbonPresent`|判斷 `CMFCRibbonBar` 是否存在並且可見。|  
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|覆寫 [CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md)。|  
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|覆寫 [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md)。|  
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|覆寫 [CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|覆寫 [CMFCVisualManager::OnDrawDefaultRibbonImage](../Topic/CMFCVisualManager::OnDrawDefaultRibbonImage.md)。|  
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|覆寫 [CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md)。|  
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|覆寫 [CMFCVisualManager::OnDrawMenuCheck](../Topic/CMFCVisualManager::OnDrawMenuCheck.md)。|  
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|覆寫 [CMFCVisualManager::OnDrawMenuLabel](../Topic/CMFCVisualManager::OnDrawMenuLabel.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|覆寫 `CMFCVisualManager::OnDrawRadioButton`。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|覆寫 [CMFCVisualManager::OnDrawRibbonApplicationButton](../Topic/CMFCVisualManager::OnDrawRibbonApplicationButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|覆寫 [CMFCVisualManager::OnDrawRibbonButtonBorder](../Topic/CMFCVisualManager::OnDrawRibbonButtonBorder.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|覆寫 [CMFCVisualManager::OnDrawRibbonCaption](../Topic/CMFCVisualManager::OnDrawRibbonCaption.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|覆寫 [CMFCVisualManager::OnDrawRibbonCaptionButton](../Topic/CMFCVisualManager::OnDrawRibbonCaptionButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|覆寫 [CMFCVisualManager::OnDrawRibbonCategory](../Topic/CMFCVisualManager::OnDrawRibbonCategory.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|覆寫 [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|覆寫 [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|覆寫 [CMFCVisualManager::OnDrawRibbonGalleryButton](../Topic/CMFCVisualManager::OnDrawRibbonGalleryButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|覆寫 `CMFCVisualManager::OnDrawRibbonLaunchButton`。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|覆寫 [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../Topic/CMFCVisualManager::OnDrawRibbonMenuCheckFrame.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|覆寫 [CMFCVisualManager::OnDrawRibbonPanel](../Topic/CMFCVisualManager::OnDrawRibbonPanel.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|覆寫 [CMFCVisualManager::OnDrawRibbonPanelCaption](../Topic/CMFCVisualManager::OnDrawRibbonPanelCaption.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|覆寫 [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|覆寫 [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../Topic/CMFCVisualManager::OnDrawRibbonRecentFilesFrame.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|覆寫 [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|覆寫 [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|覆寫 [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|覆寫 [CMFCVisualManager::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManager::OnDrawRibbonStatusBarPane.md)。|  
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|覆寫 [CMFCVisualManager::OnDrawRibbonTabsFrame](../Topic/CMFCVisualManager::OnDrawRibbonTabsFrame.md)。|  
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|覆寫 [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md)。|  
|`CMFCVisualManagerWindows7::OnFillBarBackground`|覆寫 [CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md)。|  
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|覆寫 [CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md)。|  
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](../Topic/CMFCVisualManagerWindows7::OnFillMenuImageRect.md)|表示處於功能表項目時，影像周圍繪製區域架構會呼叫這個方法。|  
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|覆寫 [CMFCVisualManager::OnFillRibbonButton](../Topic/CMFCVisualManager::OnFillRibbonButton.md)。|  
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|覆寫 [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../Topic/CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup.md)。|  
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|覆寫 [CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md)。|  
|`CMFCVisualManagerWindows7::OnNcActivate`|覆寫 [CMFCVisualManager::OnNcActivate](../Topic/CMFCVisualManager::OnNcActivate.md)。|  
|`CMFCVisualManagerWindows7::OnNcPaint`|覆寫 [CMFCVisualManager::OnNcPaint](../Topic/CMFCVisualManager::OnNcPaint.md)。|  
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|覆寫 [CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md)。|  
|`CMFCVisualManagerWindows7::SetResourceHandle`|設定描述視覺管理員的屬性的資源控制代碼。|  
|`CMFCVisualManagerWindows7::SetStyle`|設定 `CMFCVisualManagerWindows7` GUI 的色彩配置。|  
  
## 備註  
 使用 `CMFCVisualManagerWindows7` 類別將您的應用程式會模擬預設 [!INCLUDE[win7](../../build/includes/win7_md.md)] 應用程式。  此外，如果您的應用程式在 Windows 版本早於 [!INCLUDE[win7](../../build/includes/win7_md.md)]執行，這個類別可能會無效。  在該案例中，使用 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md) 所定義的預設視覺管理員，。  
  
 CMFCVisualManagerWindows7 繼承自 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md) 和 `CMFCVisualManager` 類別的多個方法。  在上一節中所列的方法是方法的新 `CMFCVisualManagerWindows7` 類別。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
 `CMFCVisualManagerWindows7`  
  
## 需求  
 **標題:** afxvisualmanagerwindows7.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)