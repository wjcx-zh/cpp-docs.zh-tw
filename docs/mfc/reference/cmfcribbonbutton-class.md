---
title: "CMFCRibbonButton Class | Microsoft Docs"
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
  - "CMFCRibbonButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButton class"
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonButton` 類別實作可以放置在功能區列項目 \(例如面板、快速存取工具列和快顯功能表\) 上的按鈕。  
  
## 語法  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonButton::CMFCRibbonButton](../Topic/CMFCRibbonButton::CMFCRibbonButton.md)|建構功能區按鈕物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonButton::AddSubItem](../Topic/CMFCRibbonButton::AddSubItem.md)|將功能表項目加入至與按鈕相關聯的快顯功能表。|  
|[CMFCRibbonButton::CanBeStretched](../Topic/CMFCRibbonButton::CanBeStretched.md)|\(覆寫 [CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)。\)|  
|[CMFCRibbonButton::CleanUpSizes](../Topic/CMFCRibbonButton::CleanUpSizes.md)|\(覆寫 [CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)。\)|  
|[CMFCRibbonButton::ClosePopupMenu](../Topic/CMFCRibbonButton::ClosePopupMenu.md)|\(覆寫 [CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)。\)|  
|[CMFCRibbonButton::DrawBottomText](../Topic/CMFCRibbonButton::DrawBottomText.md)||  
|[CMFCRibbonButton::DrawImage](../Topic/CMFCRibbonButton::DrawImage.md)|\(覆寫 [CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)。\)|  
|[CMFCRibbonButton::DrawRibbonText](../Topic/CMFCRibbonButton::DrawRibbonText.md)||  
|[CMFCRibbonButton::FindSubItemIndexByID](../Topic/CMFCRibbonButton::FindSubItemIndexByID.md)|傳回與指定之命令識別碼相關聯的快顯功能表項目索引。|  
|[CMFCRibbonButton::GetCommandRect](../Topic/CMFCRibbonButton::GetCommandRect.md)||  
|[CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)|傳回功能區項目的壓縮大小。  \(覆寫 [CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)。\)|  
|[CMFCRibbonButton::GetIcon](../Topic/CMFCRibbonButton::GetIcon.md)||  
|[CMFCRibbonButton::GetImageIndex](../Topic/CMFCRibbonButton::GetImageIndex.md)|傳回與按鈕相關聯的映像索引。|  
|[CMFCRibbonButton::GetImageSize](../Topic/CMFCRibbonButton::GetImageSize.md)|傳回功能區項目的影像大小。  \(覆寫 [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)。\)|  
|[CMFCRibbonButton::GetIntermediateSize](../Topic/CMFCRibbonButton::GetIntermediateSize.md)|傳回中繼狀態之功能區項目的大小。  \(覆寫 [CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)。\)|  
|[CMFCRibbonButton::GetMenu](../Topic/CMFCRibbonButton::GetMenu.md)|傳回已指派給功能區按鈕之 Windows 功能表的控制代碼。|  
|[CMFCRibbonButton::GetMenuRect](../Topic/CMFCRibbonButton::GetMenuRect.md)||  
|[CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)|傳回功能區項目的一般大小。  \(覆寫 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)。\)|  
|[CMFCRibbonButton::GetSubItems](../Topic/CMFCRibbonButton::GetSubItems.md)||  
|[CMFCRibbonButton::GetTextRowHeight](../Topic/CMFCRibbonButton::GetTextRowHeight.md)||  
|[CMFCRibbonButton::GetToolTipText](../Topic/CMFCRibbonButton::GetToolTipText.md)|傳回功能區項目的工具提示文字。  \(覆寫 [CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)。\)|  
|[CMFCRibbonButton::HasCompactMode](../Topic/CMFCRibbonButton::HasCompactMode.md)|指定功能區項目是否有精簡模式。  \(覆寫 [CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)。\)|  
|[CMFCRibbonButton::HasIntermediateMode](../Topic/CMFCRibbonButton::HasIntermediateMode.md)|指定功能區項目是否有中繼模式。  \(覆寫 [CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)。\)|  
|[CMFCRibbonButton::HasLargeMode](../Topic/CMFCRibbonButton::HasLargeMode.md)|指定功能區項目是否有大型模式。  \(覆寫 [CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)。\)|  
|[CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md)|\(覆寫 [CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)。\)|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](../Topic/CMFCRibbonButton::IsAlwaysDrawBorder.md)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](../Topic/CMFCRibbonButton::IsAlwaysLargeImage.md)|\(覆寫 [CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)。\)|  
|[CMFCRibbonButton::IsApplicationButton](../Topic/CMFCRibbonButton::IsApplicationButton.md)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](../Topic/CMFCRibbonButton::IsCommandAreaHighlighted.md)||  
|[CMFCRibbonButton::IsDefaultCommand](../Topic/CMFCRibbonButton::IsDefaultCommand.md)|判定您是否已啟用功能區按鈕的預設命令。|  
|[CMFCRibbonButton::IsDefaultPanelButton](../Topic/CMFCRibbonButton::IsDefaultPanelButton.md)||  
|[CMFCRibbonButton::IsDrawTooltipImage](../Topic/CMFCRibbonButton::IsDrawTooltipImage.md)||  
|[CMFCRibbonButton::IsLargeImage](../Topic/CMFCRibbonButton::IsLargeImage.md)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](../Topic/CMFCRibbonButton::IsMenuAreaHighlighted.md)||  
|[CMFCRibbonButton::IsMenuOnBottom](../Topic/CMFCRibbonButton::IsMenuOnBottom.md)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](../Topic/CMFCRibbonButton::IsPopupDefaultMenuLook.md)||  
|[CMFCRibbonButton::IsRightAlignMenu](../Topic/CMFCRibbonButton::IsRightAlignMenu.md)|判定功能表是否靠右對齊。|  
|[CMFCRibbonButton::IsSingleLineText](../Topic/CMFCRibbonButton::IsSingleLineText.md)||  
|[CMFCRibbonButton::OnCalcTextSize](../Topic/CMFCRibbonButton::OnCalcTextSize.md)|\(覆寫 [CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)。\)|  
|[CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md)||  
|[CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)|由架構呼叫以繪製功能區項目。  \(覆寫 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)。\)|  
|[CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md)||  
|[CMFCRibbonButton::RemoveAllSubItems](../Topic/CMFCRibbonButton::RemoveAllSubItems.md)|從快顯功能表中移除所有功能表項目。|  
|[CMFCRibbonButton::RemoveSubItem](../Topic/CMFCRibbonButton::RemoveSubItem.md)|從快顯功能表中移除功能表項目。|  
|[CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)|\(覆寫 [CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)。\)|  
|[CMFCRibbonButton::SetAlwaysLargeImage](../Topic/CMFCRibbonButton::SetAlwaysLargeImage.md)|指定使用者摺疊按鈕時，按鈕是顯示大型影像還是小型影像。|  
|[CMFCRibbonButton::SetDefaultCommand](../Topic/CMFCRibbonButton::SetDefaultCommand.md)|啟用功能區按鈕的預設命令。|  
|[CMFCRibbonButton::SetDescription](../Topic/CMFCRibbonButton::SetDescription.md)|設定功能區項目的描述。  \(覆寫 [CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)。\)|  
|[CMFCRibbonButton::SetImageIndex](../Topic/CMFCRibbonButton::SetImageIndex.md)|將索引指派給按鈕的影像。|  
|[CMFCRibbonButton::SetMenu](../Topic/CMFCRibbonButton::SetMenu.md)|將快顯功能表上指派給功能區按鈕。|  
|[CMFCRibbonButton::SetParentCategory](../Topic/CMFCRibbonButton::SetParentCategory.md)|\(覆寫 [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)。\)|  
|[CMFCRibbonButton::SetRightAlignMenu](../Topic/CMFCRibbonButton::SetRightAlignMenu.md)|將快顯功能表對齊按鈕右邊。|  
|[CMFCRibbonButton::SetText](../Topic/CMFCRibbonButton::SetText.md)|設定功能區項目的文字。  \(覆寫 [CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)。\)|  
  
### 保護方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonButton::OnClick](../Topic/CMFCRibbonButton::OnClick.md)|使用者按一下按鈕時由架構呼叫。|  
  
## 範例  
 下列範例示範如何在 `CMFCRibbonButton` 類別中使用各種方法。  此範例示範如何建構 `CMFCRibbonButton` 類別的物件、將快顯功能表指派給功能區按鈕、設定按鈕的描述、從快顯功能表中移除功能表項目，以及將快顯功能表靠右對齊按鈕的邊緣。  
  
 [!code-cpp[NVC_MFC_RibbonApp#7](../../mfc/reference/codesnippet/CPP/cmfcribbonbutton-class_1.cpp)]  
  
## 備註  
 若要在應用程式中使用功能區按鈕，請建構按鈕物件，並將它加入至適當的功能區 [面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (  
    _T("Clipboard"),                       // Panel name  
    m_PanelIcons.ExtractIcon (0));  // Panel icon  
// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton =   
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);  
// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);  
// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));  
```  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## 需求  
 **標頭：** afxribbonbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)