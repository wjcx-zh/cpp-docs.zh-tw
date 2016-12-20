---
title: "CMFCToolBarComboBoxButton Class | Microsoft Docs"
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
  - "CMFCToolBarComboBoxButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarComboBoxButton class"
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 30
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarComboBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含下拉式方塊控制項的工具列按鈕 \([CComboBox Class](../../mfc/reference/ccombobox-class.md)\)。  
  
## 語法  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](../Topic/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton.md)|建構 `CMFCToolBarComboBoxButton`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarComboBoxButton::AddItem](../Topic/CMFCToolBarComboBoxButton::AddItem.md)|將項目加入至結尾的下拉式方塊清單。|  
|[CMFCToolBarComboBoxButton::AddSortedItem](../Topic/CMFCToolBarComboBoxButton::AddSortedItem.md)|加入項目至下拉式方塊清單。  中的項目順序清單中的 `Compare`由指定。|  
|[CMFCToolBarComboBoxButton::Compare](../Topic/CMFCToolBarComboBoxButton::Compare.md)|比較兩個項目。  呼叫 `AddSortedItems` 排序加入至下拉式方塊清單中的項目。|  
|[CMFCToolBarComboBoxButton::CreateEdit](../Topic/CMFCToolBarComboBoxButton::CreateEdit.md)|建立下拉式方塊按鈕的新編輯控制項。|  
|[CMFCToolBarComboBoxButton::DeleteItem](../Topic/CMFCToolBarComboBoxButton::DeleteItem.md)|刪除下拉式方塊清單中的項目。|  
|[CMFCToolBarComboBoxButton::FindItem](../Topic/CMFCToolBarComboBoxButton::FindItem.md)|傳回包含指定字串項目的索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](../Topic/CMFCToolBarComboBoxButton::GetByCmd.md)|會將指標傳至具有指定的命令 ID. 的下拉式方塊按鈕|  
|[CMFCToolBarComboBoxButton::GetComboBox](../Topic/CMFCToolBarComboBoxButton::GetComboBox.md)|傳回指向儲存在下拉式方塊按鈕中內嵌的下拉式方塊控制項。|  
|[CMFCToolBarComboBoxButton::GetCount](../Topic/CMFCToolBarComboBoxButton::GetCount.md)|傳回集合中的項目數目下拉式方塊清單中。|  
|[CMFCToolBarComboBoxButton::GetCountAll](../Topic/CMFCToolBarComboBoxButton::GetCountAll.md)|尋找具有指定的命令 ID. 的下拉式方塊按鈕  傳回的項目數該按鈕下拉式方塊清單中。|  
|[CMFCToolBarComboBoxButton::GetCurSel](../Topic/CMFCToolBarComboBoxButton::GetCurSel.md)|傳回選取項目的索引下拉式方塊清單中。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](../Topic/CMFCToolBarComboBoxButton::GetCurSelAll.md)|尋找具有指定的命令 ID 的下拉式方塊按鈕，並傳回選取項目的索引是在該按鈕下拉式方塊清單中。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](../Topic/CMFCToolBarComboBoxButton::GetEditCtrl.md)|會將指標傳至下拉式方塊按鈕內嵌的編輯控制項。|  
|[CMFCToolBarComboBoxButton::GetItem](../Topic/CMFCToolBarComboBoxButton::GetItem.md)|傳回與下拉式方塊清單中指定索引處的字串。|  
|[CMFCToolBarComboBoxButton::GetItemAll](../Topic/CMFCToolBarComboBoxButton::GetItemAll.md)|尋找具有指定的命令 ID 的下拉式方塊按鈕，並傳回與該按鈕下拉式方塊清單的索引的字串。|  
|[CMFCToolBarComboBoxButton::GetItemData](../Topic/CMFCToolBarComboBoxButton::GetItemData.md)|傳回與下拉式方塊清單中指定索引處的 32 位元值。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataAll.md)|尋找具有指定的命令 ID 的下拉式方塊按鈕，並傳回與該按鈕下拉式方塊清單的索引為 32 位元值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataPtrAll.md)|尋找具有指定的命令 ID. 的下拉式方塊按鈕  擷取與該按鈕下拉式方塊清單的索引為 32 位元值，並傳回 32 位元的值做為指標。|  
|[CMFCToolBarComboBoxButton::GetText](../Topic/CMFCToolBarComboBoxButton::GetText.md)|傳回從下拉式方塊中的編輯控制項的文字。|  
|[CMFCToolBarComboBoxButton::GetTextAll](../Topic/CMFCToolBarComboBoxButton::GetTextAll.md)|尋找具有指定的命令 ID 的下拉式方塊中的  按鈕，然後傳回該按鈕編輯控制項的文字。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](../Topic/CMFCToolBarComboBoxButton::IsCenterVert.md)|判斷應用程式的下拉式方塊按鈕是否置中或對齊工具列的上方。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](../Topic/CMFCToolBarComboBoxButton::IsFlatMode.md)|判斷應用程式的下拉式方塊按鈕是否具有平面外觀。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](../Topic/CMFCToolBarComboBoxButton::RemoveAllItems.md)|從下拉式方塊的清單方塊和編輯控制項中移除所有項目。|  
|[CMFCToolBarComboBoxButton::SelectItem](../Topic/CMFCToolBarComboBoxButton::SelectItem.md)|根據索引、32 位元值或字串選取下拉式方塊中的項目，並通知有關選取範圍的下拉式方塊控制項。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](../Topic/CMFCToolBarComboBoxButton::SelectItemAll.md)|尋找具有指定的命令 ID. 的下拉式方塊按鈕  呼叫 `SelectItem` 根據其字串、索引或 32 位元值選取下拉式方塊中的項目該按鈕。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](../Topic/CMFCToolBarComboBoxButton::SetCenterVert.md)|指定應用程式的下拉式方塊按鈕是否垂直置中或對齊工具列的上方。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](../Topic/CMFCToolBarComboBoxButton::SetDropDownHeight.md)|組態下拉式清單方塊的高度。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](../Topic/CMFCToolBarComboBoxButton::SetFlatMode.md)|指定應用程式的下拉式方塊按鈕是否具有平面外觀。|  
  
## 備註  
 若要加入下拉式方塊按鈕加入至工具列，請依照下列步驟執行:  
  
 1.  為按鈕保留虛擬資源 ID 在父代 \(Parent\) 工具列資源。  
  
 2.  建構 `CMFCToolBarComboBoxButton` 物件。  
  
 3.  您可以使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在處理 `AFX_WM_RESETTOOLBAR` 訊息的訊息處理常式，以新的下拉式方塊按鈕取代空的按鈕。  
  
 如需詳細資訊，請參閱 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  如需下拉式方塊工具列按鈕的範例，請參閱範例專案 VisualStudioDemo。  
  
## 範例  
 下列範例會在 `CMFCToolBarComboBoxButton` 類別會示範如何使用各種方法。  這個範例示範如何啟用編輯和下拉式方塊，設定下拉式方塊按鈕的垂直位置在應用程式中，設定清單方塊的高度，並在其下拉時，設定下拉式方塊按鈕平面樣式外觀在應用程式中，並設定下拉式方塊按鈕上的編輯方塊中的文字。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## 需求  
 **標題:** afxtoolbarcomboboxbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)