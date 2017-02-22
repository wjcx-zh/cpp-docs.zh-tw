---
title: "管理工具提示控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl 類別, 管理工具提示屬性"
  - "工具提示 [C++], 屬性"
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 管理工具提示控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別 `CToolTipCtrl` 提供一群成員函式，其可以控制 `CToolTipCtrl` 物件和工具提示視窗的各種屬性。  
  
 工具提示視窗的初始、快顯和 reshow 期間使用對 [GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md) 和 [SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md) 呼叫進行設定和擷取。  
  
 使用下列函式變更工具提示視窗的外觀：  
  
-   [GetMargin](../Topic/CToolTipCtrl::GetMargin.md) 和 [SetMargin](../Topic/CToolTipCtrl::SetMargin.md) 擷取和設定工具提示框線和工具提示文字之間的寬度。  
  
-   [GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md) 和 [SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md) 擷取和設定工具提示視窗的最大寬度。  
  
-   [GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md) 和 [SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md) 擷取和設定工具提示視窗的背景色彩。  
  
-   [GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md) 和 [SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md) 擷取和設定工具提示視窗的文字色彩。  
  
 為了讓工具提示控制項可以收到重要訊息 \(例如 **WM\_LBUTTONXXX** 訊息\)，您必須將訊息傳遞至工具提示控制項。  這個轉送的最佳方法是呼叫 [CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md) \(在主控視窗的 `PreTranslateMessage` 函式內\)。  下列範例說明可能的方法 \(假設工具提示控制項名為 `m_ToolTip`\)：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/CPP/manipulating-the-tool-tip-control_1.cpp)]  
  
 若要立即移除工具提示視窗，請呼叫 [Pop](../Topic/CToolTipCtrl::Pop.md) 成員函式。  
  
## 請參閱  
 [Using CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)