---
title: "初始化 CStatusBarCtrl 物件的組件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl 類別, 宣告其組件"
  - "CStatusBarCtrl 類別, 簡單模式"
  - "圖示, 在狀態列中使用"
  - "簡單狀態列"
  - "狀態列, 宣告其組件"
  - "狀態列, 圖示"
  - "狀態列, 簡單模式"
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化 CStatusBarCtrl 物件的組件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，狀態列會使用不同的窗格顯示狀態資訊。  這些窗格 \(也稱為組件\) 可以包含文字字串、圖示或兩者。  
  
 使用 [SetParts](../Topic/CStatusBarCtrl::SetParts.md) 定義狀態列會有多少部分和長度。  在您建立這個狀態列之後的部分，請呼叫 [SetText](../Topic/CStatusBarCtrl::SetText.md) 和 [SetIcon](../Topic/CStatusBarCtrl::SetIcon.md) 設定文字或圖示狀態列的特定部分。  一旦這個部分已成功設定，控制項會自動重新繪製。  
  
 下列範例使用現有的 `CStatusBarCtrl` 物件 \(`m_StatusBarCtrl`\) 具有四個窗格然後在第二個部分設定圖示 \(IDI\_ICON1\) 的一些文字。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/CPP/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 如需設定 `CStatusBarCtrl` 物件為簡易模式的相關資訊，請參閱 [設定 CStatusBarCtrl 物件的模式](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)