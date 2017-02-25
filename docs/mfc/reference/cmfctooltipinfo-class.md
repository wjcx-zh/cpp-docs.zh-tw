---
title: "CMFCToolTipInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipInfo class"
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCToolTipInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

儲存工具提示視覺外觀的相關資訊。  
  
## 語法  
  
```  
class CMFCToolTipInfo  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolTipInfo::operator\=](../Topic/CMFCToolTipInfo::operator=.md)||  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolTipInfo::m\_bBalloonTooltip](../Topic/CMFCToolTipInfo::m_bBalloonTooltip.md)|一個布林值變數，指出工具提示是否有氣球外觀。|  
|[CMFCToolTipInfo::m\_bBoldLabel](../Topic/CMFCToolTipInfo::m_bBoldLabel.md)|一個布林值變數，指出工具提示標籤是否以粗體字顯示。|  
|[CMFCToolTipInfo::m\_bDrawDescription](../Topic/CMFCToolTipInfo::m_bDrawDescription.md)|一個布林值變數，指出工具提示是否包含描述。|  
|[CMFCToolTipInfo::m\_bDrawIcon](../Topic/CMFCToolTipInfo::m_bDrawIcon.md)|一個布林值變數，指出工具提示是否包含圖示。|  
|[CMFCToolTipInfo::m\_bDrawSeparator](../Topic/CMFCToolTipInfo::m_bDrawSeparator.md)|一個布林值變數，指出是否要在工具提示標籤與工具提示描述之間顯示分隔符號。|  
|[CMFCToolTipInfo::m\_bRoundedCorners](../Topic/CMFCToolTipInfo::m_bRoundedCorners.md)|一個布林值變數，指出工具提示是否有圓角。|  
|[CMFCToolTipInfo::m\_bVislManagerTheme](../Topic/CMFCToolTipInfo::m_bVislManagerTheme.md)|一個布林值變數，指出工具提示的外觀是否應由視覺管理員控制 \(請參閱 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)\)。|  
|[CMFCToolTipInfo::m\_clrBorder](../Topic/CMFCToolTipInfo::m_clrBorder.md)|工具提示框線的色彩。|  
|[CMFCToolTipInfo::m\_clrFill](../Topic/CMFCToolTipInfo::m_clrFill.md)|工具提示背景的色彩。|  
|[CMFCToolTipInfo::m\_clrFillGradient](../Topic/CMFCToolTipInfo::m_clrFillGradient.md)|工具提示中填入的漸層色彩。|  
|[CMFCToolTipInfo::m\_clrText](../Topic/CMFCToolTipInfo::m_clrText.md)|工具提示的文字色彩。|  
|[CMFCToolTipInfo::m\_nGradientAngle](../Topic/CMFCToolTipInfo::m_nGradientAngle.md)|工具提示中填入的漸層角度。|  
|[CMFCToolTipInfo::m\_nMaxDescrWidth](../Topic/CMFCToolTipInfo::m_nMaxDescrWidth.md)|工具提示描述的最大可能寬度，以像素為單位。|  
  
## 備註  
 同時使用 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)、`CMFCToolTipInfo` 和 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)，在您的應用程式中實作自訂的工具提示。  如需如何使用這些工具提示類別的範例，請參閱 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md) 主題。  
  
## 範例  
 下列範例示範如何設定 `CMFCToolTipInfo` 類別中各種成員變數的值。  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/CPP/cmfctooltipinfo-class_1.cpp)]  
  
## 繼承階層  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## 需求  
 **標頭：**afxtooltipctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)