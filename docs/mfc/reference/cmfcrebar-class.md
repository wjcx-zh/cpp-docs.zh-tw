---
title: "CMFCReBar Class | Microsoft Docs"
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
  - "CMFCReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCReBar class"
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCReBar` 物件是針對 Rebar 控制項的配置、保存及狀態資訊的控制列。  
  
## 語法  
  
```  
class CMFCReBar : public CPane  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCReBar::AddBar](../Topic/CMFCReBar::AddBar.md)|將加入至 Rebar 群組列。|  
|[CMFCReBar::CalcFixedLayout](../Topic/CMFCReBar::CalcFixedLayout.md)|\(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\)。|  
|[CMFCReBar::CanFloat](../Topic/CMFCReBar::CanFloat.md)|\(覆寫 [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)\)。|  
|[CMFCReBar::Create](../Topic/CMFCReBar::Create.md)|建立 Rebar 控制項並將其附加至 `CMFCReBar` 物件。|  
|[CMFCReBar::EnableDocking](../Topic/CMFCReBar::EnableDocking.md)|\(覆寫 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)\)。|  
|[CMFCReBar::GetReBarBandInfoSize](../Topic/CMFCReBar::GetReBarBandInfoSize.md)||  
|[CMFCReBar::GetReBarCtrl](../Topic/CMFCReBar::GetReBarCtrl.md)|提供對基礎 [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) 通用控制項的直接存取。|  
|[CMFCReBar::OnShowControlBarMenu](../Topic/CMFCReBar::OnShowControlBarMenu.md)|\(覆寫 [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)\)。|  
|[CMFCReBar::OnToolHitTest](../Topic/CMFCReBar::OnToolHitTest.md)|\(覆寫 [CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)\)。|  
|[CMFCReBar::OnUpdateCmdUI](../Topic/CMFCReBar::OnUpdateCmdUI.md)|\(覆寫 [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-tw/e139f06a-9793-4ee2-bc3d-517389368c77)\)。|  
|[CMFCReBar::SetPaneAlignment](../Topic/CMFCReBar::SetPaneAlignment.md)|\(覆寫 [CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md)\)。|  
  
## 備註  
 `CMFCReBar` 物件可以包含各種子視窗。  這包括編輯方塊、工具列和清單方塊。  您可以調整 Rebar 的方式，或者使用者可以藉由拖曳項目的移駐夾列手動調整 Rebar 群組列。  您也可以將 Rebar 物件的背景設定為您選擇的點陣圖的。  
  
 Rebar 物件具有類似的行為需工具列物件。  Rebar 控制項可以包含一或多個群組列，，而且每個群組列可以包含移駐夾列、點陣圖、文字標籤和子視窗。  
  
## 範例  
 下列範例會在 `CMFCReBar` 類別會示範如何使用各種方法。  這個範例顯示如何建立控制項並加入 Rebar 群組列加入其中。  群組列函式為內部工具列。  這個程式碼片段是 [Rebar 測試範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## 需求  
 **標題:** afxRebar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl Class](../../mfc/reference/crebarctrl-class.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)