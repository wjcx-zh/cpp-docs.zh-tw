---
title: "CMFCRibbonStatusBarPane Class | Microsoft Docs"
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
  - "CMFCRibbonStatusBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBarPane class"
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonStatusBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonStatusBarPane` 類別實作可以加入至功能區顯示在狀態列的一個功能區項目。  
  
## 語法  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](../Topic/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane.md)|建構和 `CMFCRibbonStatusBarPane` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::GetAlmostLargeText.md)|傳回定義最長的文字字串在窗格中顯示，但不會攔截的字串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](../Topic/CMFCRibbonStatusBarPane::GetTextAlign.md)|傳回文字對齊的目前設定。|  
|[CMFCRibbonStatusBarPane::IsAnimation](../Topic/CMFCRibbonStatusBarPane::IsAnimation.md)|決定動畫是否正在進行中。|  
|[CMFCRibbonStatusBarPane::IsExtended](../Topic/CMFCRibbonStatusBarPane::IsExtended.md)|判斷窗格是否位於功能區狀態列的擴充區域。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](../Topic/CMFCRibbonStatusBarPane::OnDrawBorder.md)|\(覆寫 [CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md)\)。|  
|[CMFCRibbonStatusBarPane::OnFillBackground](../Topic/CMFCRibbonStatusBarPane::OnFillBackground.md)|\(覆寫 [CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md)\)。|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::SetAlmostLargeText.md)|定義會在窗格中顯示，但不會攔截的最長的文字字串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](../Topic/CMFCRibbonStatusBarPane::SetAnimationList.md)|指派給窗格可用於動畫使用的影像清單。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](../Topic/CMFCRibbonStatusBarPane::SetTextAlign.md)|將文字對齊。|  
|[CMFCRibbonStatusBarPane::StartAnimation](../Topic/CMFCRibbonStatusBarPane::StartAnimation.md)|開始指派至  窗格中的動畫。|  
|[CMFCRibbonStatusBarPane::StopAnimation](../Topic/CMFCRibbonStatusBarPane::StopAnimation.md)|停止指派至窗格的動畫。  .|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](../Topic/CMFCRibbonStatusBarPane::OnFinishAnimation.md)|呼叫框架，將指派至窗格的動畫停止。|  
  
## 範例  
 下列範例會在 `CMFCRibbonStatusBarPane` 類別會示範如何使用各種方法。  這個範例顯示如何建構 `CMFCRibbonStatusBarPane` 物件，將狀態列窗格的標籤文字對齊方式，定義在狀態列窗格，而不會攔截到，狀態列窗格的附加可以顯示影像清單可用於動畫使用，並啟動動畫的最長的文字。  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## 需求  
 **標題:** afxribbonstatusbarpane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar Class](../../mfc/reference/cmfcribbonstatusbar-class.md)