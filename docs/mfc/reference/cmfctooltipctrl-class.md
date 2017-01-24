---
title: "CMFCToolTipCtrl Class | Microsoft Docs"
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
  - "CMFCToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipCtrl class"
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根據 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的擴充工具提示實作。  根據 `CMFCToolTipCtrl` 類別的工具提示可以顯示圖示、標籤和描述。  您可以使用漸層填滿、自訂文字和框線色彩、粗體文字、圓角或氣球樣式，自訂其視覺外觀。  
  
## 語法  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolTipCtrl::GetIconSize](../Topic/CMFCToolTipCtrl::GetIconSize.md)|傳回工具提示中的圖示大小。|  
|[CMFCToolTipCtrl::GetParams](../Topic/CMFCToolTipCtrl::GetParams.md)|傳回工具提示的顯示設定。|  
|[CMFCToolTipCtrl::OnDrawBorder](../Topic/CMFCToolTipCtrl::OnDrawBorder.md)|繪製工具提示的框線。|  
|[CMFCToolTipCtrl::OnDrawDescription](../Topic/CMFCToolTipCtrl::OnDrawDescription.md)||  
|[CMFCToolTipCtrl::OnDrawIcon](../Topic/CMFCToolTipCtrl::OnDrawIcon.md)|在工具提示中顯示圖示。|  
|[CMFCToolTipCtrl::OnDrawLabel](../Topic/CMFCToolTipCtrl::OnDrawLabel.md)|繪製工具提示的標籤，或計算標籤的大小。|  
|[CMFCToolTipCtrl::OnDrawSeparator](../Topic/CMFCToolTipCtrl::OnDrawSeparator.md)|工具提示中的標籤和描述之間繪製分隔符號。|  
|[CMFCToolTipCtrl::OnFillBackground](../Topic/CMFCToolTipCtrl::OnFillBackground.md)|填滿工具提示背景。|  
|[CMFCToolTipCtrl::SetDescription](../Topic/CMFCToolTipCtrl::SetDescription.md)|設定要由工具提示顯示的描述。|  
|[CMFCToolTipCtrl::SetFixedWidth](../Topic/CMFCToolTipCtrl::SetFixedWidth.md)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](../Topic/CMFCToolTipCtrl::SetHotRibbonButton.md)||  
|[CMFCToolTipCtrl::SetLocation](../Topic/CMFCToolTipCtrl::SetLocation.md)||  
|[CMFCToolTipCtrl::SetParams](../Topic/CMFCToolTipCtrl::SetParams.md)|使用 `CMFCToolTipInfo` 物件指定工具提示的視覺外觀。|  
  
## 備註  
 同時使用 `CMFCToolTipCtrl`、`CMFCToolTipInfo` 和 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) 物件，在您的應用程式中實作自訂的工具提示。  
  
 例如，若要使用氣球樣式工具提示，請依照下列步驟：  
  
 1.  使用 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) 方法來初始化應用程式中的工具提示管理員。  
  
 2.  建立 `CMFCToolTipInfo` 結構來指定您想要的視覺樣式：  
  
```  
CMFCToolTipInfo params;  
 params.m_bBoldLabel = FALSE;  
 params.m_bDrawDescription = FALSE;  
 params.m_bDrawIcon = FALSE;  
 params.m_bRoundedCorners = TRUE;  
 params.m_bDrawSeparator = FALSE;  
 if (m_bCustomColors)  
 {  
  params.m_clrFill = RGB (255, 255, 255);  
  params.m_clrFillGradient = RGB (228, 228, 240);  
  params.m_clrText = RGB (61, 83, 80);  
  params.m_clrBorder = RGB (144, 149, 168);  
 }  
```  
  
 3.  使用 [CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md) 方法來設定應用程式中所有工具提示的視覺樣式，採用的樣式為 `CMFCToolTipInfo` 物件中定義的樣式：  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);  
```  
  
 您也可以從 `CMFCToolTipCtrl` 衍生新的類別，以控制工具提示的行為和呈現。  若要指定新的工具提示控制項類別，請使用 `CTooltipManager::SetTooltipParams` 方法：  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
  
 若要還原預設工具提示控制類別，並將工具提示外觀重設為預設狀態，請在 `SetTooltipParams` 的執行階段類別和工具提示資訊參數中指定 NULL：  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL, NULL);  
```  
  
## 範例  
 下列範例示範如何建構 `CMFCToolTipCtrl` 物件、設定工具提示顯示的描述，以及設定工具提示控制項的寬度。  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/CPP/cmfctooltipctrl-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## 需求  
 **標頭：**afxtooltipctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)