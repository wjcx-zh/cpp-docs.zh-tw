---
title: "CMFCRibbonCategory Class | Microsoft Docs"
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
  - "CMFCRibbonCategory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonCategory class"
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
caps.latest.revision: 38
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonCategory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonCategory` 類別實作包含一組 [功能區面板](../../mfc/reference/cmfcribbonpanel-class.md)的功能區索引標籤。  
  
## 語法  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](../Topic/CMFCRibbonCategory::CMFCRibbonCategory.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonCategory::AddHidden](../Topic/CMFCRibbonCategory::AddHidden.md)|加入一個隱藏的項目加入至功能區類別。|  
|[CMFCRibbonCategory::AddPanel](../Topic/CMFCRibbonCategory::AddPanel.md)|加入新的面板加入至功能區類別。|  
|[CMFCRibbonCategory::CopyFrom](../Topic/CMFCRibbonCategory::CopyFrom.md)||  
|[CMFCRibbonCategory::FindByData](../Topic/CMFCRibbonCategory::FindByData.md)||  
|[CMFCRibbonCategory::FindByID](../Topic/CMFCRibbonCategory::FindByID.md)||  
|[CMFCRibbonCategory::FindPanelWithElem](../Topic/CMFCRibbonCategory::FindPanelWithElem.md)||  
|[CMFCRibbonCategory::GetContextID](../Topic/CMFCRibbonCategory::GetContextID.md)|傳回功能區類別的內容 ID。|  
|[CMFCRibbonCategory::GetData](../Topic/CMFCRibbonCategory::GetData.md)|傳回與功能區類別的使用者定義的資料。|  
|[CMFCRibbonCategory::GetDroppedDown](../Topic/CMFCRibbonCategory::GetDroppedDown.md)||  
|[CMFCRibbonCategory::GetElements](../Topic/CMFCRibbonCategory::GetElements.md)||  
|[CMFCRibbonCategory::GetElementsByID](../Topic/CMFCRibbonCategory::GetElementsByID.md)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](../Topic/CMFCRibbonCategory::GetFirstVisibleElement.md)|取得屬於功能區類別的第一個可見的項目。|  
|[CMFCRibbonCategory::GetFocused](../Topic/CMFCRibbonCategory::GetFocused.md)|傳回一個可焦點化項目。|  
|[CMFCRibbonCategory::GetHighlighted](../Topic/CMFCRibbonCategory::GetHighlighted.md)|傳回一個反白顯示的項目。|  
|[CMFCRibbonCategory::GetImageCount](../Topic/CMFCRibbonCategory::GetImageCount.md)||  
|[CMFCRibbonCategory::GetImageSize](../Topic/CMFCRibbonCategory::GetImageSize.md)||  
|[CMFCRibbonCategory::GetItemIDsList](../Topic/CMFCRibbonCategory::GetItemIDsList.md)||  
|[CMFCRibbonCategory::GetLastVisibleElement](../Topic/CMFCRibbonCategory::GetLastVisibleElement.md)|取得屬於功能區類別中的最後一個可見的項目|  
|[CMFCRibbonCategory::GetLargeImages](../Topic/CMFCRibbonCategory::GetLargeImages.md)|傳回功能區類別使用大型影像清單的參考。|  
|[CMFCRibbonCategory::GetMaxHeight](../Topic/CMFCRibbonCategory::GetMaxHeight.md)||  
|[CMFCRibbonCategory::GetName](../Topic/CMFCRibbonCategory::GetName.md)||  
|[CMFCRibbonCategory::GetPanel](../Topic/CMFCRibbonCategory::GetPanel.md)|傳回指向位於指定索引的功能區面板。|  
|[CMFCRibbonCategory::GetPanelCount](../Topic/CMFCRibbonCategory::GetPanelCount.md)|傳回功能區面板數目功能區類別的。|  
|[CMFCRibbonCategory::GetPanelFromPoint](../Topic/CMFCRibbonCategory::GetPanelFromPoint.md)||  
|[CMFCRibbonCategory::GetPanelIndex](../Topic/CMFCRibbonCategory::GetPanelIndex.md)|傳回指定之功能區面板的索引。|  
|[CMFCRibbonCategory::GetParentButton](../Topic/CMFCRibbonCategory::GetParentButton.md)||  
|[CMFCRibbonCategory::GetParentMenuBar](../Topic/CMFCRibbonCategory::GetParentMenuBar.md)||  
|[CMFCRibbonCategory::GetParentRibbonBar](../Topic/CMFCRibbonCategory::GetParentRibbonBar.md)||  
|[CMFCRibbonCategory::GetRect](../Topic/CMFCRibbonCategory::GetRect.md)||  
|[CMFCRibbonCategory::GetSmallImages](../Topic/CMFCRibbonCategory::GetSmallImages.md)|傳回類別使用小型影像清單的參考。|  
|[CMFCRibbonCategory::GetTabColor](../Topic/CMFCRibbonCategory::GetTabColor.md)|傳回功能區類別索引標籤的目前色彩。|  
|[CMFCRibbonCategory::GetTabRect](../Topic/CMFCRibbonCategory::GetTabRect.md)||  
|[CMFCRibbonCategory::GetTextTopLine](../Topic/CMFCRibbonCategory::GetTextTopLine.md)||  
|[CMFCRibbonCategory::GetVisibleElements](../Topic/CMFCRibbonCategory::GetVisibleElements.md)|取得屬於功能區類別中的所有可見的項目。|  
|[CMFCRibbonCategory::HighlightPanel](../Topic/CMFCRibbonCategory::HighlightPanel.md)||  
|[CMFCRibbonCategory::HitTest](../Topic/CMFCRibbonCategory::HitTest.md)||  
|[CMFCRibbonCategory::HitTestEx](../Topic/CMFCRibbonCategory::HitTestEx.md)||  
|[CMFCRibbonCategory::HitTestScrollButtons](../Topic/CMFCRibbonCategory::HitTestScrollButtons.md)||  
|[CMFCRibbonCategory::IsActive](../Topic/CMFCRibbonCategory::IsActive.md)||  
|[CMFCRibbonCategory::IsVisible](../Topic/CMFCRibbonCategory::IsVisible.md)|判斷功能區類別是否為可見。|  
|[CMFCRibbonCategory::IsWindows7Look](../Topic/CMFCRibbonCategory::IsWindows7Look.md)|表示父功能區是否有 Windows 7 樣式的外觀 \(小矩形應用程式按鈕\)|  
|[CMFCRibbonCategory::NotifyControlCommand](../Topic/CMFCRibbonCategory::NotifyControlCommand.md)||  
|[CMFCRibbonCategory::OnCancelMode](../Topic/CMFCRibbonCategory::OnCancelMode.md)||  
|[CMFCRibbonCategory::OnDraw](../Topic/CMFCRibbonCategory::OnDraw.md)||  
|[CMFCRibbonCategory::OnDrawImage](../Topic/CMFCRibbonCategory::OnDrawImage.md)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](../Topic/CMFCRibbonCategory::OnDrawMenuBorder.md)||  
|[CMFCRibbonCategory::OnKey](../Topic/CMFCRibbonCategory::OnKey.md)|呼叫框架，當使用者按下某個鍵盤按鍵。|  
|[CMFCRibbonCategory::OnLButtonDown](../Topic/CMFCRibbonCategory::OnLButtonDown.md)||  
|[CMFCRibbonCategory::OnLButtonUp](../Topic/CMFCRibbonCategory::OnLButtonUp.md)||  
|[CMFCRibbonCategory::OnMouseMove](../Topic/CMFCRibbonCategory::OnMouseMove.md)||  
|[CMFCRibbonCategory::OnRTLChanged](../Topic/CMFCRibbonCategory::OnRTLChanged.md)||  
|[CMFCRibbonCategory::OnScrollHorz](../Topic/CMFCRibbonCategory::OnScrollHorz.md)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](../Topic/CMFCRibbonCategory::OnUpdateCmdUI.md)||  
|[CMFCRibbonCategory::RecalcLayout](../Topic/CMFCRibbonCategory::RecalcLayout.md)||  
|[CMFCRibbonCategory::RemovePanel](../Topic/CMFCRibbonCategory::RemovePanel.md)||  
|[CMFCRibbonCategory::ReposPanels](../Topic/CMFCRibbonCategory::ReposPanels.md)||  
|[CMFCRibbonCategory::SetCollapseOrder](../Topic/CMFCRibbonCategory::SetCollapseOrder.md)|定義出現在功能區類別功能區面板中摺疊順序。|  
|[CMFCRibbonCategory::SetData](../Topic/CMFCRibbonCategory::SetData.md)|在功能區類別儲存使用者定義的資料。|  
|[CMFCRibbonCategory::SetKeys](../Topic/CMFCRibbonCategory::SetKeys.md)|keytip 指派給功能區類別。|  
|[CMFCRibbonCategory::SetName](../Topic/CMFCRibbonCategory::SetName.md)||  
|[CMFCRibbonCategory::SetTabColor](../Topic/CMFCRibbonCategory::SetTabColor.md)|將功能區類別的色彩。|  
  
## 備註  
 通常，您會呼叫 [CMFCRibbonBar::AddCategory](../Topic/CMFCRibbonBar::AddCategory.md)間接建立功能區類別，傳回指向新建立的功能區類別。  您可將面板加入類別會藉由呼叫 [CMFCRibbonCategory::AddPanel](../Topic/CMFCRibbonCategory::AddPanel.md)。  
  
 `CMFCRibbonTab` 類別繪製功能區類別。  它會從 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)衍生。  
  
 這個以下的範例將示範如何建立功能區類別並將面板加入它。  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 下圖顯示 Home 分類的嘗試從 RibbonApp 範例應用程式的。  
  
 ![CMFCRibbonCategory 影像](../Image/CMFCRibbonCategory.png "CMFCRibbonCategory")  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)  
  
## 需求  
 **標題:** afxribboncategory.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)