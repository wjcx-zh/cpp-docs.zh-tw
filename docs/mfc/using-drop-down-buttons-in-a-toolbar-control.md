---
title: "在工具列控制項中使用下拉按鈕 | Microsoft Docs"
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
  - "TBN_DROPDOWN"
  - "TBSTYLE_EX_DRAWDDARROWS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 類別, 下拉按鈕"
  - "工具列中的下拉按鈕"
  - "TBN_DROPDOWN 告知"
  - "TBSTYLE_EX_DRAWDDARROWS"
  - "工具列 [C++], 下拉按鈕"
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在工具列控制項中使用下拉按鈕
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了標準按鈕之外，工具列也有下拉式按鈕。  有下拉式按鈕由已附加的向下箭號出現通常表示。  
  
> [!NOTE]
>  只有當 `TBSTYLE_EX_DRAWDDARROWS` 延伸樣式設定，附加的向下箭頭會出現。  
  
 當使用者按一下箭號 \(或按鈕，則為，如果箭號不存在\)， `TBN_DROPDOWN` 會傳送通知訊息至工具列控制項的父代。  您可以處理這個告知和顯示快顯功能表;類似於 Internet Explorer 行為。  
  
 下列程序說明如何實作具有快顯功能表的下拉工具列按鈕:  
  
### 實作一個下拉按鈕  
  
1.  一旦建立 `CToolBarCtrl` 物件，使用下列程式碼中，將 `TBSTYLE_EX_DRAWDDARROWS` 樣式，例如:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  設定要為下拉按鈕的所有新 \([InsertButton](../Topic/CToolBarCtrl::InsertButton.md) 或 [AddButtons](../Topic/CToolBarCtrl::AddButtons.md)\) 或現有的 \([SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)\) 按鈕的 `TBSTYLE_DROPDOWN` 模式。  下列範例示範修改 `CToolBarCtrl` 物件的現有按鈕:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  將 `TBN_DROPDOWN` 處理常式到工具列物件的父類別。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  在新的處理常式，則會顯示適當的快顯功能表。  下列程式碼示範一個方法:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)