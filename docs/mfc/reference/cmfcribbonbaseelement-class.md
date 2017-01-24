---
title: "CMFCRibbonBaseElement Class | Microsoft Docs"
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
  - "CMFCRibbonBaseElement"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBaseElement class"
ms.assetid: 419ea91b-5062-44cc-b0a3-f87d29566f62
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonBaseElement Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonBaseElement` 類別是可以加入 [功能區列](../../mfc/reference/cmfcribbonbar-class.md)中所有項目的基底類別。  功能區項目的範例為 Office 功能區按鈕、核取方塊和功能區上下拉式方塊。  
  
## 語法  
  
```  
class CMFCRibbonBaseElement : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonBaseElement`|建構 `CMFCRibbonBaseElement` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonBaseElement::AddToKeyList](../Topic/CMFCRibbonBaseElement::AddToKeyList.md)|將功能區項目的 keytip 到字元陣列 keytips。|  
|[CMFCRibbonBaseElement::AddToListBox](../Topic/CMFCRibbonBaseElement::AddToListBox.md)|將功能區項目加入至指定的功能區命令清單方塊。|  
|[CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar](../Topic/CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar.md)|表示功能區項目是否可以加入至快速存取工具列。|  
|[CMFCRibbonBaseElement::CanBeCompacted](../Topic/CMFCRibbonBaseElement::CanBeCompacted.md)|表示功能區項目的大小是否可以是壓縮的。|  
|[CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)|表示功能區項目的高度是否可垂直加入至功能區列的高度。|  
|[CMFCRibbonBaseElement::CanBeStretchedHorizontally](../Topic/CMFCRibbonBaseElement::CanBeStretchedHorizontally.md)|表示功能區項目的寬度是否可以變更。|  
|[CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)|清除功能區項目的大小設定。|  
|[CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)|關閉功能區項目的快顯功能表。|  
|[CMFCRibbonBaseElement::CopyFrom](../Topic/CMFCRibbonBaseElement::CopyFrom.md)|複製指定的 `CMFCRibbonBaseElement` 的狀態設定為目前的物件。|  
|[CMFCRibbonBaseElement::DestroyCtrl](../Topic/CMFCRibbonBaseElement::DestroyCtrl.md)|終結功能區項目。|  
|[CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)|繪製功能區項目的影像。|  
|[CMFCRibbonBaseElement::Find](../Topic/CMFCRibbonBaseElement::Find.md)|如果它指向目前的物件，傳回指定之指標功能區項目。|  
|[CMFCRibbonBaseElement::FindByData](../Topic/CMFCRibbonBaseElement::FindByData.md)|其中包含指定之資料，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::FindByID](../Topic/CMFCRibbonBaseElement::FindByID.md)|如果該項目是由指定的命令 ID.，決定要擷取指標功能區項目|  
|[CMFCRibbonBaseElement::FindByOriginal](../Topic/CMFCRibbonBaseElement::FindByOriginal.md)|如果其原始的功能區項目符合指定的功能區項目，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)|傳回功能區項目的袖珍型。|  
|[CMFCRibbonBaseElement::GetData](../Topic/CMFCRibbonBaseElement::GetData.md)|擷取使用者定義的資料與功能區項目。|  
|[CMFCRibbonBaseElement::GetDescription](../Topic/CMFCRibbonBaseElement::GetDescription.md)|傳回功能區項目的描述。|  
|[CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md)|;如果它的快顯功能表的下拉式，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::GetElements](../Topic/CMFCRibbonBaseElement::GetElements.md)|將目前的功能區項目加入至指定的陣列。|  
|[CMFCRibbonBaseElement::GetElementsByID](../Topic/CMFCRibbonBaseElement::GetElementsByID.md)|如果目前的功能區項目包含指定的命令 ID.，將目前的功能區項目加入至指定的陣列。|  
|[CMFCRibbonBaseElement::GetHighlighted](../Topic/CMFCRibbonBaseElement::GetHighlighted.md)|如果，它會反白顯示，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::GetID](../Topic/CMFCRibbonBaseElement::GetID.md)|傳回功能區項目的命令 ID。|  
|[CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)|傳回功能區項目的影像大小。|  
|[CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)|傳回功能區項目大小以及它的中繼狀態的。|  
|[CMFCRibbonBaseElement::GetKeys](../Topic/CMFCRibbonBaseElement::GetKeys.md)|傳回 keytip 與功能區項目。|  
|[CMFCRibbonBaseElement::GetKeyTipRect](../Topic/CMFCRibbonBaseElement::GetKeyTipRect.md)|擷取功能區項目 keytip 界限的矩形。|  
|[CMFCRibbonBaseElement::GetKeyTipSize](../Topic/CMFCRibbonBaseElement::GetKeyTipSize.md)|擷取 keytip 文字的大小。|  
|[CMFCRibbonBaseElement::GetLocationInGroup](../Topic/CMFCRibbonBaseElement::GetLocationInGroup.md)|在功能區群組中表示功能區項目的顯示位置。|  
|[CMFCRibbonBaseElement::GetMenuKeys](../Topic/CMFCRibbonBaseElement::GetMenuKeys.md)|傳回 keytips 與按鈕。|  
|[CMFCRibbonBaseElement::GetNotifyID](../Topic/CMFCRibbonBaseElement::GetNotifyID.md)|擷取功能區項目的告知命令 ID。|  
|[CMFCRibbonBaseElement::GetOriginal](../Topic/CMFCRibbonBaseElement::GetOriginal.md)|擷取原始功能區項目。|  
|[CMFCRibbonBaseElement::GetParentCategory](../Topic/CMFCRibbonBaseElement::GetParentCategory.md)|擷取功能區項目的功能區類別。|  
|[CMFCRibbonBaseElement::GetParentPanel](../Topic/CMFCRibbonBaseElement::GetParentPanel.md)|擷取包含功能區項目的功能區面板。|  
|[CMFCRibbonBaseElement::GetParentRibbonBar](../Topic/CMFCRibbonBaseElement::GetParentRibbonBar.md)|擷取功能區項目的父功能區列。|  
|[CMFCRibbonBaseElement::GetParentWnd](../Topic/CMFCRibbonBaseElement::GetParentWnd.md)|擷取功能區項目的父視窗。|  
|[CMFCRibbonBaseElement::GetPressed](../Topic/CMFCRibbonBaseElement::GetPressed.md)|目前，如果使用者按下它，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::GetQuickAccessToolBarID](../Topic/CMFCRibbonBaseElement::GetQuickAccessToolBarID.md)|其位於快速存取工具列時，擷取功能區項目的命令 ID。|  
|[CMFCRibbonBaseElement::GetRect](../Topic/CMFCRibbonBaseElement::GetRect.md)|傳回功能區項目的週框 \(Bounding Rectangle\)。|  
|[CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)|傳回功能區項目的一般大小。|  
|[CMFCRibbonBaseElement::GetSize](../Topic/CMFCRibbonBaseElement::GetSize.md)|傳回功能區項目的目前大小。|  
|[CMFCRibbonBaseElement::GetText](../Topic/CMFCRibbonBaseElement::GetText.md)|傳回與關聯的文字功能區項目。|  
|[CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)|傳回功能區項目的工具提示文字。|  
|[CMFCRibbonBaseElement::GetTopLevelRibbonBar](../Topic/CMFCRibbonBaseElement::GetTopLevelRibbonBar.md)|擷取功能區項目的最上層功能區列。|  
|[CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)|指定功能區項目是否具有簡潔的方式。|  
|[CMFCRibbonBaseElement::HasFocus](../Topic/CMFCRibbonBaseElement::HasFocus.md)|表示父項目是否具有鍵盤焦點。|  
|[CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)|指定功能區項目是否有中繼的方式。|  
|[CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)|指定功能區項目是否具有大型的方式。|  
|[CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)|表示功能區項目是否有名為的功能表。|  
|[CMFCRibbonBaseElement::HitTest](../Topic/CMFCRibbonBaseElement::HitTest.md)|如果指定的點，它是位於，擷取指標功能區項目。|  
|[CMFCRibbonBaseElement::IsAlignByColumn](../Topic/CMFCRibbonBaseElement::IsAlignByColumn.md)|表示功能區項目是垂直對齊其他功能區項目。|  
|[CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)|表示功能區項目影像大小是否一定會很大。|  
|[CMFCRibbonBaseElement::IsAutoRepeatMode](../Topic/CMFCRibbonBaseElement::IsAutoRepeatMode.md)|表示功能區項目是否在自動重複模式。|  
|[CMFCRibbonBaseElement::IsChecked](../Topic/CMFCRibbonBaseElement::IsChecked.md)|指定功能區項目是否已選取。|  
|[CMFCRibbonBaseElement::IsCompactMode](../Topic/CMFCRibbonBaseElement::IsCompactMode.md)|指定功能區項目是以精簡模式。|  
|[CMFCRibbonBaseElement::IsDefaultMenuLook](../Topic/CMFCRibbonBaseElement::IsDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::IsDisabled](../Topic/CMFCRibbonBaseElement::IsDisabled.md)|指定功能區項目是否停用。|  
|[CMFCRibbonBaseElement::IsDroppedDown](../Topic/CMFCRibbonBaseElement::IsDroppedDown.md)|判斷功能區項目是否顯示快顯功能表和卸除下方。|  
|[CMFCRibbonBaseElement::IsFocused](../Topic/CMFCRibbonBaseElement::IsFocused.md)|指定功能區項目是否具有焦點。|  
|[CMFCRibbonBaseElement::IsGalleryIcon](../Topic/CMFCRibbonBaseElement::IsGalleryIcon.md)|表示功能區項目是否在功能區上圖庫中。|  
|[CMFCRibbonBaseElement::IsHighlighted](../Topic/CMFCRibbonBaseElement::IsHighlighted.md)|指定功能區項目是否會反白顯示。|  
|[CMFCRibbonBaseElement::IsIntermediateMode](../Topic/CMFCRibbonBaseElement::IsIntermediateMode.md)|表示功能區項目的目前影像是否為中間的大小。|  
|[CMFCRibbonBaseElement::IsLargeMode](../Topic/CMFCRibbonBaseElement::IsLargeMode.md)|表示功能區項目的目前影像是否為完整大小。|  
|[CMFCRibbonBaseElement::IsMenuMode](../Topic/CMFCRibbonBaseElement::IsMenuMode.md)|表示功能區項目是否在功能表中。|  
|[CMFCRibbonBaseElement::IsPressed](../Topic/CMFCRibbonBaseElement::IsPressed.md)|指出使用者是按一下功能區項目。|  
|[CMFCRibbonBaseElement::IsQATMode](../Topic/CMFCRibbonBaseElement::IsQATMode.md)|表示功能區項目是否在快速存取工具列中。|  
|[CMFCRibbonBaseElement::IsSeparator](../Topic/CMFCRibbonBaseElement::IsSeparator.md)|表示功能區項目是否顯示分隔符號。|  
|[CMFCRibbonBaseElement::IsShowGroupBorder](../Topic/CMFCRibbonBaseElement::IsShowGroupBorder.md)|表示功能區項目是否在顯示一般框線的群組中。|  
|[CMFCRibbonBaseElement::IsShowTooltipOnBottom](../Topic/CMFCRibbonBaseElement::IsShowTooltipOnBottom.md)|指出工具提示是否會顯示在功能區項目之下。|  
|[CMFCRibbonBaseElement::IsTabStop](../Topic/CMFCRibbonBaseElement::IsTabStop.md)|表示功能區項目可以選擇是否使用鍵盤。|  
|[CMFCRibbonBaseElement::IsTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::IsTextAlwaysOnRight.md)|表示功能區項目中的文字是否在右邊顯示。|  
|[CMFCRibbonBaseElement::IsVisible](../Topic/CMFCRibbonBaseElement::IsVisible.md)|表示功能區項目目前是否顯示。|  
|[CMFCRibbonBaseElement::IsWholeRowHeight](../Topic/CMFCRibbonBaseElement::IsWholeRowHeight.md)|表示功能區項目的顯示 heigth 是否與包含該功能區面板的顯示高度。|  
|[CMFCRibbonBaseElement::NotifyCommand](../Topic/CMFCRibbonBaseElement::NotifyCommand.md)|會將命令傳送告知給功能區項目的父視窗。|  
|[CMFCRibbonBaseElement::NotifyHighlightListItem](../Topic/CMFCRibbonBaseElement::NotifyHighlightListItem.md)|告知功能區列的父視窗，當使用者在清單中反白顯示的一個功能區項目時。|  
|[CMFCRibbonBaseElement::OnAddToQAToolbar](../Topic/CMFCRibbonBaseElement::OnAddToQAToolbar.md)|將功能區項目加入至指定的快速存取工具列。|  
|[CMFCRibbonBaseElement::OnAfterChangeRect](../Topic/CMFCRibbonBaseElement::OnAfterChangeRect.md)|更新功能區項目的工具提示。|  
|[CMFCRibbonBaseElement::OnAutoRepeat](../Topic/CMFCRibbonBaseElement::OnAutoRepeat.md)|更新功能區項目以回應所維持的使用者輸入。|  
|[CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)|計算文字大小功能區項目的。|  
|[CMFCRibbonBaseElement::OnChangeMenuHighlight](../Topic/CMFCRibbonBaseElement::OnChangeMenuHighlight.md)|呼叫框架，當焦點位於功能表上提供的功能區項目變更。|  
|[CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)|呼叫框架繪製功能區項目。|  
|[CMFCRibbonBaseElement::OnDrawKeyTip](../Topic/CMFCRibbonBaseElement::OnDrawKeyTip.md)|呼叫框架繪製功能區項目的 keytip。|  
|[CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)|呼叫由架構，在繪製功能區項目的功能表影像。|  
|[CMFCRibbonBaseElement::OnDrawOnList](../Topic/CMFCRibbonBaseElement::OnDrawOnList.md)|呼叫框架會在命令清單方塊中的功能區項目。|  
|[CMFCRibbonBaseElement::OnKey](../Topic/CMFCRibbonBaseElement::OnKey.md)|呼叫，便會由架構使用者按下時 keytip 和功能區項目具有焦點。|  
|[CMFCRibbonBaseElement::OnMenuKey](../Topic/CMFCRibbonBaseElement::OnMenuKey.md)||  
|[CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md)|呼叫由架構，在設定重新導向。|  
|[CMFCRibbonBaseElement::OnShow](../Topic/CMFCRibbonBaseElement::OnShow.md)|呼叫由架構來顯示或隱藏功能區項目。|  
|[CMFCRibbonBaseElement::OnShowPopupMenu](../Topic/CMFCRibbonBaseElement::OnShowPopupMenu.md)|呼叫框架，在功能區項目顯示快顯功能表。|  
|[CMFCRibbonBaseElement::PostMenuCommand](../Topic/CMFCRibbonBaseElement::PostMenuCommand.md)||  
|[CMFCRibbonBaseElement::Redraw](../Topic/CMFCRibbonBaseElement::Redraw.md)|更新功能區項目的顯示。|  
|[CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)|設定協助工具資料為功能區項目。|  
|[CMFCRibbonBaseElement::SetCompactMode](../Topic/CMFCRibbonBaseElement::SetCompactMode.md)|將功能區項目的顯示大小。|  
|[CMFCRibbonBaseElement::SetData](../Topic/CMFCRibbonBaseElement::SetData.md)|相關聯的資料項目與功能區項目。|  
|[CMFCRibbonBaseElement::SetDefaultMenuLook](../Topic/CMFCRibbonBaseElement::SetDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)|將功能區項目的描述。|  
|[CMFCRibbonBaseElement::SetID](../Topic/CMFCRibbonBaseElement::SetID.md)|將功能區項目的命令 ID。|  
|[CMFCRibbonBaseElement::SetInitialMode](../Topic/CMFCRibbonBaseElement::SetInitialMode.md)|將功能區項目的初始顯示大小。|  
|[CMFCRibbonBaseElement::SetKeys](../Topic/CMFCRibbonBaseElement::SetKeys.md)|將功能區項目的 keytip。|  
|[CMFCRibbonBaseElement::SetOriginal](../Topic/CMFCRibbonBaseElement::SetOriginal.md)|將功能區項目的功能區項目。|  
|[CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)|將功能區項目的父分類。|  
|[CMFCRibbonBaseElement::SetParentMenu](../Topic/CMFCRibbonBaseElement::SetParentMenu.md)|將功能區項目的父功能表容器。|  
|[CMFCRibbonBaseElement::SetParentRibbonBar](../Topic/CMFCRibbonBaseElement::SetParentRibbonBar.md)|將功能區項目的父功能區列。|  
|[CMFCRibbonBaseElement::SetRect](../Topic/CMFCRibbonBaseElement::SetRect.md)|設定的維度。FOT 顯示功能區項目的矩形。|  
|[CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)|將功能區項目的文字。|  
|[CMFCRibbonBaseElement::SetTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::SetTextAlwaysOnRight.md)|在右邊設定功能區項目的文字顯示。|  
|[CMFCRibbonBaseElement::SetToolTipText](../Topic/CMFCRibbonBaseElement::SetToolTipText.md)|將功能區項目的工具提示文字。|  
|[CMFCRibbonBaseElement::SetVisible](../Topic/CMFCRibbonBaseElement::SetVisible.md)|將功能區項目的可視性狀態。|  
|[CMFCRibbonBaseElement::StretchHorizontally](../Topic/CMFCRibbonBaseElement::StretchHorizontally.md)|自動縮放功能區項目的寬度。|  
|[CMFCRibbonBaseElement::StretchToWholeRow](../Topic/CMFCRibbonBaseElement::StretchToWholeRow.md)|變更功能區項目的顯示高度為指定的資料列高度。|  
|[CMFCRibbonBaseElement::UpdateTooltipInfo](../Topic/CMFCRibbonBaseElement::UpdateTooltipInfo.md)|您可以使用功能區項目的命令，資源更新工具提示文字。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonBaseElement::OnProcessKey](../Topic/CMFCRibbonBaseElement::OnProcessKey.md)|呼叫框架，當使用者按下快速鍵。|  
|[CMFCRibbonBaseElement::OnSetFocus](../Topic/CMFCRibbonBaseElement::OnSetFocus.md)|呼叫框架，在功能區項目接收或失去輸入焦點。|  
  
## 備註  
 `CMFCRibbonBaseElement` 類別定義所有功能區項目的通用包括命令 ID、文字標籤、工具提示文字、項目可以取得焦點時，的描述和狀態的屬性 \(反白顯示，則按下，停用，選取、、或向下\)。  
  
 功能區項目的影像大小是由 `RibbonImageType` 成員定義，可以是下列其中一個值:  
  
-   `RibbonImageLarge`  
  
-   `RibbonImageSmall`  
  
 根據其大小，功能區項目顯示大型或小型影像。  
  
## 範例  
 下列範例會在 `CMFCRibbonBaseElement` 類別會示範如何使用各種方法。  這個範例將示範如何在 `CMFCRibbonStatusBar` 類別取得 `CMFCRibbonBaseElement` 物件，設定功能區項目的描述，請將文字，設定 keytip，並將功能區項目的工具提示文字。  這個程式碼片段是 [繪製用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#8](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_1.cpp)]  
[!code-cpp[NVC_MFC_DrawClient#9](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
## 需求  
 **標題:** afxbaseribbonelement.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)