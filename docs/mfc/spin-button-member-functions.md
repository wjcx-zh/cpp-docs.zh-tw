---
title: "微調按鈕成員函式 | Microsoft Docs"
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
  - "CSpinButtonCtrl 類別, 方法"
  - "微調按鈕控制項, 方法"
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 微調按鈕成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有幾個成員函式可供微調控制項 \([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)\)。  使用這些函式變更微調按鈕的下列屬性。  
  
-   **Acceleration** 可以調整位置變更的速率，使用者按住箭號按鈕。  要與加速一起使用，請使用 [SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md) 和 [GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md) 成員函式。  
  
-   **Base** 您可以變更 \(10 或 16\) 用於基底顯示協同視窗標題的位置。  要與基礎時，請使用 [GetBase](../Topic/CSpinButtonCtrl::GetBase.md) 和 [SetBase](../Topic/CSpinButtonCtrl::SetBase.md) 成員函式。  
  
-   **Buddy Window** 您可以動態地設定協同視窗。  要查詢或變更控制項的協同視窗，請使用 [GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md) 和 [SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md) 成員函式。  
  
-   **位置** 您可以查詢和變更位置。  若要直接與位置時，請使用 [GetPos](../Topic/CSpinButtonCtrl::GetPos.md) 和 [SetPos](../Topic/CSpinButtonCtrl::SetPos.md) 成員函式。  因為協同控制項的標題可能已經變更 \(例如，在這個案例協同是編輯控制項\)， `GetPos` 會擷取目前標頭並調整位置。  
  
-   **Range** 您可以變更最大和最小微調按鈕的位置。  根據預設，最大值設定為 0，因此，最小值設定為 100。  因為預設最少於預設最小，箭號按鈕的動作違反直覺。  一般而言，使用 [SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 成員函式，您將設定範圍。  查詢範圍使用 [GetRange](../Topic/CSpinButtonCtrl::GetRange.md)。  
  
## 請參閱  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控制項](../mfc/controls-mfc.md)