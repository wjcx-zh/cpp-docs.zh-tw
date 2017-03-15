---
title: "管理進度控制項 | Microsoft Docs"
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
  - "控制進度控制項"
  - "CProgressCtrl 類別, 操作"
  - "CProgressCtrl 類別, 使用"
  - "CProgressCtrl 類別, 使用"
  - "進度控制項 [C++], 操作"
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 管理進度控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三種方式變更進度控制項 \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\) 中的目前位置。  
  
-   位置可以變更由預設加入數目。  
  
-   位置可以變更由一個任意數目。  
  
-   位置可以變更為特定值。  
  
### 由預設要變更位置中總數  
  
1.  使用 [SetStep](../Topic/CProgressCtrl::SetStep.md) 成員函式中的程式碼數量。  這個值預設為 10。  這個值通常設定為其中一個控制項的初始設定。  逐步執行的值可以是負數值。  
  
2.  使用 [StepIt](../Topic/CProgressCtrl::StepIt.md) 成員函式將位置。  這會造成控制項重繪本身。  
  
    > [!NOTE]
    >  `StepIt` 會導致位置換行。  例如將範圍 1 – 100，步驟 20 和 90 位置，則 `StepIt` 會設定為 10。  
  
### 由一個任意數目變更位置。  
  
1.  使用 [OffsetPos](../Topic/CProgressCtrl::OffsetPos.md) 成員函式變更位置。  `OffsetPos` 會接受負數值。  
  
    > [!NOTE]
    >  `OffsetPos`，不同於 `StepIt`，不會包裝位置。  新位置調整在範圍內保持。  
  
### 變更位置到特定值  
  
1.  使用 [SetPos](../Topic/CProgressCtrl::SetPos.md) 成員函式設定為特定值。  如果需要，則調整在範圍內。  
  
 通常，進度控制項為輸出個別使用。  若要取得目前位置，但不指定新的值，請使用 [GetPos](../Topic/CProgressCtrl::GetPos.md)。  
  
## 請參閱  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控制項](../mfc/controls-mfc.md)