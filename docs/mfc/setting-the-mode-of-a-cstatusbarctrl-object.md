---
title: "設定 CStatusBarCtrl 物件的模式 | Microsoft Docs"
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
  - "CStatusBarCtrl 類別, 簡單和非簡單模式"
  - "IsSimple 方法, 使用"
  - "非簡單模式和狀態列控制項"
  - "SetSimple 方法"
  - "簡單模式和狀態列控制項"
  - "狀態列控制項, 簡單和非簡單模式"
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 設定 CStatusBarCtrl 物件的模式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得 `CStatusBarCtrl` 物件的兩種方式:簡單和 nonsimple。  可能在大部分情況下，您的狀態列控制項與文字和圖示或圖示一起有一或多個組件，。  這個呼叫 nonsimple 方式。  如需此模式的詳細資訊，請參閱 [初始化 CStatusBarCtrl 物件的部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。  
  
 不過，您只需要顯示單行文字的大小寫。  在這種情況下，這個簡單的方式為您的需求就已足夠。  若要變更 `CStatusBarCtrl` 物件的方式對簡單，請呼叫 [SetSimple](../Topic/CStatusBarCtrl::SetSimple.md) 成員函式。  當狀態列控制項在簡單模式下，您可以呼叫 **SetText** 成員函式設定文字，以 255 為 **nPane** 參數的值。  
  
 您可以使用 [IsSimple](../Topic/CStatusBarCtrl::IsSimple.md) 函式來判斷模式中的 `CStatusBarCtrl` 物件。  
  
> [!NOTE]
>  如果狀態列物件從 nonsimple 變更為簡單反之亦然，視窗會重新繪製，而且，如果可能，任何定義的部分會自動還原。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)