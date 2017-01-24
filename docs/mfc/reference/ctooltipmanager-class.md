---
title: "CTooltipManager Class | Microsoft Docs"
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
  - "CTooltipManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTooltipManager class"
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTooltipManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

維護工具提示的執行階段資訊。  `CTooltipManager` 類別會在每個應用程式具現化一次。  
  
## 語法  
  
```  
class CTooltipManager : public CObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTooltipManager::CreateToolTip](../Topic/CTooltipManager::CreateToolTip.md)|建立指定的 Windows 控制項類型的工具提示控制項。|  
|[CTooltipManager::DeleteToolTip](../Topic/CTooltipManager::DeleteToolTip.md)|刪除工具提示控制項。|  
|[CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md)|自訂指定的 Windows 控制項類型的工具提示控制項的視覺外觀。|  
|[CTooltipManager::SetTooltipText](../Topic/CTooltipManager::SetTooltipText.md)|設定工具提示控制項的文字和描述。|  
|[CTooltipManager::UpdateTooltips](../Topic/CTooltipManager::UpdateTooltips.md)||  
  
## 備註  
 同時使用 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)、`CMFCToolTipInfo` 和 `CTooltipManager`，在您的應用程式中實作自訂的工具提示。  如需如何使用這些工具提示類別的範例，請參閱 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md) 主題。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## 需求  
 **標頭：**afxtooltipmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)