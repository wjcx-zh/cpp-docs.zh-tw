---
title: "Creating Pop-up Menus | Microsoft Docs"
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
  - "context menus, Menu Editor"
  - "pop-up menus, creating"
  - "menus, pop-up"
  - "menus, creating"
  - "shortcut menus, creating"
  - "pop-up menus, displaying"
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Creating Pop-up Menus
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[快顯功能表](../mfc/menus-mfc.md)會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。  
  
 當您建立功能表資源之後，您的應用程式程式碼必須載入功能表資源，並使用  讓功能表顯示。 在使用者按一下快顯功能表外部將功能表關閉，或點按命令後，該功能將會恢復。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。  
  
### 建立快顯功能表  
  
1.  以空白的標題 \(請不要提供**標題**\) [建立功能表](../windows/creating-a-menu.md)。  
  
2.  [將功能表命令加入至新功能表](../windows/adding-commands-to-a-menu.md)。 移至空白功能表標題下方的第一個功能表命令 \(暫時標題顯示為「在這裡輸入」\)。 輸入**標題**和任何其他資訊。  
  
     對快顯功能表中的其他功能表命令重複此程序。  
  
3.  儲存功能表資源。  
  
    > [!TIP]
    >  如需檢視快顯功能表的詳細資訊，請參閱[以快顯功能表方式檢視功能表](../windows/viewing-a-menu-as-a-pop-up-menu.md)。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Connecting a Pop\-up Menu to Your Application](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Menu Editor](../mfc/menu-editor.md)