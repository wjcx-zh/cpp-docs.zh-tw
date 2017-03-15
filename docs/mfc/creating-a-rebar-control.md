---
title: "建立 Rebar 控制項 | Microsoft Docs"
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
  - "CReBarCtrl 類別, 建立"
  - "Rebar 控制項, 建立"
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 建立 Rebar 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CReBarCtrl](../mfc/reference/crebarctrl-class.md) 物件應該在父物件為可見之前建立。  這樣可以將繪製問題的可能性最小化。  
  
 例如， Rebar 控制項 \(用來框架視窗物件\) 通常用於當工具列控制項的父視窗。  因此， Rebar 控制項的父代是框架視窗物件。  由於框架視窗物件是父代， `OnCreate` 成員函式 \(父\) 是建立 Rebar 控制項的好位置。  
  
 若要使用 `CReBarCtrl` 物件，您通常會執行下列步驟:  
  
### 使用 CReBarCtrl 物件  
  
1.  建構[CReBarCtrl](../mfc/reference/crebarctrl-class.md)物件。  
  
2.  呼叫 [建立](../Topic/CReBarCtrl::Create.md) 以建立公用 Rebar 控制項並將它附加至 `CReBarCtrl` 物件，指定所需的任何樣式。  
  
3.  用對 [CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md)的呼叫載入點陣圖，當做 Rebar 控制項物件的背景。  
  
4.  建立並初始化要由 Rebar 控制項中包含所有子視窗物件 \(工具列、對話方塊控制項，依此類推\)。  
  
5.  初始化具有所需資訊的 **REBARBANDINFO** 結構的群組列將插入。  
  
6.  呼叫 [InsertBand](../Topic/CReBarCtrl::InsertBand.md) 插入現有子視窗 \(例如 `m_wndReToolBar`\) 到新 Rebar 控制項。  如需外掛程式的詳細資訊結合到現有的 Rebar 控制項，請參閱 [Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)。  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)