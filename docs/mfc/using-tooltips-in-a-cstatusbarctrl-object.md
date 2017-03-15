---
title: "在 CStatusBarCtrl 物件中使用工具提示 | Microsoft Docs"
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
  - "CStatusBarCtrl 類別, 工具提示"
  - "狀態列, 工具提示"
  - "工具提示 [C++], 在狀態列中使用"
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 在 CStatusBarCtrl 物件中使用工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要啟用狀態列控制項的工具提示，請建立 **SBT\_TOOLTIPS** 樣式的 `CStatusBarCtrl` 物件。  
  
> [!NOTE]
>  如果您使用 `CStatusBar` 物件實作自己的狀態列，請使用 `CStatusBar::CreateEx` 函式。  它可讓您為內嵌 **CStatusBarCtrl** 物件指定不同的樣式。  
  
 當 `CStatusBarCtrl` 物件已成功建立，請使用 [CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md) 和 [CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md) 設定和擷取特定窗格的提示文字。  
  
 當工具提示設定時，它會只有當組件沒有圖示和文字，或者，如果所有文字不能顯示在這個組件中才顯示。  工具提示在簡單模式不支援。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)