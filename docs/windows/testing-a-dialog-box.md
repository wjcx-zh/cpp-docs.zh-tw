---
title: "Testing a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Test Dialog command"
  - "testing, dialog boxes"
  - "dialog boxes, testing"
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Testing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您設計對話方塊時，您可以模擬和測試其執行階段行為，而不用重新編譯程式。 在這個模式下，您可以：  
  
-   輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。  
  
-   測試定位順序。  
  
-   測試控制項群組，例如選項按鈕和核取方塊。  
  
-   為對話方塊中的控制項，測試鍵盤快速鍵。  
  
    > [!NOTE]
    >  使用精靈連接至對話方塊程式碼，不包含在此模擬中。  
  
 當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已經將對話方塊的 Absolute Align 屬性設為 True，對話方塊會在相對於螢幕左上角的位置顯示。  
  
### 測試對話方塊  
  
1.  當對話方塊編輯器是使用中視窗，請在功能表列上，選擇 \[**格式**\]、\[**測試對話方塊**\]。  
  
2.  如果要結束模擬，按下 Esc 鍵或選取您要測試的對話方塊中的 \[**關閉**\] 按鈕。  
  
 如需如何將資源加入 Managed 專案中的相關資訊，請參閱[桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)   
 [顯示或隱藏對話方塊編輯器工具列](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)