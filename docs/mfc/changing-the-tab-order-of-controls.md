---
title: "Changing the Tab Order of Controls | Microsoft Docs"
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
  - "controls [C++], tab order"
  - "focus, tab order"
  - "tab controls, tab order"
  - "Tabstop property for controls"
  - "controls [C++], focus"
  - "dialog box controls, tab order"
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Tab Order of Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定位順序是在對話方塊內 TAB 鍵將輸入焦點從一個控制項移往另一個的順序。  通常定位順序在對話方塊中是以由左而右和由上而下進行。  每個控制項有 **Tabstop** 屬性，決定控制項是否接受輸入焦點。  
  
### 若要設定控制項的輸入焦點  
  
1.  在[屬性視窗](../Topic/Properties%20Window.md)中，於 \[Tabstop\] 屬性中選取 \[True\] 或 \[False\]。  
  
 即使是沒有將 Tabstop 屬性設為 True 的控制項仍需要是定位順序的一部分。  這很重要，例如，當您為無標題的控制項[定義便捷鍵 \(助憶鍵\)](../mfc/defining-mnemonics-access-keys.md)。  包含相關控制項的便捷鍵 \(Access Key\) 的靜態文字必須在定位順序時必須立刻置於相關控制項之前。  
  
> [!NOTE]
>  如果您的對話方塊包含重疊控制項，變更定位順序可能會變更控制項顯示的方式。  較晚進入定位順序的控制項一定會顯示在重疊控制項的上方，以定位順序排列時位於重疊控制項之前。  
  
#### 要檢視對話方塊中所有控制項的目前定位順序  
  
1.  在 \[格式\] 功能表上，按一下 \[定位順序\]。  
  
 \-或\-  
  
-   請按 CTRL \+ D。  
  
#### 若要變更對話方塊中所有控制項的目前定位順序  
  
1.  在 \[格式\] 功能表上，按一下 \[定位順序\]。  
  
     每個控制項的左上角中的數字會顯示它在目前位於定位順序中的位置。  
  
2.  依照您想要 TAB 鍵排列的順序按一下每個控制項來設定定位順序。  
  
3.  按 ENTER 結束 \[定位順序\] 模式。  
  
    > [!TIP]
    >  一旦您進入 \[定位順序\] 模式，您可以按 ESC 或 ENTER 來停用變更定位順序的功能。  
  
#### 若要變更兩個或更多控制項的定位順序  
  
1.  從 \[格式\] 功能表中選擇 \[定位順序\]。  
  
2.  指定變更要開始的順序。  若要執行此步驟，按住 **CTRL** 鍵並且按一下您要開始變更順序之前的控制項。  
  
     例如，如果您要變更控制項 7 到 9 的順序，按住 CTRL，然後先選取控制項 6。  
  
    > [!NOTE]
    >  若要將特定控制項設為編號 1 \(定位順序中的第一個\)，請按兩下該控制項。  
  
3.  放開 CTRL 鍵，然後以您要 TAB 鍵從此點開始遵循的順序按一下控制項。  
  
4.  按 ENTER 結束 \[定位順序\] 模式。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 Win32  
  
## 請參閱  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)