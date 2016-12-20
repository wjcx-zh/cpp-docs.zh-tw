---
title: "CMFCRibbonBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBar class"
ms.assetid: a65d06fa-1a28-4cc0-8971-bc9d7c9198fe
caps.latest.revision: 41
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonBar` 類別會實作類似於 Office 2007 中使用的功能區列。  
  
## 語法  
  
```  
class CMFCRibbonBar : public CPane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonBar::CMFCRibbonBar`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonBar::ActivateContextCategory](../Topic/CMFCRibbonBar::ActivateContextCategory.md)|啟動已經可見的內容分類。|  
|[CMFCRibbonBar::AddCategory](../Topic/CMFCRibbonBar::AddCategory.md)|將新的功能區分類加入至功能區。|  
|[CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md)|加入內容分類。|  
|[CMFCRibbonBar::AddMainCategory](../Topic/CMFCRibbonBar::AddMainCategory.md)|加入新的主要功能區分類。|  
|[CMFCRibbonBar::AddPrintPreviewCategory](../Topic/CMFCRibbonBar::AddPrintPreviewCategory.md)||  
|[CMFCRibbonBar::AddQATOnlyCategory](../Topic/CMFCRibbonBar::AddQATOnlyCategory.md)||  
|[CMFCRibbonBar::AddToTabs](../Topic/CMFCRibbonBar::AddToTabs.md)|將功能區項目加入至功能區列的右側。|  
|[CMFCRibbonBar::CreateEx](../Topic/CMFCRibbonBar::CreateEx.md)|建立控制列並將它附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  \(覆寫 [CPane::CreateEx](../Topic/CPane::CreateEx.md)。\)|  
|[CMFCRibbonBar::Create](../Topic/CMFCRibbonBar::Create.md)|建立功能區列控制項並將它附加至功能區列。|  
|[CMFCRibbonBar::DeactivateKeyboardFocus](../Topic/CMFCRibbonBar::DeactivateKeyboardFocus.md)||  
|[CMFCRibbonBar::DrawMenuImage](../Topic/CMFCRibbonBar::DrawMenuImage.md)||  
|[CMFCRibbonBar::DWMCompositionChanged](../Topic/CMFCRibbonBar::DWMCompositionChanged.md)||  
|[CMFCRibbonBar::EnableKeyTips](../Topic/CMFCRibbonBar::EnableKeyTips.md)|啟用或停用功能區控制項的按鍵提示。|  
|[CMFCRibbonBar::EnablePrintPreview](../Topic/CMFCRibbonBar::EnablePrintPreview.md)|啟用 \[**預覽列印**\] 索引標籤。|  
|[CMFCRibbonBar::EnableToolTips](../Topic/CMFCRibbonBar::EnableToolTips.md)|啟用或停用功能區列上的工具提示和工具提示描述。|  
|[CMFCRibbonBar::FindByData](../Topic/CMFCRibbonBar::FindByData.md)|利用使用者指定的資料尋找功能區項目。|  
|[CMFCRibbonBar::FindByID](../Topic/CMFCRibbonBar::FindByID.md)|尋找具有指定的命令識別碼的功能區項目。|  
|[CMFCRibbonBar::FindCategoryIndexByData](../Topic/CMFCRibbonBar::FindCategoryIndexByData.md)|尋找包含使用者定義資料的功能區分類的索引。|  
|[CMFCRibbonBar::ForceRecalcLayout](../Topic/CMFCRibbonBar::ForceRecalcLayout.md)||  
|[CMFCRibbonBar::GetActiveCategory](../Topic/CMFCRibbonBar::GetActiveCategory.md)|取得作用中分類的指標。|  
|[CMFCRibbonBar::GetCaptionHeight](../Topic/CMFCRibbonBar::GetCaptionHeight.md)|傳回標題高度。  \(覆寫 [CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)。\)|  
|[CMFCRibbonBar::GetCategory](../Topic/CMFCRibbonBar::GetCategory.md)|取得位於指定索引的分類的指標。|  
|[CMFCRibbonBar::GetCategoryCount](../Topic/CMFCRibbonBar::GetCategoryCount.md)|取得功能區列中的功能區分類數目。|  
|[CMFCRibbonBar::GetCategoryHeight](../Topic/CMFCRibbonBar::GetCategoryHeight.md)||  
|[CMFCRibbonBar::GetCategoryIndex](../Topic/CMFCRibbonBar::GetCategoryIndex.md)|傳回功能區分類別的索引。|  
|[CMFCRibbonBar::GetContextName](../Topic/CMFCRibbonBar::GetContextName.md)|使用識別碼擷取您指定的內容分類標題的名稱。|  
|[CMFCRibbonBar::GetDroppedDown](../Topic/CMFCRibbonBar::GetDroppedDown.md)||  
|[CMFCRibbonBar::GetElementsByID](../Topic/CMFCRibbonBar::GetElementsByID.md)|取得陣列，其中包含具有指定識別碼的所有功能區項目的指標。|  
|[CMFCRibbonBar::GetApplicationButton](../Topic/CMFCRibbonBar::GetApplicationButton.md)|取得功能區按鈕的指標。|  
|[CMFCRibbonBar::GetFocused](../Topic/CMFCRibbonBar::GetFocused.md)|傳回具有焦點的項目。|  
|[CMFCRibbonBar::GetHideFlags](../Topic/CMFCRibbonBar::GetHideFlags.md)||  
|[CMFCRibbonBar::GetItemIDsList](../Topic/CMFCRibbonBar::GetItemIDsList.md)||  
|[CMFCRibbonBar::GetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::GetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelCurrent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelCurrent.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelParent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelParent.md)||  
|[CMFCRibbonBar::GetMainCategory](../Topic/CMFCRibbonBar::GetMainCategory.md)|傳回目前選取的功能區分類的指標。|  
|[CMFCRibbonBar::GetQATCommandsLocation](../Topic/CMFCRibbonBar::GetQATCommandsLocation.md)||  
|[CMFCRibbonBar::GetQATDroppedDown](../Topic/CMFCRibbonBar::GetQATDroppedDown.md)||  
|[CMFCRibbonBar::GetQuickAccessCommands](../Topic/CMFCRibbonBar::GetQuickAccessCommands.md)|填入清單，其中包含出現在快速存取工具列的所有項目的命令識別碼。|  
|[CMFCRibbonBar::GetQuickAccessToolbarLocation](../Topic/CMFCRibbonBar::GetQuickAccessToolbarLocation.md)||  
|[CMFCRibbonBar::GetTabTrancateRatio](../Topic/CMFCRibbonBar::GetTabTrancateRatio.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthLargeImage](../Topic/CMFCRibbonBar::GetTooltipFixedWidthLargeImage.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthRegular](../Topic/CMFCRibbonBar::GetTooltipFixedWidthRegular.md)||  
|[CMFCRibbonBar::GetVisibleCategoryCount](../Topic/CMFCRibbonBar::GetVisibleCategoryCount.md)||  
|[CMFCRibbonBar::HideAllContextCategories](../Topic/CMFCRibbonBar::HideAllContextCategories.md)|隱藏所有作用中和可見的分類。|  
|[CMFCRibbonBar::HideKeyTips](../Topic/CMFCRibbonBar::HideKeyTips.md)||  
|[CMFCRibbonBar::HitTest](../Topic/CMFCRibbonBar::HitTest.md)|尋找位於功能區列的用戶端座標指定點的功能區項目的指標。|  
|[CMFCRibbonBar::IsKeyTipEnabled](../Topic/CMFCRibbonBar::IsKeyTipEnabled.md)|決定按鍵提示是否啟用。|  
|[CMFCRibbonBar::IsMainRibbonBar](../Topic/CMFCRibbonBar::IsMainRibbonBar.md)||  
|[CMFCRibbonBar::IsPrintPreviewEnabled](../Topic/CMFCRibbonBar::IsPrintPreviewEnabled.md)|決定 \[**預覽列印**\] 索引標籤是否啟用。|  
|[CMFCRibbonBar::IsQATEmpty](../Topic/CMFCRibbonBar::IsQATEmpty.md)||  
|[CMFCRibbonBar::IsQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::IsQuickAccessToolbarOnTop.md)|指定快速存取工具列是否位於功能區列上方。|  
|[CMFCRibbonBar::IsReplaceFrameCaption](../Topic/CMFCRibbonBar::IsReplaceFrameCaption.md)|決定功能區列是否取代主框架標題，或加入至框架標題下方。|  
|[CMFCRibbonBar::IsShowGroupBorder](../Topic/CMFCRibbonBar::IsShowGroupBorder.md)||  
|[CMFCRibbonBar::IsToolTipDescrEnabled](../Topic/CMFCRibbonBar::IsToolTipDescrEnabled.md)|決定工具提示描述是否啟用。|  
|[CMFCRibbonBar::IsToolTipEnabled](../Topic/CMFCRibbonBar::IsToolTipEnabled.md)|決定功能區列的工具提示是否啟用。|  
|[CMFCRibbonBar::IsTransparentCaption](../Topic/CMFCRibbonBar::IsTransparentCaption.md)||  
|[CMFCRibbonBar::IsWindows7Look](../Topic/CMFCRibbonBar::IsWindows7Look.md)|指出功能區是否具有 Windows 7 樣式外觀 \(小型矩形應用程式按鈕\)。|  
|[CMFCRibbonBar::LoadFromResource](../Topic/CMFCRibbonBar::LoadFromResource.md)|多載。  從應用程式資源載入功能區列。|  
|[CMFCRibbonBar::OnClickButton](../Topic/CMFCRibbonBar::OnClickButton.md)||  
|[CMFCRibbonBar::OnEditContextMenu](../Topic/CMFCRibbonBar::OnEditContextMenu.md)||  
|[CMFCRibbonBar::OnRTLChanged](../Topic/CMFCRibbonBar::OnRTLChanged.md)|\(覆寫 `CPane::OnRTLChanged`。\)|  
|[CMFCRibbonBar::OnSetAccData](../Topic/CMFCRibbonBar::OnSetAccData.md)|\(覆寫 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md).\)|  
|[CMFCRibbonBar::OnShowRibbonContextMenu](../Topic/CMFCRibbonBar::OnShowRibbonContextMenu.md)||  
|[CMFCRibbonBar::OnShowRibbonQATMenu](../Topic/CMFCRibbonBar::OnShowRibbonQATMenu.md)||  
|[CMFCRibbonBar::OnSysKeyDown](../Topic/CMFCRibbonBar::OnSysKeyDown.md)||  
|[CMFCRibbonBar::OnSysKeyUp](../Topic/CMFCRibbonBar::OnSysKeyUp.md)||  
|[CMFCRibbonBar::PopTooltip](../Topic/CMFCRibbonBar::PopTooltip.md)||  
|[CMFCRibbonBar::PreTranslateMessage](../Topic/CMFCRibbonBar::PreTranslateMessage.md)|\(覆寫 `CBasePane::PreTranslateMessage`。\)|  
|[CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md)|\(覆寫 [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md).\)|  
|[CMFCRibbonBar::RemoveAllCategories](../Topic/CMFCRibbonBar::RemoveAllCategories.md)|從功能區列中移除所有功能區分類。|  
|[CMFCRibbonBar::RemoveAllFromTabs](../Topic/CMFCRibbonBar::RemoveAllFromTabs.md)|從索引標籤區域中移除所有功能區項目。|  
|[CMFCRibbonBar::RemoveCategory](../Topic/CMFCRibbonBar::RemoveCategory.md)|移除位於指定索引的功能區分類。|  
|[CMFCRibbonBar::SaveToXMLBuffer](../Topic/CMFCRibbonBar::SaveToXMLBuffer.md)|將功能區列儲存至緩衝區。|  
|[CMFCRibbonBar::SaveToXMLFile](../Topic/CMFCRibbonBar::SaveToXMLFile.md)|將功能區列儲存至 XML 檔案。|  
|[CMFCRibbonBar::SetActiveCategory](../Topic/CMFCRibbonBar::SetActiveCategory.md)|將指定的功能區分類設定為作用中。|  
|[CMFCRibbonBar::SetActiveMDIChild](../Topic/CMFCRibbonBar::SetActiveMDIChild.md)||  
|[CMFCRibbonBar::SetElementKeys](../Topic/CMFCRibbonBar::SetElementKeys.md)|針對具有指定命令識別碼的所有功能區項目，設定指定的按鍵提示。|  
|[CMFCRibbonBar::SetApplicationButton](../Topic/CMFCRibbonBar::SetApplicationButton.md)|將應用程式功能區按鈕指派給功能區列。|  
|[CMFCRibbonBar::SetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::SetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::SetMaximizeMode](../Topic/CMFCRibbonBar::SetMaximizeMode.md)||  
|[CMFCRibbonBar::SetQuickAccessCommands](../Topic/CMFCRibbonBar::SetQuickAccessCommands.md)|將一或多個功能區項目加入至快速存取工具列。|  
|[CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)|指定快速存取工具列的預設狀態。|  
|[CMFCRibbonBar::SetQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::SetQuickAccessToolbarOnTop.md)|將快速存取工具列 \(QAT\) 放在功能區列上方或下方|  
|[CMFCRibbonBar::SetTooltipFixedWidth](../Topic/CMFCRibbonBar::SetTooltipFixedWidth.md)||  
|[CMFCRibbonBar::SetWindows7Look](../Topic/CMFCRibbonBar::SetWindows7Look.md)|啟用\/停用功能區 Windows 7 樣式外觀 \(小型矩形應用程式按鈕\)。|  
|[CMFCRibbonBar::ShowCategory](../Topic/CMFCRibbonBar::ShowCategory.md)|顯示或隱藏指定的功能區分類。|  
|[CMFCRibbonBar::ShowContextCategories](../Topic/CMFCRibbonBar::ShowContextCategories.md)|顯示或隱藏具有指定識別碼的內容分類。|  
|[CMFCRibbonBar::ShowKeyTips](../Topic/CMFCRibbonBar::ShowKeyTips.md)||  
|[CMFCRibbonBar::ToggleMimimizeState](../Topic/CMFCRibbonBar::ToggleMimimizeState.md)|在功能區列的最小化和最大化狀態之間切換。|  
|[CMFCRibbonBar::TranslateChar](../Topic/CMFCRibbonBar::TranslateChar.md)||  
  
## 備註  
 Microsoft 在發行 Microsoft Office 2007 的同時，也引進 Office Fluent 功能區。  此功能區列不只是新的控制項而已。  它代表一種全新的使用者介面典範。  功能區是一個窗格，其中包含一組稱為分類的索引標籤。  每個分類在邏輯上分割為功能區面板，每個面板可以包含各種控制項和命令按鈕。  
  
 出現在功能區列的項目會展開和收合，以充分利用可用空間。  例如，如果功能區面板的空間不足以顯示項目，則會變成功能表按鈕，以快顯功能表來顯示子項目。  功能區列就像靜態 \(非浮動\) 控制列，可停駐在框架頂端。  
  
 您可以使用 `CMFCRibbonStatusBar` 類別來實作類似於 Office 2007 中使用的狀態列。  功能區分類包含 \(及顯示\) 一組[功能區面板](../../mfc/reference/cmfcribbonpanel-class.md)。  每個功能區面板包含一或多個衍生自 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) 的功能區項目。  
  
 如需如何將功能區列加入至現有 MFC 應用程式的詳細資訊，請參閱[逐步解說：更新 MFC Scribble 應用程式](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
## 需求  
 **標頭：**afxribbonbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [逐步解說：更新 MFC Scribble 應用程式](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)