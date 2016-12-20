---
title: "CMFCToolBarInfo Class | Microsoft Docs"
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
  - "CMFCToolBarInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarInfo class"
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含工具列影像資源 ID 在各種狀態。  `CMFCToolBarInfo` 是當做 [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md) 方法之參數的 Helper 類別。  
  
## 語法  
  
```  
class CMFCToolBarInfo  
```  
  
## Members  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarInfo::m\_uiColdResID](../Topic/CMFCToolBarInfo::m_uiColdResID.md)|包含標準工具列點陣圖的資源 ID \(冷\) 工具列影像。|  
|[CMFCToolBarInfo::m\_uiDisabledResID](../Topic/CMFCToolBarInfo::m_uiDisabledResID.md)|包含停用工具列影像工具列點陣圖的資源 ID。|  
|[CMFCToolBarInfo::m\_uiHotResID](../Topic/CMFCToolBarInfo::m_uiHotResID.md)|包含選取工具列點陣圖的資源 ID \(作用中\) 工具列影像。|  
|[CMFCToolBarInfo::m\_uiLargeColdResID](../Topic/CMFCToolBarInfo::m_uiLargeColdResID.md)|包含大，規則工具列影像工具列點陣圖的資源 ID。|  
|[CMFCToolBarInfo::m\_uiLargeDisabledResID](../Topic/CMFCToolBarInfo::m_uiLargeDisabledResID.md)|包含大，停用工具列影像工具列點陣圖的資源 ID。|  
|[CMFCToolBarInfo::m\_uiLargeHotResID](../Topic/CMFCToolBarInfo::m_uiLargeHotResID.md)|包含大型工具列點陣圖的資源 ID，選取工具列影像。|  
|[CMFCToolBarInfo::m\_uiMenuDisabledResID](../Topic/CMFCToolBarInfo::m_uiMenuDisabledResID.md)|包含停用功能表影像工具列點陣圖的資源 ID。|  
|[CMFCToolBarInfo::m\_uiMenuResID](../Topic/CMFCToolBarInfo::m_uiMenuResID.md)|包含功能表影像工具列點陣圖的資源 ID。|  
  
## 備註  
 完整的工具列點陣圖包含小型工具列影像 \(按鈕\) 固定大小。   在 `CMFCToolBarInfo` 物件中儲存的每個資源 ID 是以單一狀態包含完整工具列影像的點陣圖 \(，選取，停用的大型影像，或功能表\)。  
  
## 繼承階層架構  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## 需求  
 **標題:** afxtoolbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)