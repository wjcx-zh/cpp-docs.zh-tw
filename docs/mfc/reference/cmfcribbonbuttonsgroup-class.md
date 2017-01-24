---
title: "CMFCRibbonButtonsGroup 類別 | Microsoft Docs"
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
  - "CMFCRibbonButtonsGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButtonsGroup 類別"
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonButtonsGroup 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonButtonsGroup` 類別可讓您組織的一組功能區按鈕為群組。  所有按鈕在群組中水平地直接彼此相鄰和置於邊界。  
  
## 語法  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](../Topic/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup.md)|建構 `CMFCRibbonButtonsGroup` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonButtonsGroup::AddButton](../Topic/CMFCRibbonButtonsGroup::AddButton.md)|將按鈕加入至群組。|  
|[CMFCRibbonButtonsGroup::AddButtons](../Topic/CMFCRibbonButtonsGroup::AddButtons.md)|將按鈕清單加入至群組。|  
|[CMFCRibbonButtonsGroup::GetButton](../Topic/CMFCRibbonButtonsGroup::GetButton.md)|將指標傳回至位於指定索引處的按鈕。|  
|[CMFCRibbonButtonsGroup::GetCount](../Topic/CMFCRibbonButtonsGroup::GetCount.md)|在群組中傳回按鈕的數目。|  
|[CMFCRibbonButtonsGroup::GetImageSize](../Topic/CMFCRibbonButtonsGroup::GetImageSize.md)|在功能區群組 \(覆寫 [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)中傳回一般影像的影像大小\)。|  
|[CMFCRibbonButtonsGroup::GetRegularSize](../Topic/CMFCRibbonButtonsGroup::GetRegularSize.md)|傳回功能區項目 \(覆寫 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)的一般大小\)。|  
|[CMFCRibbonButtonsGroup::HasImages](../Topic/CMFCRibbonButtonsGroup::HasImages.md)|報告 `CMFCRibbonButtonsGroup` 物件是否包含工具列影像。|  
|[CMFCRibbonButtonsGroup::OnDrawImage](../Topic/CMFCRibbonButtonsGroup::OnDrawImage.md)|繪製指定按鈕的適當的影像，取決於按鈕是否為一般，反白顯示或停用。|  
|[CMFCRibbonButtonsGroup::RemoveAll](../Topic/CMFCRibbonButtonsGroup::RemoveAll.md)|從 `CMFCRibbonButtonsGroup` 物件移除所有按鈕。|  
|[CMFCRibbonButtonsGroup::SetImages](../Topic/CMFCRibbonButtonsGroup::SetImages.md)|將影像指派給群組。|  
|[CMFCRibbonButtonsGroup::SetParentCategory](../Topic/CMFCRibbonButtonsGroup::SetParentCategory.md)|在其中設定 `CMFCRibbonButtonsGroup` 物件的父代 `CMFCRibbonCategory` 和所有按鈕 \(覆寫 [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)\)。|  
  
## 備註  
 群組衍生自 [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) 的類別，並可用來做為單一實體。  您可以在任何面板或快顯功能表可以將群組。  
  
## 範例  
 下列範例在 `CMFCRibbonButtonsGroup` 類別示範如何使用各種方法。  這個範例顯示如何建構 `CMFCRibbonButtonsGroup` 物件，將影像指派給功能區按鈕群組和將按鈕加入至功能區按鈕的群組。  這個程式碼片段是 [繪製用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/CPP/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## 需求  
 **標題:** afxribbonbuttonsgroup.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)