---
title: "CMFCRibbonProgressBar Class | Microsoft Docs"
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
  - "CMFCRibbonProgressBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonProgressBar class"
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonProgressBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作以視覺方式指出長時間作業的進度的控制項。  
  
## 語法  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](../Topic/CMFCRibbonProgressBar::CMFCRibbonProgressBar.md)|建構和 `CMFCRibbonProgressBar` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonProgressBar::GetPos](../Topic/CMFCRibbonProgressBar::GetPos.md)|傳回目前進度。|  
|[CMFCRibbonProgressBar::GetRangeMax](../Topic/CMFCRibbonProgressBar::GetRangeMax.md)|傳回目前範圍的最大值。|  
|[CMFCRibbonProgressBar::GetRangeMin](../Topic/CMFCRibbonProgressBar::GetRangeMin.md)|傳回目前範圍的最小值。|  
|[CMFCRibbonProgressBar::GetRegularSize](../Topic/CMFCRibbonProgressBar::GetRegularSize.md)|傳回功能區項目的一般大小。  \(覆寫 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)\)。|  
|[CMFCRibbonProgressBar::IsInfiniteMode](../Topic/CMFCRibbonProgressBar::IsInfiniteMode.md)|指定進度列是否在無限的模式下運作。|  
|[CMFCRibbonProgressBar::OnDraw](../Topic/CMFCRibbonProgressBar::OnDraw.md)|呼叫框架繪製功能區項目。  \(覆寫 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)\)。|  
|[CMFCRibbonProgressBar::SetInfiniteMode](../Topic/CMFCRibbonProgressBar::SetInfiniteMode.md)|在無限模式下設定進度列工作。|  
|[CMFCRibbonProgressBar::SetPos](../Topic/CMFCRibbonProgressBar::SetPos.md)|若要設定使用中處理序。|  
|[CMFCRibbonProgressBar::SetRange](../Topic/CMFCRibbonProgressBar::SetRange.md)|設定的最小和最大值。|  
  
## 備註  
 `CMFCRibbonProgressBar` 是兩種模式下運作:規則和無限大。  以一般模式，，當到達最大值，進度列由左到右填滿而停止。  在無限的模式，進度列會從最小值重複已填入到最大的值。  您可以使用無限方式表示作業是持續的，不過，完成時間是未知的。  
  
## 範例  
 下列範例會在 `CMFCRibbonProgressBar` 類別會示範如何使用各種方法。  這個範例會在無限模式顯示如何設定進度列工作 \(其中作業的完成時間未知\)，設定最小和最大值進度列的，並設定進度列的目前位置。  這個程式碼片段是 [MS Office 2007 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_MSOffice2007Demo#11](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#11)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## 需求  
 **標題:** afxRibbonProgressBar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)