---
title: "Aligning Controls on a Guide | Microsoft Docs"
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
  - "DLUs (dialog units)"
  - "controls [C++], aligning"
  - "Dialog editor, snap to guides"
  - "guides, tick mark interval"
  - "dialog box controls, placement"
  - "guides, aligning controls"
  - "dialog units (DLUs)"
  - "snap to guides (Dialog editor)"
  - "controls [C++], sizing"
  - "tick mark interval in Dialog editor"
  - "controls [C++], snap to guides/grid"
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Aligning Controls on a Guide
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移動控制項時，控制項的縮放控點會貼齊格線，而且輔助線貼齊控制項 \(如果先前沒有將控制項貼齊輔助線\)。  當移動輔助線時，貼齊的控制項也會移動。  當其中一個輔助線移動時，貼齊一條以上輔助線的控制項的大小會被重新調整。  
  
 決定輔助線和控制項間距的尺規中的刻度標記是以對話方塊單位 \(DLU\) 來定義。  DLU 根據對話方塊字型的大小定義，通常是 8 點的 MS Shell Dlg。  水平 DLU 是對話方塊字型的平均寬度除以四。  垂直的 DLU 是字形的平均高度除以八。  
  
### 若要以輔助線調整控制項群組的大小  
  
1.  將控制項的一端貼齊輔助線。  
  
2.  將輔助線拖曳到控制項的另一端。  
  
     如果多個控制項都需要調整的話，請調整每個控制項的大小以貼齊第二個輔助線。  
  
3.  移動任一條輔助線調整控制項的大小。  
  
### 若要變更刻度標記的間隔  
  
1.  從 \[格式\] 功能表選擇 \[輔助線設定\]。  
  
2.  在[輔助線設定對話方塊](../mfc/guide-settings-dialog-box.md)的 \[格線間距\] 欄位中，以 DLU 指定新寬度和高度。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)