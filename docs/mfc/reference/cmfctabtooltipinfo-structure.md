---
title: "CMFCTabToolTipInfo Structure | Microsoft Docs"
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
  - "CMFCTabToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabToolTipInfo struct"
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTabToolTipInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個結構會提供有關停留的 MDI 選項的資訊。  
  
## 語法  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## Members  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTabToolTipInfo::m\_nTabIndex](../Topic/CMFCTabToolTipInfo::m_nTabIndex.md)|指定索引標籤控制項的索引。|  
|[CMFCTabToolTipInfo::m\_pTabWnd](../Topic/CMFCTabToolTipInfo::m_pTabWnd.md)|的索引標籤控制項的指標。|  
|[CMFCTabToolTipInfo::m\_strText](../Topic/CMFCTabToolTipInfo::m_strText.md)|工具提示文字。|  
  
## 備註  
 為 `CMFCTabToolTipInfo` 結構的指標傳遞做為 `AFX_WM_ON_GET_TAB_TOOLTIP` 訊息的參數。  如同的 MDI 選項啟用和索引標籤上的控制項時，使用者停留產生這個訊息。  
  
## 範例  
 下列範例顯示 `CMFCTabToolTipInfo` 如何在 [MDITabsDemo 範例:MFC 索引標籤式的 MDI 應用程式](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/CPP/cmfctabtooltipinfo-structure_1.cpp)]  
  
## 繼承階層架構  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## 需求  
 **標題:** afxbasetabctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)   
 [CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)