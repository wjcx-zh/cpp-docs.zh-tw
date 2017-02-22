---
title: "Sizing Individual Controls | Microsoft Docs"
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
  - "Size to Content command"
  - "size, controls"
  - "text, autosizing controls to fit text"
  - "controls [C++], sizing"
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Sizing Individual Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

縮放控點 \(Sizing Handle\) 可以用來調整控制項的大小。  當指標置於縮放控點上時，會變更形狀以指示控制項可以重新調整大小的方向。  作用中的縮放控點是實心的；如果縮放控點是中空的，控制項無法沿著座標軸調整大小。  
  
 您也可以藉由將控制項貼齊輔助線或邊界，或藉由將貼齊的控制項和輔助線分開，以變更控制項的大小。  
  
### 若要調整控制項大小  
  
1.  選取控制項。  
  
2.  拖曳縮放控點以變更控制項的大小：  
  
    -   上方和兩側的縮放控點變更水平和垂直的大小。  
  
    -   角落的縮放控點可同時變更水平和垂直的大小。  
  
    > [!TIP]
    >  您可以按住 SHIFT 鍵，再按向右鍵或向下鍵，一次調整控制項一個對話方塊單位 \(Dialog Unit，DLU\)。  
  
### 若要自動調整控制項的大小以符合內部的內容  
  
1.  從 \[格式\] 功能表選擇 \[依內容調整大小\]。  
  
 \-或\-  
  
-   在控制項上按滑鼠右鍵並且從捷徑功能表選擇 \[依內容調整大小\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)