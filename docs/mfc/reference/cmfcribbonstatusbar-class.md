---
title: "CMFCRibbonStatusBar Class | Microsoft Docs"
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
  - "CMFCRibbonStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBar class"
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonStatusBar` 類別實作可以顯示功能區項目的狀態列控制項。  
  
## 語法  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonStatusBar::AddDynamicElement](../Topic/CMFCRibbonStatusBar::AddDynamicElement.md)|將動態功能區項目加入至狀態列。|  
|[CMFCRibbonStatusBar::AddElement](../Topic/CMFCRibbonStatusBar::AddElement.md)|將新功能區項目加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::AddExtendedElement](../Topic/CMFCRibbonStatusBar::AddExtendedElement.md)|將功能區項目加入至功能區狀態列的擴充區域。|  
|[CMFCRibbonStatusBar::AddSeparator](../Topic/CMFCRibbonStatusBar::AddSeparator.md)|將分隔符號加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::Create](../Topic/CMFCRibbonStatusBar::Create.md)|建立功能區狀態列。|  
|[CMFCRibbonStatusBar::CreateEx](../Topic/CMFCRibbonStatusBar::CreateEx.md)|建立具有延伸樣式的一個功能區狀態列。|  
|[CMFCRibbonStatusBar::FindByID](../Topic/CMFCRibbonStatusBar::FindByID.md)||  
|[CMFCRibbonStatusBar::FindElement](../Topic/CMFCRibbonStatusBar::FindElement.md)|傳回指向具有指定的命令 ID. 的項目|  
|[CMFCRibbonStatusBar::GetCount](../Topic/CMFCRibbonStatusBar::GetCount.md)|傳回位於功能區顯示在狀態列的主要區域的項目數目。|  
|[CMFCRibbonStatusBar::GetElement](../Topic/CMFCRibbonStatusBar::GetElement.md)|傳回指向設定指定之索引處的項目。|  
|[CMFCRibbonStatusBar::GetExCount](../Topic/CMFCRibbonStatusBar::GetExCount.md)|傳回位於功能區狀態列的擴充區域中的項目數目。|  
|[CMFCRibbonStatusBar::GetExElement](../Topic/CMFCRibbonStatusBar::GetExElement.md)|傳回指向所指定之索引處的功能區狀態列的擴充區域的項目。|  
|[CMFCRibbonStatusBar::GetExtendedArea](../Topic/CMFCRibbonStatusBar::GetExtendedArea.md)||  
|[CMFCRibbonStatusBar::GetSpace](../Topic/CMFCRibbonStatusBar::GetSpace.md)||  
|[CMFCRibbonStatusBar::IsBottomFrame](../Topic/CMFCRibbonStatusBar::IsBottomFrame.md)||  
|[CMFCRibbonStatusBar::IsExtendedElement](../Topic/CMFCRibbonStatusBar::IsExtendedElement.md)||  
|[CMFCRibbonStatusBar::IsInformationMode](../Topic/CMFCRibbonStatusBar::IsInformationMode.md)|判斷訊息方式是否為功能區狀態列開始。|  
|[CMFCRibbonStatusBar::RecalcLayout](../Topic/CMFCRibbonStatusBar::RecalcLayout.md)|\(覆寫 [CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md)\)。|  
|[CMFCRibbonStatusBar::RemoveAll](../Topic/CMFCRibbonStatusBar::RemoveAll.md)|從功能區狀態列移除所有項目。|  
|[CMFCRibbonStatusBar::RemoveElement](../Topic/CMFCRibbonStatusBar::RemoveElement.md)|從功能區移除有狀態列的指定命令 ID 的項目。|  
|[CMFCRibbonStatusBar::SetInformation](../Topic/CMFCRibbonStatusBar::SetInformation.md)|可啟用或停用功能區狀態列的資訊。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonStatusBar::OnDrawInformation](../Topic/CMFCRibbonStatusBar::OnDrawInformation.md)|顯示在功能區上狀態列中的訊息字串，當訊息方式啟動時。|  
  
## 備註  
 您可以使用功能區的狀態列，內建的內容功能表使用者可以變更功能區項目的可視性功能區列。  您可以動態地加入或移除項目。  
  
 功能區狀態列有兩個區域:一個主要區域和延伸的區域。  延伸的區域會在功能區狀態列右邊的主要區域隨即出現並顯示於不同的色彩。  
  
 通常，這個狀態列的主要區域的顯示狀態，告知，而擴充區域顯示控制項。  當使用者調整大小的功能區狀態列時，擴充區域越久去保持可見狀態。  
  
## 範例  
 下列範例會在 `CMFCRibbonStatusBar` 類別會示範如何使用各種方法。  這個範例顯示如何將新功能區項目加入至功能區狀態列，將功能區項目加入至功能區狀態列的延伸的區域，加入分隔符號和啟動功能區顯示在狀態列的一般模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## 需求  
 **標題:** afxribbonstatusbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)