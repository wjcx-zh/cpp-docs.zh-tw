---
title: "建立工具提示的方法 | Microsoft Docs"
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
  - "CToolTipCtrl 類別, 建立工具提示"
  - "工具提示 [C++], 建立"
  - "工具提示 [C++], 工具提示控制項"
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 建立工具提示的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供三種類別以建立及管理工具提示控制項: [CWnd](../mfc/reference/cwnd-class.md)、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)、 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 和 [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)。  這些類別中的工具提示成員函式包裝 Windows 通用控制項 API。  `CToolBarCtrl` 類別和 `CToolTipCtrl` 類別衍生自 `CWnd` 類別。  
  
 `CWnd` 提供四個成員函式來建立並管理工具提示: [EnableToolTips](../Topic/CWnd::EnableToolTips.md)、 [CancelToolTips](../Topic/CWnd::CancelToolTips.md)、 [FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md)和 [OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)。  參考這些個別成員函式以取得實作工具提示的詳細資訊。  
  
 如果您使用 `CToolBarCtrl` 建立工具列，您可以使用下列成員函式實作該工具列上的工具提示: [GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md) 和 [SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md)。  參考這些個別成員函式和 [處理工具提示通知](../mfc/handling-tool-tip-notifications.md) 以取得實作工具提示的詳細資訊。  
  
 `CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。  一個工具提示控制項可以提供多個工具的資訊。  工具是一個視窗，例如子視窗或控制項或為視窗工作區中應用程式定義的矩形區域。  [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) 類別衍生自 `CToolTipCtrl` 並提供額外的視覺化樣式和功能。  
  
## 請參閱  
 [Using CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)