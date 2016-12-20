---
title: "CMFCDropDownToolBar Class | Microsoft Docs"
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
  - "CMFCDropDownToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolBar class"
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDropDownToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

隨即出現，當使用者按下並按住最上層工具列按鈕的工具列。  
  
## 語法  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](../Topic/CMFCDropDownToolBar::AllowShowOnPaneMenu.md)|\(覆寫 `CPane::AllowShowOnPaneMenu`\)。|  
|[CMFCDropDownToolBar::LoadBitmap](../Topic/CMFCDropDownToolBar::LoadBitmap.md)|\(覆寫 [CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md)\)。|  
|[CMFCDropDownToolBar::LoadToolBar](../Topic/CMFCDropDownToolBar::LoadToolBar.md)|\(覆寫 [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)\)。|  
|[CMFCDropDownToolBar::OnLButtonUp](../Topic/CMFCDropDownToolBar::OnLButtonUp.md)||  
|[CMFCDropDownToolBar::OnMouseMove](../Topic/CMFCDropDownToolBar::OnMouseMove.md)||  
|[CMFCDropDownToolBar::OnSendCommand](../Topic/CMFCDropDownToolBar::OnSendCommand.md)|\(覆寫 `CMFCToolBar::OnSendCommand`\)。|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](../Topic/CMFCDropDownToolBar::OnUpdateCmdUI.md)|\(覆寫 [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/zh-tw/571a38ab-2a56-4968-9796-273516126f80)\)。|  
  
### 備註  
 `CMFCDropDownToolBar` 物件共用工具列的視覺外觀與快顯功能表的行為。  當使用者按下並按住拉工具列按鈕 \(請參閱\) 時， [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)下拉式工具列會出現以及使用者可以選取按鈕從工具列上的下拉式捲動到並放開滑鼠按鈕。  在使用者選取下拉式工具列中的按鈕，該按鈕會顯示為最上層的目前工具列按鈕。  
  
 下拉式工具列無法自訂或內建，，且沒有一個 Tear\-Off 狀態。  
  
 下圖顯示的是 `CMFCDropDownToolBar` 物件:  
  
 ![CMFCDropDownToolbar 範例](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDown")  
  
 您建立物件 `CMFCDropDownToolBar` 您建立泛型的工具列上的相同方式 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)\(請參閱\)。  
  
 插入下拉式工具列的父代 \(Parent\) 工具列:  
  
 1.  為按鈕保留虛擬資源 ID 在父代 \(Parent\) 工具列資源。  
  
 2.  建立包含下拉式工具列的 `CMFCDropDownToolBarButton` 物件 \(如需詳細資訊，請參閱 [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)\)。  
  
 3.  您可以使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，以 `CMFCDropDownToolBarButton` 物件取代空的按鈕。  
  
 如需工具列按鈕的詳細資訊，請參閱 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  如需下拉式工具列的範例，請參閱範例專案 VisualStudioDemo。  
  
## 範例  
 下列範例會在 `CMFCDropDownToolBar` 類別會示範如何使用 `Create` 方法。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## 需求  
 **標題:** afxdropdowntoolbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)