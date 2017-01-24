---
title: "Rebar 控制項和群組列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "寬線, 在 Rebar 控制項中"
  - "Rebar 控制項, 使用其中的群組列"
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rebar 控制項和群組列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Rebar 控制項的主要目的是要當做子視窗，通用對話方塊控制項，功能表，工具列容器，依此類推。  這個內含項目由「群組列的概念支援」。每個 Rebar 群組列可以包含移駐夾列、點陣圖、文字標籤和子視窗中的任何組合。  
  
 `CReBarCtrl` 類別可用來擷取的許多成員函式和管理，特定 Rebar 群組列的資訊:  
  
-   [GetBandCount](../Topic/CReBarCtrl::GetBandCount.md) 擷取目前的群組列數目 Rebar 控制項的。  
  
-   [GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md) 的資訊初始化一 **REBARBANDINFO** 結構從指定的群組列。  沒有對應的 [SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md) 成員函式。  
  
-   [GetRect](../Topic/CReBarCtrl::GetRect.md) 會擷取指定的群組列的週框。  
  
-   [GetRowCount](../Topic/CReBarCtrl::GetRowCount.md) 擷取群組列行數目 Rebar 控制項中。  
  
-   [IDToIndex](../Topic/CReBarCtrl::IDToIndex.md) 會擷取指定的群組列的索引。  
  
-   [GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md) 擷取群組列的框線。  
  
 刪除作業之外，數個成員函式時，讓您將特定 Rebar 群組列的手的情況。  
  
 [InsertBand](../Topic/CReBarCtrl::InsertBand.md) 和 [DeleteBand](../Topic/CReBarCtrl::DeleteBand.md) 加入和移除 Rebar 群組列。  [MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md) 和 [MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md) 會影響特定 Rebar 群組列的目前大小。  [MoveBand](../Topic/CReBarCtrl::MoveBand.md) 變更特定 Rebar 群組列的索引。  [ShowBand](../Topic/CReBarCtrl::ShowBand.md) 會顯示或隱藏使用者的 Rebar 群組列。  
  
 下列範例示範加入工具列群組列 \(`m_wndToolBar`\) 加入至現有的 Rebar 控制項 \(`m_wndReBar`\)。  群組列以初始化 `rbi` 結構的 `InsertBand` 呼叫成員函式描述的:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/CPP/rebar-controls-and-bands_1.cpp)]  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)