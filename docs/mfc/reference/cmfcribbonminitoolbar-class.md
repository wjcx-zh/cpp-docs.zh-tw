---
title: "CMFCRibbonMiniToolBar Class | Microsoft Docs"
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
  - "CMFCRibbonMiniToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMiniToolBar class"
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonMiniToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作內容快顯工具列。  
  
## 語法  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|預設建構函式。|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonMiniToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonMiniToolBar::GetThisClass`|由取得與此類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件標的架構使用。|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](../Topic/CMFCRibbonMiniToolBar::IsContextMenuMode.md)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](../Topic/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar.md)|\(覆寫 `CMFCPopupMenu::IsRibbonMiniToolBar`。\)|  
|[CMFCRibbonMiniToolBar::SetCommands](../Topic/CMFCRibbonMiniToolBar::SetCommands.md)|設定要顯示在工具列上的命令清單。|  
|[CMFCRibbonMiniToolBar::Show](../Topic/CMFCRibbonMiniToolBar::Show.md)|顯示位於指定的螢幕座標的迷你工具列。|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](../Topic/CMFCRibbonMiniToolBar::ShowWithContextMenu.md)|顯示迷你工具列以及內容功能表。|  
  
## 備註  
 使用者在文件中選取物件之後，通常會顯示迷你工具列。  比方說，在使用者於文書處理程式中選取文字區塊之後，應用程式會顯示包含文字格式化命令的迷你工具列。  
  
 當滑鼠指標超出迷你工具列的範圍時，迷你工具列會變成透明。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## 需求  
 **標頭：** afxRibbonMiniToolBar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)