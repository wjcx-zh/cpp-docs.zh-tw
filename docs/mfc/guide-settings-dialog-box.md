---
title: "輔助線設定對話方塊 | Microsoft Docs"
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
  - "DLU (對話方塊單位)"
  - "對話方塊編輯器, 貼齊輔助線"
  - "格線間距"
  - "輔助線, 設定"
  - "對話方塊單位 (DLU)"
  - "對話方塊編輯器中的配置格線"
  - "貼齊格線 (對話方塊編輯器)"
  - "控制項 [C++], 貼齊輔助線/格線"
  - "輔助線設定對話方塊 (對話方塊編輯器)"
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 輔助線設定對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 配置輔助線  
 顯示配置輔助線的設定。  
  
 **None**  
  
 隱藏配置工具。  
  
 **尺規和輔助線**  
  
 啟動時，將尺規加入至配置工具；輔助線可以置於尺規中。  預設輔助線是邊界，可用拖曳移動。  按一下尺規置放輔助線。  當控制項移在輔助線之上或接近它們時，控制項會「貼齊」輔助線。  一旦控制項附加至輔助線，控制項也可以隨輔助線移動。  當控制項在每一端附加於輔助線，並且在移動輔助線時，會重新調整控制項的大小。  
  
 **Grid**  
  
 建立配置格線。  新控制項會自動對齊格線。  
  
## 格線間距  
 以對話方塊單位 \(DLU\) 顯示格線間距的設定。  
  
 **寬度：DLU**  
  
 以 DLU 為單位設定配置格線的寬度。  水平 DLU 是對話方塊字型的平均寬度除以四。  
  
 **高度：DLU**  
  
 以 DLU 為單位設定配置格線的高度。  垂直 DLU 是對話方塊字型的平均寬度除以八。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Modifying the Layout Grid](../mfc/modifying-the-layout-grid.md)   
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)