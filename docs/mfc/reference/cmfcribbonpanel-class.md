---
title: "CMFCRibbonPanel Class | Microsoft Docs"
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
  - "CMFCRibbonPanel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonPanel class"
ms.assetid: 51d70749-1140-4386-b103-f14082049ba6
caps.latest.revision: 34
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonPanel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作包含一組功能區項目的面板。  在繪製面板時，會顯示多個元素盡可能將面板的大小。  
  
## 語法  
  
```  
class CMFCRibbonPanel : public CObject  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonPanel::CMFCRibbonPanel](../Topic/CMFCRibbonPanel::CMFCRibbonPanel.md)|建構和 `CMFCRibbonPanel` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md)|將功能區項目加入面板。|  
|[CMFCRibbonPanel::AddSeparator](../Topic/CMFCRibbonPanel::AddSeparator.md)|將分隔符號加入至功能區面板。|  
|[CMFCRibbonPanel::AddToolBar](../Topic/CMFCRibbonPanel::AddToolBar.md)|將工具列加入至功能區面板。|  
|[CMFCRibbonPanel::FindByData](../Topic/CMFCRibbonPanel::FindByData.md)||  
|[CMFCRibbonPanel::FindByID](../Topic/CMFCRibbonPanel::FindByID.md)|傳回指定的命令 ID. 判斷的項目|  
|[CMFCRibbonPanel::GetCaptionHeight](../Topic/CMFCRibbonPanel::GetCaptionHeight.md)||  
|[CMFCRibbonPanel::GetCount](../Topic/CMFCRibbonPanel::GetCount.md)|傳回的項目數功能區面板的。|  
|[CMFCRibbonPanel::GetData](../Topic/CMFCRibbonPanel::GetData.md)|傳回使用者定義的資料與指定的面板。|  
|[CMFCRibbonPanel::GetDefaultButton](../Topic/CMFCRibbonPanel::GetDefaultButton.md)||  
|[CMFCRibbonPanel::GetDroppedDown](../Topic/CMFCRibbonPanel::GetDroppedDown.md)||  
|[CMFCRibbonPanel::GetElement](../Topic/CMFCRibbonPanel::GetElement.md)|傳回功能區項目位於指定索引處。|  
|[CMFCRibbonPanel::GetElements](../Topic/CMFCRibbonPanel::GetElements.md)|擷取功能區面板內的所有項目。|  
|[CMFCRibbonPanel::GetElementsByID](../Topic/CMFCRibbonPanel::GetElementsByID.md)||  
|[CMFCRibbonPanel::GetFocused](../Topic/CMFCRibbonPanel::GetFocused.md)|傳回一個可焦點化項目。|  
|[CMFCRibbonPanel::GetGalleryRect](../Topic/CMFCRibbonPanel::GetGalleryRect.md)|傳回陳列庫項目的週框 \(Bounding Rectangle\)。|  
|[CMFCRibbonPanel::GetHighlighted](../Topic/CMFCRibbonPanel::GetHighlighted.md)||  
|[CMFCRibbonPanel::GetIndex](../Topic/CMFCRibbonPanel::GetIndex.md)||  
|[CMFCRibbonPanel::GetItemIDsList](../Topic/CMFCRibbonPanel::GetItemIDsList.md)||  
|[CMFCRibbonPanel::GetName](../Topic/CMFCRibbonPanel::GetName.md)||  
|[CMFCRibbonPanel::GetParentButton](../Topic/CMFCRibbonPanel::GetParentButton.md)||  
|[CMFCRibbonPanel::GetParentCategory](../Topic/CMFCRibbonPanel::GetParentCategory.md)|傳回功能區面板的父分類。|  
|[CMFCRibbonPanel::GetParentMenuBar](../Topic/CMFCRibbonPanel::GetParentMenuBar.md)||  
|[CMFCRibbonPanel::GetPreferedMenuLocation](../Topic/CMFCRibbonPanel::GetPreferedMenuLocation.md)||  
|[CMFCRibbonPanel::GetPressed](../Topic/CMFCRibbonPanel::GetPressed.md)||  
|[CMFCRibbonPanel::GetRect](../Topic/CMFCRibbonPanel::GetRect.md)||  
|[CMFCRibbonPanel::GetVisibleElements](../Topic/CMFCRibbonPanel::GetVisibleElements.md)|取得陣列中可見的項目。|  
|[CMFCRibbonPanel::HasElement](../Topic/CMFCRibbonPanel::HasElement.md)||  
|[CMFCRibbonPanel::HitTest](../Topic/CMFCRibbonPanel::HitTest.md)||  
|[CMFCRibbonPanel::HitTestEx](../Topic/CMFCRibbonPanel::HitTestEx.md)||  
|[CMFCRibbonPanel::Insert](../Topic/CMFCRibbonPanel::Insert.md)|將功能區項目在指定的位置。|  
|[CMFCRibbonPanel::InsertSeparator](../Topic/CMFCRibbonPanel::InsertSeparator.md)|插入分隔符號在指定的位置。|  
|[CMFCRibbonPanel::IsCenterColumnVert](../Topic/CMFCRibbonPanel::IsCenterColumnVert.md)|依資料行指定是否應該垂直置中所有面板項目 \(對齊\)。|  
|[CMFCRibbonPanel::IsCollapsed](../Topic/CMFCRibbonPanel::IsCollapsed.md)||  
|[CMFCRibbonPanel::IsHighlighted](../Topic/CMFCRibbonPanel::IsHighlighted.md)||  
|[CMFCRibbonPanel::IsJustifyColumns](../Topic/CMFCRibbonPanel::IsJustifyColumns.md)|指定所有面板資料行是否具有相同的寬度。|  
|[CMFCRibbonPanel::IsMainPanel](../Topic/CMFCRibbonPanel::IsMainPanel.md)||  
|[CMFCRibbonPanel::IsMenuMode](../Topic/CMFCRibbonPanel::IsMenuMode.md)||  
|[CMFCRibbonPanel::MakeGalleryItemVisible](../Topic/CMFCRibbonPanel::MakeGalleryItemVisible.md)|將這個一般模式庫可指定功能區項目可見。|  
|[CMFCRibbonPanel::OnKey](../Topic/CMFCRibbonPanel::OnKey.md)||  
|[CMFCRibbonPanel::RecalcWidths](../Topic/CMFCRibbonPanel::RecalcWidths.md)||  
|[CMFCRibbonPanel::Remove](../Topic/CMFCRibbonPanel::Remove.md)|移除和選擇性地刪除項目位在指定索引處。|  
|[CMFCRibbonPanel::RemoveAll](../Topic/CMFCRibbonPanel::RemoveAll.md)|從功能區面板的所有項目。|  
|[CMFCRibbonPanel::Replace](../Topic/CMFCRibbonPanel::Replace.md)|這會根據其各自的索引值的取代項目。|  
|[CMFCRibbonPanel::ReplaceByID](../Topic/CMFCRibbonPanel::ReplaceByID.md)|會根據指定的命令 ID. 的取代項目|  
|[CMFCRibbonPanel::SetCenterColumnVert](../Topic/CMFCRibbonPanel::SetCenterColumnVert.md)|排序面板是資料行垂直對齊項目。|  
|[CMFCRibbonPanel::SetData](../Topic/CMFCRibbonPanel::SetData.md)|相關聯的使用者定義的資料與功能區面板。|  
|[CMFCRibbonPanel::SetElementMenu](../Topic/CMFCRibbonPanel::SetElementMenu.md)|將快顯功能表會具有指定的命令 ID. 的項目|  
|[CMFCRibbonPanel::SetElementRTC](../Topic/CMFCRibbonPanel::SetElementRTC.md)|將所提供的執行階段類別指定資訊的一個功能區項目加入至功能區面板。|  
|[CMFCRibbonPanel::SetElementRTCByID](../Topic/CMFCRibbonPanel::SetElementRTCByID.md)|將所提供的執行階段類別指定資訊的一個功能區項目加入至功能區面板。|  
|[CMFCRibbonPanel::SetFocused](../Topic/CMFCRibbonPanel::SetFocused.md)|會將焦點設定至指定功能區項目。|  
|[CMFCRibbonPanel::SetJustifyColumns](../Topic/CMFCRibbonPanel::SetJustifyColumns.md)|啟用或停用資料行對齊。|  
|[CMFCRibbonPanel::SetKeys](../Topic/CMFCRibbonPanel::SetKeys.md)|設定顯示功能區面板的鍵盤快速鍵。|  
|[CMFCRibbonPanel::ShowPopup](../Topic/CMFCRibbonPanel::ShowPopup.md)||  
  
## 備註  
 功能區面板是您在功能區類別中建立相關工作的邏輯群組。  當功能區的大小變更，面板配置自動調整顯示多個元素越好。  
  
 在功能區類別包含可藉由呼叫方法 [CMFCRibbonCategory::GetPanel](../Topic/CMFCRibbonCategory::GetPanel.md) 便可取得功能區面板。  
  
## 範例  
 您可以使用類別，在 `CMFCRibbonPanel` 的各種方法。下列範例將示範如何設定 `CMFCRibbonPanel` 物件。  這個範例顯示如何設定顯示功能區面板的鍵盤快速鍵，是由資料行的垂直對齊面板的項目，並且啟用資料行對齊。  這個程式碼片段是 [MS Office 2007 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_MSOffice2007Demo#10](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#10)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
## 需求  
 **標題:** afxRibbonPanel.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)