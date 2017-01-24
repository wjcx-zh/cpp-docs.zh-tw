---
title: "CMFCPropertyGridToolTipCtrl Class | Microsoft Docs"
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
  - "CMFCPropertyGridToolTipCtrl::PreTranslateMessage"
  - "~CMFCPropertyGridToolTipCtrl"
  - "PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl.~CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl.PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCPropertyGridToolTipCtrl destructor"
  - "CMFCPropertyGridToolTipCtrl class"
  - "CMFCPropertyGridToolTipCtrl class, 解構函式"
  - "PreTranslateMessage method"
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) 使用顯示工具提示的工具提示控制項。  
  
## 語法  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](../Topic/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl.md)|建構 `CMFCPropertyGridToolTipCtrl` 物件。|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCPropertyGridToolTipCtrl::Create](../Topic/CMFCPropertyGridToolTipCtrl::Create.md)|建立工具提示控制項的視窗。|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](../Topic/CMFCPropertyGridToolTipCtrl::Deactivate.md)|停用和隱藏工具提示控制項。|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](../Topic/CMFCPropertyGridToolTipCtrl::GetLastRect.md)|傳回工具提示控制項中的最後一個位置的座標。|  
|[CMFCPropertyGridToolTipCtrl::Hide](../Topic/CMFCPropertyGridToolTipCtrl::Hide.md)|隱藏工具提示控制項。|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|由類別 [CWinApp](../../mfc/reference/cwinapp-class.md) 將 Windows 訊息，然後才會傳送至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](../Topic/CMFCPropertyGridToolTipCtrl::SetTextMargin.md)|設定工具提示文字和工具提示視窗的框線之間的間距。|  
|[CMFCPropertyGridToolTipCtrl::Track](../Topic/CMFCPropertyGridToolTipCtrl::Track.md)|顯示工具提示控制項。|  
  
## 備註  
 當指標停留在屬性名稱時，就會顯示工具提示。  [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) 類別顯示工具提示，以便讓使用者很容易讀取。  通常，工具提示的位置取決於指標的位置。  您可以使用這個類別，工具提示會在屬性名稱類似於自然屬性擴充功能，因此，屬性名稱是完整可見的。  
  
 MFC 會在 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)自動建立這個控制項並使用它。  
  
## 範例  
 下列範例示範如何建構物件 `CMFCPropertyGridToolTipCtrl` 類別以及如何顯示工具提示控制項。  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/CPP/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## 需求  
 **標題:** afxpropertygridtooltipctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)