---
title: "Defining Mnemonics (Access Keys) | Microsoft Docs"
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
  - "access keys [C++], adding"
  - "keyboard shortcuts [C++], controls"
  - "dialog box controls, mnemonics"
  - "access keys [C++], checking"
  - "mnemonics, checking for duplicate"
  - "mnemonics"
  - "mnemonics, dialog box controls"
  - "keyboard shortcuts [C++], uniqueness checking"
  - "Check Mnemonics command"
  - "controls [C++], access keys"
  - "access keys [C++]"
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Defining Mnemonics (Access Keys)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，鍵盤使用者會以 TAB 鍵和方向鍵將輸入焦點從一個控制項移向另一個對話方塊。  然而，您可以定義便捷鍵 \(Access Key\) \(助憶鍵 \(Mnemonic\) 或容易記憶的名稱\)，讓使用者藉著按一個鍵來選擇控制項。  
  
### 若要為具可見標題的控制項定義便捷鍵 \(按鈕、核取方塊和選項按鈕\)  
  
1.  在對話方塊中，選取控制項。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)的 \[標題\] 屬性中，輸入控制項的新名稱，在您要用來當做控制項的便捷鍵的字母之前輸入連字號 \(**&**\)。  例如 `&Radio1`。  
  
3.  按 **Enter**。  
  
     底線會出現在顯示標題中來指示便捷鍵，例如 **R**adio1。  
  
### 若要為沒有可見標題的控制項定義便捷鍵  
  
1.  藉著使用[工具箱](../Topic/Toolbox.md)中的 \[靜態文字\] 控制項來做控制項的標題。  
  
2.  在靜態文字標題中，在要用來做為便捷鍵的字母之前輸入連字號 \(**&**\)。  
  
3.  確定靜態文字控制項立即出現在定位順序中標明的控制項之前。  
  
 對話方塊內的所有便捷鍵應該是唯一的。  
  
#### 若要檢查重複的便捷鍵  
  
1.  在 \[格式\] 功能表上，按一下 \[檢查助憶鍵\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)