---
title: "建立狀態列的方法 | Microsoft Docs"
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
  - "CStatusBar 類別, 和 CStatusBarCtrl 比較"
  - "CStatusBarCtrl 類別, 建立"
  - "CStatusBarCtrl 類別, 和 CStatusBar 比較"
  - "方法 [MFC]"
  - "方法 [MFC], 建立狀態列"
  - "狀態列, 建立"
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 建立狀態列的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供兩個類別會建立狀態列:\(包裝 Windows 通用控制項 API\) 的 [CStatusBar](../mfc/reference/cstatusbar-class.md) 和 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) 。  `CStatusBar` 提供所有狀態列通用控制項的功能，它與功能表和工具列會自動互動，因此，它處理許多必要的通用控制項設定和結構您的;不過，您產生的可執行檔通常大於該使用所建立的 `CStatusBarCtrl`。  
  
 `CStatusBarCtrl` 通常會產生較小的可執行檔，因此，您可能想要使用 `CStatusBarCtrl` ，如果您不打算將狀態列 MFC 結構。  如果您計劃使用 `CStatusBarCtrl` 和整合狀態列 MFC 架構，您必須注意其他傳達狀態列控制項作業加入至 MFC。  這個通訊並不困難;不過使用 `CStatusBar`時，它是不需要的其他工作。  
  
 Visual C\+\+ 提供兩種利用狀態列通用控制項。  
  
-   使用 `CStatusBar`，建立這個狀態列，然後呼叫 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md) 取得 `CStatusBarCtrl` 成員函式的存取。  
  
-   使用 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)建構函式，建立這個狀態列。  
  
 這些方法可讓您對狀態列控制項的成員函式的存取。  當您呼叫 `CStatusBar::GetStatusBarCtrl`時，會傳回 `CStatusBarCtrl` 物件的參考，因此您可以使用任一組成員函式。  使用 `CStatusBar`，請參閱 [CStatusBar](../mfc/reference/cstatusbar-class.md) 與用來建構和建立狀態列的資訊。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)