---
title: "建立工具列的方法 | Microsoft Docs"
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
  - "CToolBar 類別, 建立工具列"
  - "CToolBarCtrl 類別, 和 CToolBar 類別"
  - "CToolBarCtrl 類別, 建立工具列"
  - "MFC 工具列"
  - "工具列控制項 [MFC]"
  - "工具列控制項 [MFC], 建立"
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立工具列的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供兩個類別來建立工具列:\(包裝 Windows 通用控制項 API\) 的 [CToolBar](../mfc/reference/ctoolbar-class.md) 和 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 。  `CToolBar` 提供所有工具列通用控制項的功能，因此，它處理許多必要的通用控制項設定和結構您的;不過，您產生的可執行檔通常大於該使用所建立的 `CToolBarCtrl`。  
  
 `CToolBarCtrl` 通常會產生較小的可執行檔，因此，您可能想要使用 `CToolBarCtrl` ，如果您不想要整合工具列 MFC 結構。  如果您計劃使用 `CToolBarCtrl` 和整合工具列 MFC 架構，您必須注意其他傳達工具列控制項作業加入至 MFC。  這個通訊並不困難;不過，它是不需要的其他工作，當您使用 `CToolBar`時。  
  
 Visual C\+\+ 提供兩種利用工具列通用控制項。  
  
-   使用 `CToolBar`，建立工具列，然後呼叫 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md) 取得 `CToolBarCtrl` 成員函式的存取。  
  
-   使用 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 建構函式，建立工具列。  
  
 這些方法可讓您對工具列控制項的成員函式的存取。  當您呼叫 `CToolBar::GetToolBarCtrl`時，會傳回 `CToolBarCtrl` 物件的參考，因此您可以使用任一組成員函式。  使用 `CToolBar`，請參閱 [CToolBar](../mfc/reference/ctoolbar-class.md) 與用來建構和建立工具列的資訊。  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)