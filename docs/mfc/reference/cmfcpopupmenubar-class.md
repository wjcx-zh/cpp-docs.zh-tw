---
title: "CMFCPopupMenuBar 類別 | Microsoft Docs"
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
  - "CMFCPopupMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenuBar 類別"
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPopupMenuBar 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

功能表列內嵌於快顯功能表。  
  
## 語法  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](../Topic/CMFCPopupMenuBar::AdjustSizeImmediate.md)|立即重新計算窗格的配置。  覆寫 \( [CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md)\)。|  
|[CMFCPopupMenuBar::BuildOrigItems](../Topic/CMFCPopupMenuBar::BuildOrigItems.md)|從指定的功能表資源載入快顯功能表項目。|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](../Topic/CMFCPopupMenuBar::CloseDelayedSubMenu.md)|關閉一個延遲快顯功能表按鈕。|  
|[CMFCPopupMenuBar::ExportToMenu](../Topic/CMFCPopupMenuBar::ExportToMenu.md)|建立快顯功能表按鈕的功能表。|  
|[CMFCPopupMenuBar::FindDestintationToolBar](../Topic/CMFCPopupMenuBar::FindDestintationToolBar.md)|在指定的點加入水平軸的工具列。|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](../Topic/CMFCPopupMenuBar::GetCurrentMenuImageSize.md)|表示功能表按鈕影像的大小。|  
|[CMFCPopupMenuBar::GetDefaultMenuId](../Topic/CMFCPopupMenuBar::GetDefaultMenuId.md)|傳回預設功能表項目的識別項。|  
|[CMFCPopupMenuBar::GetLastCommandIndex](../Topic/CMFCPopupMenuBar::GetLastCommandIndex.md)|取得最近叫用功能表命令的索引。|  
|[CMFCPopupMenuBar::GetOffset](../Topic/CMFCPopupMenuBar::GetOffset.md)|取得快顯功能表列的行位移。|  
|[CMFCPopupMenuBar::ImportFromMenu](../Topic/CMFCPopupMenuBar::ImportFromMenu.md)|從指定的功能表的快顯功能表按鈕。|  
|[CMFCPopupMenuBar::IsDropDownListMode](../Topic/CMFCPopupMenuBar::IsDropDownListMode.md)|表示快顯功能表列下拉清單模式。|  
|[CMFCPopupMenuBar::IsPaletteMode](../Topic/CMFCPopupMenuBar::IsPaletteMode.md)|表示快顯功能表列是否在調色盤模式。|  
|[CMFCPopupMenuBar::IsRibbonPanel](../Topic/CMFCPopupMenuBar::IsRibbonPanel.md)|表示這是否為功能區面板`FALSE` \(預設\)。|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](../Topic/CMFCPopupMenuBar::IsRibbonPanelInRegularMode.md)|表示這是否為功能區面板在一般模式下`FALSE` \(預設\)。|  
|[CMFCPopupMenuBar::LoadFromHash](../Topic/CMFCPopupMenuBar::LoadFromHash.md)|載入封存的功能表。|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](../Topic/CMFCPopupMenuBar::RestoreDelayedSubMenu.md)|還原關閉的快顯功能表列一個延遲功能表按鈕。|  
|[CMFCPopupMenuBar::SetButtonStyle](../Topic/CMFCPopupMenuBar::SetButtonStyle.md)|將工具列按鈕的樣式在指定的索引。  覆寫 \( [CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md)\)。|  
|[CMFCPopupMenuBar::SetOffset](../Topic/CMFCPopupMenuBar::SetOffset.md)|設定快顯功能表列的行位移。|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](../Topic/CMFCPopupMenuBar::StartPopupMenuTimer.md)|開始一個指定的延遲快顯功能表按鈕的計時器。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPopupMenuBar::m\_bDisableSideBarInXPMode](../Topic/CMFCPopupMenuBar::m_bDisableSideBarInXPMode.md)|指定灰色提要欄位是否會顯示，當應用程式具有 Windows XP 外觀。|  
  
## 備註  
 `CMFCPopupMenuBar` 會在 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 並內嵌在其中。  `CMFCPopupMenuBar` 報告 `CMFCPopupMenu` 物件的整個工作區。  它支援鍵盤和滑鼠輸入。  它也會到達該輸入至 `CMFCPopupMenu` 以及最上層框架視窗。  
  
## 範例  
 下列範例示範如何使用從 `CMFCPopupMenu` 物件的 `CMFCPopupMenuBar` 物件。  這個程式碼片段是 [繪製用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/CPP/cmfcpopupmenubar-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## 需求  
 **標題:** afxpopupmenubar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)