---
title: "使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "CStatusBarCtrl 類別, 建立"
  - "狀態列控制項, 建立"
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下是對 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) 的典型用法的範例：  
  
### 若要與組件一起使用狀態列控制項  
  
1.  建構 `CStatusBarCtrl` 物件。  
  
2.  如果您要設定狀態列控制項的繪圖區域的最小高度，請呼叫 [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md) 。  
  
3.  呼叫 [SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md) 設定狀態列控制項的背景色彩。  
  
4.  呼叫 [SetParts](../Topic/CStatusBarCtrl::SetParts.md) 設定狀態列控制項的區段數目和每個部分的右邊緣座標。  
  
5.  呼叫 [SetText](../Topic/CStatusBarCtrl::SetText.md) 設定狀態列控制項的特定組件的文字。  訊息使控制項變更的部分失效，讓它在控制項收到 `WM_PAINT` 訊息時顯示新文字。  
  
 在某些情況下，狀態列只需要顯示一行的文字。  在這種情況下，請呼叫 [SetSimple](../Topic/CStatusBarCtrl::SetSimple.md)。  這會將狀態列控制項轉為「簡單模式」，只顯示單行文字。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)