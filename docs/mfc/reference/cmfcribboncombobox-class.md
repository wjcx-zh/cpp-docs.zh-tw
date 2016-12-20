---
title: "CMFCRibbonComboBox Class | Microsoft Docs"
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
  - "CMFCRibbonComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonComboBox class"
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonComboBox` 類別實作可以加入至功能區列、功能區面板或功能區快顯功能表的下拉式方塊控制項。  
  
## 語法  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## Members  
  
### 建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](../Topic/CMFCRibbonComboBox::CMFCRibbonComboBox.md)|CMFCRibbonComboBox 建構物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonComboBox::AddItem](../Topic/CMFCRibbonComboBox::AddItem.md)|附加唯一的項目加入至清單方塊。|  
|[CMFCRibbonComboBox::DeleteItem](../Topic/CMFCRibbonComboBox::DeleteItem.md)|從清單方塊刪除項目中指定之項目的。|  
|[CMFCRibbonComboBox::EnableDropDownListResize](../Topic/CMFCRibbonComboBox::EnableDropDownListResize.md)|指定清單方塊是否變更大小，會被關閉。|  
|[CMFCRibbonComboBox::FindItem](../Topic/CMFCRibbonComboBox::FindItem.md)|傳回第一個項目的索引符合指定字串的清單方塊中的。|  
|[CMFCRibbonComboBox::GetCount](../Topic/CMFCRibbonComboBox::GetCount.md)|傳回中項目的清單方塊中的。|  
|[CMFCRibbonComboBox::GetCurSel](../Topic/CMFCRibbonComboBox::GetCurSel.md)|取得目前選取之項目的索引在清單方塊中。|  
|[CMFCRibbonComboBox::GetDropDownHeight](../Topic/CMFCRibbonComboBox::GetDropDownHeight.md)|在清單方塊中下拉式時，取得清單方塊的高度。|  
|[CMFCRibbonComboBox::GetIntermediateSize](../Topic/CMFCRibbonComboBox::GetIntermediateSize.md)|傳回下拉式方塊的大小來顯示在中間的方式。|  
|[CMFCRibbonComboBox::GetItem](../Topic/CMFCRibbonComboBox::GetItem.md)|傳回字串與項目在清單方塊中的指定索引處的。|  
|[CMFCRibbonComboBox::GetItemData](../Topic/CMFCRibbonComboBox::GetItemData.md)|傳回資料與指定的項目在清單方塊中的指定索引處的。|  
|[CMFCRibbonComboBox::HasEditBox](../Topic/CMFCRibbonComboBox::HasEditBox.md)|表示控制項是否包含的編輯方塊。|  
|[CMFCRibbonComboBox::IsResizeDropDownList](../Topic/CMFCRibbonComboBox::IsResizeDropDownList.md)|清單方塊是否可以調整大小。|  
|[CMFCRibbonComboBox::OnSelectItem](../Topic/CMFCRibbonComboBox::OnSelectItem.md)|呼叫框架，當使用者選取清單方塊中的項目。|  
|[CMFCRibbonComboBox::RemoveAllItems](../Topic/CMFCRibbonComboBox::RemoveAllItems.md)|從清單方塊刪除項目的所有項目並清除  編輯方塊。|  
|[CMFCRibbonComboBox::SelectItem](../Topic/CMFCRibbonComboBox::SelectItem.md)|選取清單方塊中的項目。|  
|[CMFCRibbonComboBox::SetDropDownHeight](../Topic/CMFCRibbonComboBox::SetDropDownHeight.md)|會下拉時，將清單方塊的高度。|  
  
## 備註  
 功能區上下拉式方塊包含清單方塊結合使用者可以編輯的靜態 \(Static\) 標籤或標籤。  您必須指定哪一個型別，您需要在建立自己的功能區上下拉式方塊時。  
  
## 範例  
 下列範例示範如何建構物件 `CMFCRibbonComboBox` 類別，將項目加入至下拉式方塊中，選取  下拉式方塊中的項目並將下拉式方塊加入面板。  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/CPP/cmfcribboncombobox-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## 需求  
 **標題:** afxribboncombobox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit Class](../../mfc/reference/cmfcribbonedit-class.md)