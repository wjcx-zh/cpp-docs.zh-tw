---
title: "使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl 類別, 使用"
  - "工具提示 [C++], 建立"
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 使用方式的範例：  
  
### 建立和管理 CToolTipCtrl  
  
1.  建構 `CToolTipCtrl` 物件。  
  
2.  呼叫 [建立](../Topic/CToolTipCtrl::Create.md) 以建立視窗工具提示通用控制項並將它附加至 `CToolTipCtrl` 物件。  
  
3.  呼叫 [AddTool](../Topic/CToolTipCtrl::AddTool.md) 註冊工具提示控制項的工具，因此，在工具提示中所儲存的資訊隨即顯示，當游標位於工具時。  
  
4.  呼叫 [SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md) 設定工具提示的工具所維護的資訊。  
  
5.  呼叫 [SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md) 設定中顯示的週框。  
  
6.  呼叫 [HitTest](../Topic/CToolTipCtrl::HitTest.md) 測試點判斷它是否在指定之工具的週框內，如果有的話，擷取有關工具的相關資訊。  
  
7.  呼叫 [GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md) 擷取工具的計數向工具提示控制項註冊。  
  
## 請參閱  
 [Using CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)